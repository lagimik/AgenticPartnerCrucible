---
title: Azure SRE Agent Incident Response Playbook
type: resource
created: 2026-08-28
updated: 2026-08-28
tags:
  - azure
  - sre
  - incident-response
  - agentic-operations
  - reliability
sources:
  - https://techcommunity.microsoft.com/blog/microsoftmissioncriticalblog/your-on-call-rotation-has-a-new-member-10-production-incidents-end-to-end-with-a/4545187
  - raw/2026-08-28-github-open-issues-65-70/issues.md
status: active
---

# Azure SRE Agent Incident Response Playbook

Hands-on production incident pattern for Azure SRE Agent across App Service, AKS, Azure SQL, Cosmos DB, virtual machines, VM Scale Sets, Application Gateway, and Service Bus.

## Safe Incident Flow

```text
Alert -> read-only investigation -> evidence-backed ticket -> bounded action proposal
      -> human approval -> execution -> recovery validation -> follow-up record
```

The primary value is consistent investigation: correlate Azure Monitor, Application Insights, deployment history, Activity Log, Resource Health, and prior incident knowledge before proposing a fix.

## Guardrails

- Start with Reader access and automate the read phase broadly.
- Permit only one bounded, reversible production action per incident.
- Keep production writes in Review mode with human approval.
- Use fixed-purpose runbooks for guest-OS actions rather than open shell prompts.
- Define the validation metric, threshold, and observation period before approval.
- Scope managed identity and RBAC at resource boundaries that match the intended blast radius.
- Use hooks for policy enforcement and audit emission.

Azure SRE Agent blocks delete/remove operations and Azure Key Vault CLI commands, respects Azure management locks, and supports only one active incident platform at a time. Workflows still require telemetry, scoped RBAC, response plans, approved action surfaces, and ITSM integration.

## Pilot Measures

Track time to acknowledge, time spent investigating, time to a supported root-cause hypothesis, remediation approval rate, recovery validation success, recurrence, and the cost of false or unnecessary actions.

## Related Pages

- [[agentic-cloud-operations]]
- [[agent-recovery-engineering]]
- [[ai-agent-lifecycle]]
- [Azure Infrastructure](../100-Crucible/AzureInfrastructureSolutionArea.md)
