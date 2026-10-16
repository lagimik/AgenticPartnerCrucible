---
title: Azure SRE Agent - First Deployment and Workflow Adoption
type: resource
created: 2026-10-16
updated: 2026-10-16
tags: [azure-sre-agent, operations, adoption, reliability, automation]
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-1-deploying-your-first-azure-/4564306
  - raw/2026-10-16-azure-sre-agent-adoption/sources.md
status: active
---

# Azure SRE Agent - First Deployment and Workflow Adoption

## Source Summary

[Part 1 of Microsoft's enterprise adoption guide](https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-1-deploying-your-first-azure-/4564306),
published October 15, 2026, recommends proving one bounded operational use case
before expanding customization, automation, or enterprise topology.

## First-Use-Case Sequence

1. Choose recurring operational pain the team understands: investigation,
   triage, deployment validation, proactive health, cost, or certificate expiry.
2. Connect only the telemetry, code, deployment history, and runbooks needed
   for that problem.
3. Begin with diagnostic or read-only access through managed identity and scoped
   Azure RBAC; add narrowly scoped writes only when the workflow requires them.
4. Replay known historical incidents to expose missing context, then use the
   agent alongside the normal live response process.
5. Establish a baseline and measure the chosen outcome in the existing system
   of record, such as incident resolution time, false positives, or rollbacks.

## Customize Only for a Demonstrated Need

| Mechanism | Use |
| --- | --- |
| Built-in capabilities or existing plugins | Start here before adding custom components. |
| Skill | Teach organizational procedures, evidence interpretation, runbooks, and escalation. |
| Tool | Execute deterministic calculations, queries, external calls, or exact-format outputs. |
| Custom subagent | Package a focused workflow with selected instructions and tools for independent testing, invocation, or triggers. |

A skill and tool can work together; a skill is not a substitute for deterministic
execution, and a subagent is not required simply because a use case is important.

## Expand into Reviewed Automation

Reuse proven context and workflows. Choose response plans for incident or alert
entry, scheduled tasks for recurring work, and HTTP triggers for pipelines or
external systems. Start in Review mode. Consider Autonomous mode only for actions
the team already permits operators to perform without case-by-case approval.
Use live reports to identify the next recurring source of operational toil.

## Partner Application and Boundaries

**Interpretation:** Package a readiness assessment and measured pilot with a
selected use case, scoped access, known-incident replay, an outcome baseline,
and an approval design before offering workflow automation.

The source supplies guidance, not a quantified improvement guarantee or blanket
approval for production writes. Broader adoption requires a separate review of
shared context, user visibility, and authority in Part 2.

## Related Pages

- [Azure SRE Agent](../10-Notes/entities/azure-sre-agent.md)
- [Part 2 - Enterprise Adoption and Governance](./azure-sre-agent-enterprise-adoption.md)
- [Configuration Guide](./azure-sre-agent-configuration-guide.md)
- [Incident Response Playbook](./azure-sre-agent-incident-response-playbook.md)
- [Agentic Cloud Operations](../10-Notes/concepts/agentic-cloud-operations.md)
