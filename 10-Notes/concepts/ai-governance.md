---
title: AI Governance
type: concept
created: 2026-07-10
updated: 2026-09-05
tags:
  - governance
  - security
  - ai
  - responsible-ai
  - agents
sources:
  - raw/2026-07-10-ingestlinks/
  - raw/2026-07-16-policy-to-proof-ai-governance/source.md
  - raw/2026-08-07-github-open-issues-42-45/issues.md
  - raw/2026-08-21-github-open-issues-55-63/issues.md
  - raw/2026-09-05-github-open-issues-72-85/issues.md
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

## Security Validation Boundaries

Governance evidence must cover both the model and the application around it. Managed Foundry evaluation and red teaming can test supported Foundry and Azure OpenAI targets, while custom endpoints, RAG layers, tools, and business logic may require PyRIT or comparable application-level adversarial testing.

Cloud and AI posture should also be correlated with runtime, identity, data, application, and attack-path context. Treating AI systems as part of the broader cloud risk graph avoids a separate governance silo.

## Deterministic Agent Controls

Prompts should not be the authorization boundary for consequential actions. The SAFE pattern adds four enforceable controls:

1. Scope the cases, tools, and parameters the agent may use.
2. Anchor consequential decisions in host-verified evidence.
3. Verify that required workflow stages occurred in order.
4. Require or prevent human escalation according to trusted state.

Signed evidence, policy-as-code, protected tool execution, and output gates keep these controls effective even when prompts are weak or adversarial.

## Adaptive and Evidence-Gated Governance

Agentic governance must cover the full interaction system: models, memory, identities, tools, permissions, data, actions, people, and other agents. Requirements should combine controls that always apply with scenario-specific controls that can evolve as capabilities and risks change.

For customer-operated edge AI, release sensitive weights, credentials, and data only when both the runtime and its behavior-shaping artifacts are trusted:

- Attestation verifies the hardware, firmware, runtime, and execution state.
- Provenance verifies models, agent definitions, tools, retrieval indexes, and updates.
- Deterministic mediation constrains actions outside the model.
- Renewable evidence withdraws access when the environment no longer matches policy.

## Related

- [Policy to Proof — AI Governance Reference](../40-Resources/policy-to-proof-ai-governance.md)
- [AI Gateway Pattern](ai-gateway-pattern.md)
- [AI Red-Teaming Tool Selection](ai-red-teaming-tool-selection.md)
- [CNAPP as a Cloud and AI Security Control Plane](../../40-Resources/cnapp-cloud-ai-security-control-plane.md)
- [SAFE Agent Controls on Microsoft Foundry](../../40-Resources/safe-agent-controls-foundry.md)
- [Microsoft Zero Trust Workshop and Assessment](../../40-Resources/zero-trust-workshop-assessment.md)
- [Responsible AI in 2026](../../40-Resources/responsible-ai-transparency-2026.md)
- [Securing Edge AI in Customer-Owned Environments](../../40-Resources/secure-edge-ai-customer-environments.md)
- [ASCII Smuggling in Phishing Evasion](../../40-Resources/ascii-smuggling-phishing-evasion.md)
- [[moc-ingested-link-library]]
