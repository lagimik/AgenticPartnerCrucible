# Build and govern AI agents across a multitenant organization

**Source:** https://techcommunity.microsoft.com/blog/azurearchitectureblog/build-and-govern-ai-agents-across-a-multitenant-organization/4559921
**Captured:** 2026-10-03
**Published:** 2026-10-01 (Azure Architecture Blog, Microsoft Community Hub)

---

> Preview features: this article uses generally available Microsoft Agent 365
> together with capabilities currently in preview, including Microsoft Entra
> Tenant Governance, multitenant agent management, and the Azure API
> Management dedicated AI Gateway tier.

## Why this architecture exists

Enterprises want more people building agents, not fewer — business users
understand the processes to automate, makers need low-code tools, developers
need full control over orchestration, identity, and runtime. The hard part
isn't creating the first agent; it's operating hundreds or thousands safely
across business units with different Entra tenants, data stores, regulatory
obligations, budgets, and autonomy levels — some of which may even compete
with one another.

The architecture uses a **federated agent factory**:
- Centralize standards, deployment patterns, governance views, and
  operational oversight.
- Keep agent identities, business data, detailed telemetry, and runtime
  enforcement local to the owning tenant unless there's a documented reason
  to centralize them.
- Use the Microsoft service that fits each layer rather than assuming one
  product is the "control plane" for everything.
- Govern both Microsoft-managed agents and custom/pro-code agents, using
  different enforcement mechanisms where the runtime model differs.

## Five architectural principles

1. **Centralize governance, not tenant data.** The governing tenant owns
   shared standards, templates, cross-tenant administrative relationships,
   and consolidated operational views. Each subsidiary keeps its own Entra
   identities, production agents, business data, tenant-specific
   permissions, detailed telemetry, local audit evidence, and runtime policy
   enforcement.
2. **Give every governed agent a clear identity and owner.** Use Microsoft
   Entra Agent ID so each agent has a first-class identity, sponsor,
   permissions, sign-in history, and lifecycle. Agent identities are
   tenant-local; a multitenant agent identity blueprint can be published to
   other tenants to create locally owned identities.
3. **Treat tools as governed enterprise capabilities.** Agents should not
   receive broad database credentials. Developers expose narrow, typed
   capabilities (e.g., `invoice.lookup`, `approval.request`) versioned and
   published through governed APIs or MCP servers — separating what the
   agent may do (business), how tools work (developers), and who may call
   them (security/platform).
4. **Make governance a runtime property.** Design-time review is
   insufficient; the platform must check sensitive actions when the agent
   runs (caller, agent, action, resource, data classification, policy
   version, human-approval need, current allowance) via a chain of runtime
   enforcement points.
5. **Observe quality, security, reliability, and value together.** A
   production agent isn't healthy merely because it returns HTTP 200 —
   observability and evaluation (task success, correct tool choice, SOP
   adherence, data exposure, cost, value delivered, quality regression) are
   part of the runtime operating model.

## Architecture (four parts)

Authoring surfaces (no-code to pro-code) → one control plane (**Microsoft
Agent 365**, the central inventory/governance view, with shadow-agent
discovery depending on agent type/integration/licensing) → platform-specific
runtime enforcement → an operations plane for visibility. Some services
(e.g., Microsoft Purview) appear in more than one plane because a plane shows
where a control is configured vs. enforced/observed.

## Workflow (14 steps, numbered to match the reference diagram)

1. Catalog governed data and knowledge (versioned, owned, classified;
   bidirectional links to agents using each source).
2. Author the specification (no/low-code studio: intent, typed I/O with
   classification labels, permitted tools/data, escalation/checkpoint rules,
   collaboration graph, budget, ROI baseline).
3. Register the agent and capability (registration requires an approved
   spec + governed data references before promotion to production).
4. Build tools with typed MCP contracts (least-privilege scope per tool).
5. Evaluate before release (golden test sets, shadow mode, drift checks —
   a release toll-gate).
6. Promote through governance (stage-gated workflow; higher classification
   adds more gates; every approval is immutable evidence; production pins to
   an exact artifact version so rollback is a pointer change).
7. Route custom-agent invocations through the gateway (Azure API Management
   AI Gateway is the mandatory enforcement point for pro-code Foundry
   agents — direct network egress is blocked so agents can't bypass it;
   Copilot Studio/M365 Copilot agents run on Microsoft-managed runtime
   governed by Agent 365/Purview instead).
8. Enforce policy at runtime (every in-scope sensitive action traverses a
   policy enforcement point calling a policy decision point; cached
   decisions during brief outages expire on a TTL, highest-risk actions are
   never cached, and unresolved requests fail closed with an audit event).
9. Reach data only through governed tools (classification-aware access layer
   compares caller clearance to data classification before returning
   results; source-system controls remain authoritative).
10. Apply guardrails and human checkpoints (prompt-injection validation, tool
    call authorization, output sensitive-data/format checks, HITL pauses for
    high-risk actions).
11. Record evidence (OpenTelemetry traces with correlation IDs to an
    immutable, tamper-evident audit store; classification-aware redaction
    for central views).
12. Measure value (ROI capability attributes value per capability against a
    manual baseline, rolls up by business unit, forecasts trends).
13. Deploy and roll back safely (pin production to an exact immutable
    artifact; rollback is a pointer change; Foundry hosted agents serve one
    active version, so blue-green/canary needs weighted routing across
    separate endpoints through the gateway; triggers include evaluation
    regression, policy-violation spikes, SLA error-rate breaches).
14. Deploy build-once across the federation (an IaC factory stamps identical
    customer-controlled governance/enforcement infrastructure into each
    tenant; Microsoft-managed services are configured, not deployed, by the
    factory; the governing tenant gets delegated, least-privileged
    administrative/operational views rather than a replicated central data
    store).

## Key components by plane

**Data foundation and control plane:** Dataverse/SharePoint (catalog), Azure
AI Search (grounded retrieval with permission/classification filtering),
Agent Builder (no-code, M365 Copilot), Copilot Studio (low-code), Microsoft
Entra Agent ID (tenant-local specialized service principal; blueprint
publishes to other tenants), **Agent 365** (control plane across M365 admin
center, Entra, and Purview; GA, licensed per user, included with M365 E7 or
standalone), Azure API Center (MCP tool catalog), Azure Container Registry
(immutable artifact repo), Azure Logic Apps (stage-gated governance
workflow), Azure Policy (infrastructure config standards — distinct from the
runtime policy decision point), and a policy decision point (no single
Microsoft product; suggests an OPA-style policy-as-code engine with a
hierarchical, non-overridable enterprise policy namespace).

**Execution plane:** Microsoft Foundry (agent runtime with isolation/resource
limits), Azure API Management AI Gateway (routing/orchestration enforcement
point for the customer-controlled pro-code path; dedicated AI Gateway tier is
in preview, no SLA, limited regions), MCP tools in APIM, Azure Container Apps
(hosts custom MCP tools and the policy decision point per tenant), Azure AI
Content Safety, Azure OpenAI in Foundry Models, Microsoft Purview (data
classification/DLP feeding the access layer; also covers agent prompts and
responses), Azure Key Vault (secrets for non-managed-identity cases).

**Operations plane:** Azure Monitor (per-tenant telemetry, cross-workspace
queries), Azure Blob Storage with WORM retention (audit evidence store),
Foundry observability (evaluation/monitoring/tracing gating promotion),
Azure Managed Grafana (fleet-wide dashboards for the governing tenant), Azure
Event Hubs (event-driven triggers and telemetry streaming).

**Shared services and federation:** Microsoft Entra ID, Microsoft Entra
multitenant organizations, **Microsoft Entra Tenant Governance (preview)**
for GDAP-based delegated administration, Azure Lighthouse (read-only
cross-tenant Azure visibility), Terraform on Azure with Azure Verified
Modules (the build-once IaC factory; can adopt the Azure AI Gateway Landing
Zone accelerator).

## Assumptions / preview caveats

- Agents get a platform-issued identity only where the platform provides
  one; Agent Builder agents in M365 Copilot don't currently get an Entra
  Agent ID but Agent 365 still discovers/governs them; agents outside
  discovery coverage may remain undetected (shadow agents).
- Requires per-user Agent 365 licensing and tenant enrollment.
- Entra Tenant Governance, multitenant agent management in the M365 admin
  center, and the APIM dedicated AI Gateway tier are in preview at time of
  writing — confirm current status, SLAs, and regional availability before
  depending on them in production.

## Potential use cases

- Retail/distribution: scoped procedure automation (order status, warranty
  returns, pricing lookups) that can't exceed procedure scope.
- Manufacturing/consumer goods parent company: let subsidiaries build their
  own agents while keeping central oversight of posture, cost, and
  evaluation.
- Regulated finance/healthcare/government: every agent action traced to a
  policy set and artifact version, with tamper-evident evidence under local
  custody.
- Large-enterprise platform teams: self-serve agent delivery within
  guardrails instead of ticket-driven central builds.
- Energy/telecom multicloud: agents interact with data where it resides
  without centralizing it.

## When not to use this pattern

- A single team, single tenant, no federation or cross-business-unit
  oversight need.
- Agents don't reach sensitive data or take consequential actions.
- Orchestration is fully deterministic/hard-coded with no business-user
  authoring.
- Data-residency/regulatory rules require one centrally controlled tenant —
  use the single-tenant form of the pattern instead.
