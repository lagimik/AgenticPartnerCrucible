---
title: Agent Execution Sandbox Isolation
type: concept
created: 2026-10-03
updated: 2026-10-03
tags:
  - agentic-ai
  - architecture-pattern
  - sandboxing
  - aks
  - container-apps
  - mcp
  - security-boundary
sources:
  - raw/2026-10-03-opensandbox-aks-execution-boundaries/source.md
status: active
---

# Agent Execution Sandbox Isolation

When an agent moves from suggesting text to executing generated code and
calling tools, the execution platform — not the model — becomes the actual
security boundary. A practitioner's deep-dive (source below) untangles three
concepts that are routinely conflated, then compares three Azure-era ways to
host that execution boundary.

## Three concepts, one confusion

1. **MCP (Model Context Protocol)** standardizes how a model discovers and
   invokes tools. It says nothing about *where* a tool runs or what it may
   touch — that's a separate design decision.
2. **OpenSandbox** is an open-source framework that turns the "working
   environment" (filesystem, process, network) into an application resource
   with a lifecycle: create, execute, snapshot, delete. It can run on
   Docker locally or on Kubernetes.
3. **Kata Containers** is the runtime isolation layer: instead of sharing
   the host kernel, a Kata-run pod gets its own lightweight guest kernel.
   On AKS, this is enabled per node pool/pod via `KataVmIsolation`.

MCP defines the interface, OpenSandbox manages the environment's lifecycle,
Kata provides kernel-level isolation — and the application still owns
authorization, session ownership, and business rules. None of the three
substitute for the others.

## What isolation does *not* mean

- Not one VM per chat message — a session can reuse its sandbox across
  turns.
- Not one VM per user — sandboxes share AKS node capacity.
- A session ID is not an authorization token; services must still validate
  session ownership server-side.
- Files surviving across turns in a live sandbox does not mean they survive
  sandbox deletion — durable records need explicit, governed persistence
  outside the sandbox.

## Three ways to host the execution boundary (Azure)

| Model | Owner of operations | Isolation | State | Best fit |
|---|---|---|---|---|
| OpenSandbox on AKS | Team operates OpenSandbox + AKS nodes; Azure runs the control plane | Explicit Kata pod VMs | Temporary by default; persistence needs separate validation | Teams with existing Kubernetes platforms needing deep runtime control |
| Azure Container Apps **Sandboxes** | Azure manages infra; app manages sandbox lifecycle | Documented security boundary | Explicit suspend/resume, snapshots, volumes | Long-running/paused coding agents needing workspace state control |
| Azure Container Apps **Dynamic Sessions** | Azure manages pool allocation and session lifecycle | Documented Hyper-V isolation | Ephemeral, reclaimed after session | Brief, stateless tool/code execution at low latency |

ACA Sandboxes and Dynamic Sessions are two distinct ACA compute models and
should not be used interchangeably in architecture discussions. At review
time, ACA Sandboxes still carried mixed GA/early-access signals in official
docs — verify current release status, RBAC (Container Apps SandboxGroup
Data Owner), and networking before committing an architecture to it.

Not every agent needs a sandbox platform at all: an agent that only calls a
governed business API with no generated-code execution can use a regular
container app with authentication and a tool gateway.

## Credential handling: reduce exposure, don't assume elimination

A workable pattern is a **Credential Vault egress sidecar**: the trusted
backend holds real credentials; the sandboxed workload only sees
placeholders, and a proxy injects real credentials into matching outbound
HTTPS calls. This reduces the sandboxed process's *direct* access to
long-lived secrets but does not remove the backend/sidecar from the trusted
computing base, and it does not prevent misuse of operations an already-
authorized token legitimately allows — tools still need explicit scoping
(e.g., read-only remote calls).

## Operational lessons worth carrying into any execution-sandbox design

- **Startup latency has many components** (scheduling, image pull, guest
  boot, cert/proxy setup, CLI startup, execution, result transport) — don't
  compare a vendor's documented warm-start number to your own cold-image
  pull.
- **Isolation success ≠ data-contract success.** Markdown/table rendering,
  log line-wrapping, and sanitization pipelines (e.g., Marked + DOMPurify)
  need their own acceptance tests against the real CLI/log path, not a
  fixed-reply mock.
- **Prove completion with structured results and observed side effects**,
  not a model's success-shaped sentence — this applies to both local tool
  execution and remote MCP calls.

## Five questions before calling a sandbox platform "production"

| Question | Required design |
|---|---|
| Who owns the session? | Authentication, tenant binding, server-side session ownership |
| Which state deserves to survive? | Separate temp workspace files from durable/audited business records |
| Who may cause side effects? | User approval bound to exact content, idempotency, auditable authorization — not just a model-reported boolean |
| Where can the system fail? | Startup metrics, admission control, budgets, timeouts, retries, reclamation |
| Can the execution backend change? | Contract tests for create/execute/files/credentials/state-restore/delete |

## Related

- [Multitenant AI Agent Governance Architecture](multitenant-ai-agent-governance-architecture.md) —
  governs the agent and its identity; this page covers where the agent's
  generated code/tools actually execute.
- [Model Context Protocol (MCP)](model-context-protocol-mcp.md) — the tool
  interface this execution boundary must still enforce authorization
  around.
- [AI Agent Lifecycle](ai-agent-lifecycle.md) — session/state lifecycle
  parallels the sandbox lifecycle described here.
