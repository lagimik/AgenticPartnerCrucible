---
title: Microsoft Foundry Agent Optimizer
type: resource
created: 2026-08-07
updated: 2026-11-27
tags:
  - microsoft-foundry
  - agents
  - evaluation
  - optimization
  - observability
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights
  - https://azure.microsoft.com/en-us/updates?id=581363
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/from-good-to-great-we-put-agent-optimizer-to-the-test-in-microsoft-foundry/4543982
  - raw/2026-08-07-github-open-issues-42-45/issues.md
status: active
---

# Microsoft Foundry Agent Optimizer

Microsoft Foundry capability that uses evaluation results and natural-language execution traces to propose better agent instructions and configuration. The event's GA announcement and the reviewed insights-driven workflow's preview label have an unresolved scope difference; see the release-status note below.

## Summary

Agent Optimizer replaces manual prompt trial and error with reflection-based optimization. Given an agent, representative cases, and trusted evaluators, it reviews failed traces, proposes targeted configuration changes, tests candidates on small batches, and fully evaluates promising candidates.

The process preserves human control: candidate changes and scores remain reviewable, and an approved candidate becomes the next agent version without automatically changing the model or tools.

## Reported experiment

Microsoft tested six prompt agents with consistent before-and-after evaluation. All six improved, with reported gains ranging from 6.7 to 17.5 percentage points. These results are directional rather than general guarantees: the post describes small, single-seed internal runs of the then-preview capability.

## Best fit

- The agent already has representative datasets and reliable evaluators.
- Instruction changes fix one case but regress another.
- Teams maintain multiple agents or optimize them repeatedly.
- Failures originate in instructions, skills, tool descriptions, or model choice.

It is not a substitute for repairing infrastructure or tools that return incorrect data.

## Related pages

- [Foundry Agent Insights](foundry-agent-insights.md) - GA trace issue grouping, distinct from preview optimization.
- [Agent Configuration Optimization](../10-Notes/concepts/agent-configuration-optimization.md)
- [AI Agent Lifecycle](../10-Notes/concepts/ai-agent-lifecycle.md)
- [Data and AI](../100-Crucible/DataAISolutionArea.md)

## Ignite Release-Status Reconciliation

The [Ignite Book of News](https://news.microsoft.com/events/ignite/2026/book-of-news/)
announces Agent Optimizer GA. The
[Learn workflow reviewed on November 27](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights)
still labels insights-driven optimization preview. Scope/version equivalence
is not established: preserve both sources rather than extending GA to every
workflow or discarding the announcement.
The [heading-led event resource](ignite-2026/microsoft-foundry.md#release-status-reconciliation)
also distinguishes evaluation/insights GA from training previews.

## November Insights-Driven Workflow

[Agent insights](foundry-agent-insights.md) is separately announced as GA.
The [fix-insights optimizer workflow](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights)
was labeled preview in the November 27 review and supports prompt agents without the Microsoft Copilot
harness; hosted agents use separate Toolkit/CLI workflows. Its candidates can
change instructions and function-tool descriptions, not the model or skills.

An optimization run does not promote a candidate automatically, but evaluation
can invoke side-effecting production tools before promotion. Isolate actual
resources and permissions or use read-only tools. The documented general-quality
check can pass with up to 2% regression when a selected insight improves, so
review insight improvement and regression results separately against the
customer's acceptance criteria.
