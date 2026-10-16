---
title: Agentic Cloud Operations
type: concept
created: 2026-08-02
updated: 2026-10-16
tags:
  - ai-operations
  - observability
  - azure-monitor
  - agentic-ai
  - sre
sources:
  - raw/2026-08-02-azure-copilot-observability-agent/source.md
  - raw/2026-08-21-github-open-issues-55-63/issues.md
  - raw/2026-09-12-azure-copilot-troubleshooting-agent/source.md
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-1-deploying-your-first-azure-/4564306
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-2-from-one-team-to-enterprise/4564311
status: active
---

# Agentic Cloud Operations

Agentic cloud operations is an operations pattern where AI agents reason across telemetry, resource context, topology, alerts, and operational history to prepare investigations and recommended next steps while humans retain control over mitigation decisions.

## Pattern

1. Collect signals from applications, infrastructure, platform services, logs, metrics, traces, alerts, resource health, and changes.
2. Correlate related signals into higher-signal issues instead of isolated alerts.
3. Run explainable investigations that frame hypotheses, gather evidence, compare signals, and document reasoning.
4. Preserve context in a shared case file so humans and agents can collaborate.
5. Keep humans accountable for approvals, mitigations, and environment changes.

## Operational Agent Layers

- **Observe** - Correlate telemetry, alerts, topology, health, and changes into explainable investigations.
- **Troubleshoot** - Scope a resource-aware issue, run supported diagnostics, identify a likely cause, recommend a fix, or prepare an informed support escalation.
- **Respond** - Propose bounded remediation, require risk-appropriate approval, execute through controlled action surfaces, and validate recovery.

These layers can share context without sharing authority. Broader observation does not imply permission to remediate, and troubleshooting depth depends on the diagnostics available for the selected service and scenario.

## Why it matters

Cloud operations teams face more telemetry than manual workflows can interpret quickly. Agentic cloud operations shifts responders from dashboard-hopping and query assembly toward evidence-backed triage, lower alert noise, and faster time-to-mitigate without removing human judgment.

## Infrastructure Ownership Choices

Teams can run custom agents on AKS for full control over hosting, scaling, RAG, networking, and monitoring, or use Foundry-hosted agents for managed lifecycle, tracing, evaluation, and knowledge configuration. The choice shifts operational ownership but does not remove the need for managed identity, private networking, secrets management, observability, and cost controls.

## Adoption and Shared-Agent Boundaries

The [Azure SRE Agent adoption series](../../40-Resources/azure-sre-agent-first-deployment.md)
recommends proving a bounded operational problem with read-only access, known
incident replay, and an outcome baseline before expanding automation.

Its [enterprise guidance](../../40-Resources/azure-sre-agent-enterprise-adoption.md)
distinguishes roles from isolation: users of one SRE Agent share its operational
context and memory. Split agents where visibility, permissions, action policies,
ownership, or residency require separate boundaries, not simply because a
resource count grows. Coordinate through evidence-bearing handoffs rather than
combining authority, and review exported configuration and learned state before
versioning or reuse.

## Related pages

- [Azure SRE Agent](../entities/azure-sre-agent.md)
- [First Deployment and Workflow Adoption](../../40-Resources/azure-sre-agent-first-deployment.md)
- [Enterprise Adoption and Governance](../../40-Resources/azure-sre-agent-enterprise-adoption.md)
- [[azure-copilot-observability-agent]]
- [[ai-agents-for-it-ops-workshop]]
- [[cloud-native-application-platform-leader-2026]]
- [[azure-copilot-troubleshooting-agent]]
- [[azure-sre-agent-incident-response-playbook]]
