---
title: AI Governance
type: concept
created: 2026-07-10
updated: 2026-07-16
tags:
  - governance
  - security
  - ai
  - responsible-ai
  - agents
sources:
  - raw/2026-07-10-ingestlinks/
  - raw/2026-07-16-policy-to-proof-ai-governance/source.md
status: active
---

# AI Governance

AI Governance covers the policies, controls, evaluation, monitoring, identity, data protection, and operational guardrails needed for safe AI adoption.

## Governance as an Operating System

Modern AI governance is not a static policy document — it is an operating system: a connected set of policies, controls, telemetry, and evidence that runs alongside AI everywhere it operates.

- **Governance** defines what should happen.
- **Observability and evaluations** verify what is actually happening.
- **Audit and response** prove it, and feed learnings back into policy.

The continuous loop — not any single control — is what makes governance real.

## Four Pillars

1. **Policy** – Define rules, risk classifications, acceptable use, and accountability.
2. **Control** – Enforce boundaries proportionate to risk via guardrails, access decisions, and lifecycle gates.
3. **Visibility** – Observe behavior through logs, metrics, traces, and runtime signals.
4. **Proof** – Produce audit evidence, investigate incidents, and improve policy.

## Nine Domains

1. Policy (RAI policies, approval workflows, guardrails)
2. Data governance (classification, DLP, sensitivity labels, retention, lineage)
3. Model governance (validation, versioning, documentation, change control)
4. Observability (logs, metrics, traces, token usage, runtime signals)
5. Evaluations (quality, safety, grounding, drift, agent task success)
6. Security (threat detection, posture management, red teaming, prompt-injection resistance)
7. Identity & access (RBAC, least privilege, conditional access, agent identities)
8. Audit & compliance (evidence, eDiscovery, legal hold, reporting)
9. Agent governance (registry, lifecycle, policy enforcement, fleet visibility)

**Cross-cutting:** Runtime enforcement operationalizes policy, security, identity, data protection, observability, and agent governance while AI systems are running.

## Practical Path Forward

1. **Scope** – Inventory AI apps, Copilots, agents, APIs, tools, MCP servers.
2. **Classify risk** – What data, actions, systems, and regulations apply.
3. **Apply controls** – Purview, Entra, Defender, Foundry guardrails, APIM AI Gateway, Agent 365, ACS.
4. **Measure and prove** – Evaluations (ASSERT), observability, audit evidence, dashboards.

## Related

- [Policy to Proof — AI Governance Reference](../40-Resources/policy-to-proof-ai-governance.md)
- [AI Gateway Pattern](ai-gateway-pattern.md)
- [[moc-ingested-link-library]]
