---
title: Microsoft Foundry Agent Optimizer
type: resource
created: 2026-08-07
updated: 2026-08-07
tags:
  - microsoft-foundry
  - agents
  - evaluation
  - optimization
  - observability
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/from-good-to-great-we-put-agent-optimizer-to-the-test-in-microsoft-foundry/4543982
  - raw/2026-08-07-github-open-issues-42-45/issues.md
status: active
---

# Microsoft Foundry Agent Optimizer

Microsoft Foundry preview capability that uses evaluation results and natural-language execution traces to propose better agent instructions and configuration.

## Summary

Agent Optimizer replaces manual prompt trial and error with reflection-based optimization. Given an agent, representative cases, and trusted evaluators, it reviews failed traces, proposes targeted configuration changes, tests candidates on small batches, and fully evaluates promising candidates.

The process preserves human control: candidate changes and scores remain reviewable, and an approved candidate becomes the next agent version without automatically changing the model or tools.

## Reported experiment

Microsoft tested six prompt agents with consistent before-and-after evaluation. All six improved, with reported gains ranging from 6.7 to 17.5 percentage points. These results are directional rather than general guarantees: the post describes small, single-seed internal runs, and the capability is in preview.

## Best fit

- The agent already has representative datasets and reliable evaluators.
- Instruction changes fix one case but regress another.
- Teams maintain multiple agents or optimize them repeatedly.
- Failures originate in instructions, skills, tool descriptions, or model choice.

It is not a substitute for repairing infrastructure or tools that return incorrect data.

## Related pages

- [Agent Configuration Optimization](../10-Notes/concepts/agent-configuration-optimization.md)
- [AI Agent Lifecycle](../10-Notes/concepts/ai-agent-lifecycle.md)
- [Data and AI](../100-Crucible/DataAISolutionArea.md)
