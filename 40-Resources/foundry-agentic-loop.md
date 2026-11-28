---
title: Foundry Agentic Loop
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [microsoft-foundry, github-copilot, agents, delivery, workshops]
sources:
  - https://aiappsgbb.github.io/agentic-loop/
  - https://github.com/aiappsgbb/agentic-loop/blob/123d5d2d303d64f3b6725416d290ee990f1bbeae/README.md
  - https://github.com/lagimik/AgenticPartnerCrucible/issues/156
  - raw/2026-11-27-github-open-issues-156-157/issues.md
  - raw/2026-11-27-github-open-issues-156-157/source-review.md
status: active
---

# Foundry Agentic Loop

The [public portal](https://aiappsgbb.github.io/agentic-loop/) points to a
build-with-Copilot, run-with-Foundry approach. Its
[reviewed repository README](https://github.com/aiappsgbb/agentic-loop/blob/123d5d2d303d64f3b6725416d290ee990f1bbeae/README.md)
describes workshop preparation, reusable playbooks and a build plugin for
translating customer intent into specified, verified and deployable Azure agents.

## Source Summary

| Path | Starting point | Review boundary |
| --- | --- | --- |
| Workshop preparation | Customer brief and selected guidance | Confirm scope before copying a build prompt; preparation is not deployment. |
| Rapid build | Existing Foundry project | Build and verify locally; approve deployment separately. |
| Spec-driven development | Brief and Azure subscription | Specify, Implement, Verify, Deploy; review the specification and separately approve `azd up`. |
| Production improvement | Deployed solution and operational evidence | Observe, evaluate, improve and redeploy; keep changes evidence-backed. |

The README describes independent fresh-context phase review, bounded fix rounds
and durable flight records. It routes runtime-skills agents to the GitHub
Copilot SDK and basic agents or explicit workflows to Microsoft Agent Framework,
requiring clarification for workflows that also need skills.

## Access and Evidence Boundaries

The source says workshop preparation runs in the browser without local setup
or Copilot sign-in. Actual builds require Azure authentication, appropriate
resource and role-assignment permissions, approved data and model capacity.
Deployment can create billable resources and requires confirmation.

A generated or deployed workshop pilot is **not production-ready by default**.
Validate workload-specific identity, data handling, tool authorization,
evaluations, recovery, observability and cost before acceptance. Model and
regional availability must be checked in the chosen project.

This resource is based on the public README and portal metadata; the rendered
portal, plugin, privacy implementation and deployments were not tested.
Repository descriptions do not establish a product GA or preview status.
The build plugin and SDK-based hosted runtime are distinct from the
[managed Copilot harness for Foundry prompt agents](foundry-copilot-harness-managed-execution.md).

**Partner interpretation:** use it to structure scoped workshops and delivery
gates, not as a certification or guaranteed production accelerator.

## Related

- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [GitHub](../10-Notes/entities/github.md)
- [AI Agent Lifecycle](../10-Notes/concepts/ai-agent-lifecycle.md)
- [Agent Selection](microsoft-foundry-agent-selection.md)
- [Agent Recovery Engineering](../10-Notes/concepts/agent-recovery-engineering.md)
- [Time-Boxed AI-Assisted Experimentation](../10-Notes/concepts/time-boxed-ai-assisted-experimentation.md)
