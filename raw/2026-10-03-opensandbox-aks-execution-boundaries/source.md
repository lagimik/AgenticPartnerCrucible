# When AI Starts Taking Action: Building Execution Boundaries with OpenSandbox and AKS

**Source:** https://techcommunity.microsoft.com/blog/azuredevcommunityblog/when-ai-starts-taking-action-building-execution-boundaries-with-opensandbox-and-/4561601
**Captured:** 2026-10-03
**Published:** 2026-10-02 (Microsoft Developer Community Blog / Microsoft Community Hub)
**Author:** kinfey
**Demo project:** `kinfey/aks_opensbx_ghc_demo` (unofficial, McDonald's-themed technical demonstration — not an official service or real transaction system)

---

## Core thesis

Model capability determines what an agent can *propose*; the execution
platform determines *where*, with which permissions, and for how long those
proposals can become actions. Running every agent's tool processes inside
the business API container creates coupling — leftover files, stuck
processes, dependency drift, and resource contention across sessions. A
sandbox is a working environment with a lifecycle, a resource budget, and an
access policy — not an instruction to "please be safe."

## Three concepts that get conflated

1. **MCP (Model Context Protocol)** describes tool interaction — discovery
   and invocation. It does *not* put tools inside a VM. An MCP server can run
   on a laptop, in a business-service container, remotely, or in a dedicated
   sandbox; whether a tool can write data, who may invoke it, and how side
   effects are reversed are separate design questions.
2. **OpenSandbox** is an open-source platform that makes the working
   environment an application resource: sandbox lifecycle, command
   execution, file operations, and network-access capabilities via SDKs/
   APIs. Docker supports a local start; Kubernetes provides a cluster
   deployment path. It is not a language model, not a Kubernetes
   replacement, and not synonymous with Kata.
3. **Kata Containers** adds a separate guest kernel to the sandbox pod.
   Conventional containers share the host kernel; Kata runs workloads in
   lightweight VMs. With AKS Pod Sandboxing, the isolation unit is the pod
   using the Kata runtime with its own guest kernel. This doesn't mean every
   container in a pod gets its own VM, nor does a VM replace application
   authentication, outbound restrictions, or business approvals.

Summary: MCP defines the tool interface, OpenSandbox manages the working
environment, Kata provides runtime isolation, and the application still owns
authorization and business rules.

## What a "per-session Kata VM" actually isolates

A session (`session_id`) gets an OpenSandbox sandbox whose pod selects the
Kata RuntimeClass; later requests in the same session reuse that
environment.

- Not a new VM per message — related turns can reuse files/temp state.
- Not an Azure VM purchased per user — Kata pod VMs run on AKS nodes; many
  sandboxes can share a node's compute.
- Not one sandbox per node — capacity depends on resource settings, VM
  overhead, system components, and concurrent work.
- A session ID is not authorization — it identifies routing/resource
  mappings; production services must still validate session ownership.
- Files surviving between turns does not mean they survive sandbox
  deletion — durable artifacts need explicit, governed persistence.

Analogy: AKS is the campus, nodes are buildings, Kata sandboxes are
workrooms, and OpenSandbox is the workspace management system.

## OpenSandbox on AKS: installation is not the finish line

Execution path: FastAPI backend requests a sandbox via the OpenSandbox SDK →
lifecycle service creates a `BatchSandbox` resource → controller reconciles
into a sandbox pod → pod starts with the Kata runtime → SDK accesses `execd`
through the gateway for command/file operations → deletion or expiration
reclaims the sandbox.

Key pod template fragment:
```yaml
spec:
  runtimeClassName: kata-vm-isolation
  nodeSelector:
    kubernetes.azure.com/kata-vm-isolation: "true"
  securityContext:
    seccompProfile:
      type: RuntimeDefault
```

The deployed example uses one shared system/Kata pool: three
`Standard_D4s_v5` Azure Linux nodes with `KataVmIsolation` (AKS API
2026-07-01). The model is `gpt-6-astra` accessed through GitHub Copilot APIs
— not a GPU model-serving deployment. Deployment checks inspect actual pool
properties, Ready node count, the RuntimeClass, and the guest kernel inside
a temporary Kata pod — a deployment acceptance signal, not formal proof of
the entire system's security.

More platform control also means more platform ownership: node capacity,
image provenance, control-plane upgrades, resource budgets, observability,
recovery, and removal of temporary installation privileges all become the
team's responsibility. Three nodes are explicitly not a high-availability
guarantee; production designs should reconsider dedicated system/workload
pools, zones, quotas, and tenant separation.

**Credential Vault:** the trusted backend supplies credentials/bindings to
OpenSandbox's egress sidecar; the workload process receives placeholders,
and the proxy injects authentication into matching outbound HTTPS requests.
This reduces the workload's *direct* access to long-lived credentials — it
does not make credentials disappear from the system; the backend and egress
sidecar remain in the trusted computing base. Preventing a model from
reading a token also doesn't prevent misuse of operations already authorized
by that token, so tools should still be scoped (e.g., read-only remote
operations, exact hostname bindings). Kubernetes pause/resume can recreate
the sidecar, requiring a trusted client to repopulate its in-memory vault —
restoring compute state, identity context, and business permissions are
different operations.

## ACA Sandboxes vs. ACA Dynamic Sessions vs. OpenSandbox on AKS

Azure Container Apps has four compute models: Regular Container Apps (web
apps/APIs), Jobs (run-to-completion tasks), Dynamic Sessions (isolated
execution via a session pool + identifier), and **Sandboxes** (explicit
lifecycle/state/policy control over individual environments via a
`Microsoft.App/SandboxGroups` resource — supports suspend/resume, memory/
disk state, ports, egress policies, Azure Blob/Data Disk volumes; requires a
Microsoft Entra ID identity and the Container Apps SandboxGroup Data Owner
role).

**Release-status caveat:** at time of review, Microsoft Learn described
Sandboxes capabilities while an earlier Microsoft repository doc still
carried an *Early Access* label warning that early resources might need
recreation. Verify access, SDKs, RBAC, networking, and service terms before
adoption — don't infer universal GA.

| Dimension | OpenSandbox on AKS (this project) | ACA Sandboxes | ACA Dynamic Sessions |
|---|---|---|---|
| Main object | OpenSandbox sandbox + Kubernetes workload | Sandbox group + individual sandbox | Session pool + identifier |
| Platform operations | Team operates OpenSandbox + AKS workloads/nodes; Azure manages AKS control plane | Azure manages infra; app manages sandbox lifecycle | Azure manages pool allocation/session lifecycle |
| Isolation | Explicitly selects Kata pod VMs | Documented independent security boundary (runtime not inferred) | Officially documented Hyper-V isolation |
| State | Temporary per-session here; persistence/snapshots need separate validation | Explicit suspend, resume, snapshots, volumes | Context while session exists; ephemeral after reclamation |
| Images/tools | Custom images, CLI, MCP, runtime policy | OCI images converted to root filesystems | Built-in interpreters or custom container pools |
| Network/credentials | Team combines private networking, egress policy, Vault, app authorization | Service identity/network/policy capabilities | Pool access/network controls; app owns identity/tool auth |
| Startup | Depends on cache/scheduling/runtime/init — no instant-start guarantee | Documented prewarmed subsecond startup/restore | Documented low-latency prewarmed allocation |
| Team fit | Kubernetes expertise, deeper runtime control | Managed infra, explicit workspace state control | Managed sessions without full lifecycle ownership |

Cost nuance: total cost per successfully completed task includes execution
resources, warm capacity, state storage, images, networking, logs, model
usage, and operational effort — stopped ACA sandboxes incur no CPU/memory
fees, but that doesn't zero the bill for storage/dependencies, and deleting
an AKS sandbox doesn't eliminate fixed node costs.

## Decision guidance by scenario

- **Brief, stateless work** (e.g., upload a CSV, run a short analysis):
  evaluate Dynamic Sessions first to reduce platform work.
- **Cross-turn, long-running coding agent**: ACA Sandboxes' explicit
  lifecycle is compelling — still decide what enters a snapshot, how
  credentials reauthorize after restore, and how deletion policy meets
  business obligations.
- **Established AKS platform / need deep runtime control**: OpenSandbox on
  AKS is attractive — control and composability, not cost-free operation.
- **Agent only calls a governed business API** (no generated-code execution,
  no local tool/filesystem need): a regular ACA API with authentication and
  a tool gateway may be simpler — not every agent needs a sandbox platform.

These choices are not mutually exclusive; different task classes can use
different execution backends if identity, lifecycle, results, and error
contracts stay explicit.

## Three lessons from building the demo

1. **Startup latency is not one number.** Initial sandbox image pull
   (~2.8 GB) took almost six minutes; image warmup was moved outside the
   request path, waiting for actual `execd` health. End-to-end latency =
   queue/scheduling + image pull + guest startup + cert/proxy setup + CLI
   startup + model/tool execution + result transport/rendering. Don't
   compare a documented subsecond warm-capacity allocation to one cold
   image pull.
2. **A working isolation boundary doesn't guarantee a working data
   contract.** Copilot's terminal output converted Markdown tables into
   character borders, and line-oriented logging stripped terminators. Fix:
   extract original content from CLI JSONL, encode it in a single-line JSON
   envelope across command logs, decode back into Markdown, then sanitize
   with Marked + DOMPurify before rendering.
3. **Acceptance must cover the real path.** A fixed-reply browser test
   proves only that the renderer works, not that model output survives the
   CLI, logs, and API. Prove completion with structured results and actual
   side effects, not a success-shaped sentence.

## Before calling this production

Five questions the author would answer first (not "add more tools"):

| Question | Required design |
|---|---|
| Who owns the session? | Authentication, tenant binding, server-side session ownership, resource authorization |
| Which state deserves to survive? | Separate temp workspace files, durable artifacts, business orders, audit records |
| Who may cause side effects? | User approval bound to contents, idempotency, auditable authorization beyond model instructions |
| Where can the system fail? | Stage-level startup metrics, admission control, budgets, timeouts, retries, resource reclamation |
| Can the execution backend change? | Contract tests for create, execute, files, credentials, state restoration, deletion |

The demo's own backend keeps session mappings in memory, runs at most one
replica, and has no public user login or authenticated session ownership —
explicitly demonstration constraints, not a production multitenancy
template. Order creation is local simulation only; a `confirmed` boolean
from the agent is not an independently authenticated, auditable
purchase-approval system — real commerce needs server-verifiable
authorization bound to a user and the exact order contents.

## Closing framing

Three better questions than "self-hosted vs. serverless": What do we need to
control? What are we willing to operate? How will we prove that execution
completed as intended? A reliable AI application needs both a capable model
and a workspace with clear boundaries, a reclaimable lifecycle, and an
auditable record of what happened.
