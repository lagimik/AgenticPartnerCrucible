---
title: Microsoft Foundry Continuous Improvement
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [microsoft-foundry, evaluation, observability, optimization, training]
sources:
  - https://azure.microsoft.com/en-us/blog/continuous-improvement-comes-to-microsoft-foundry/
  - raw/2026-11-20-iq-foundry-onelake-finops/sources.md
status: active
---

# Microsoft Foundry Continuous Improvement

## Source Summary

The [November 17 announcement](https://azure.microsoft.com/en-us/blog/continuous-improvement-comes-to-microsoft-foundry/)
describes a repeatable loop: **Establish -> Identify -> Optimize -> Validate and
repeat**. Define quality and safety criteria, collect traces and expert
feedback, investigate recurring issues, evaluate candidate improvements, and
promote only changes the owning team approves.

Agent Optimizer can propose instruction, skill, and model-choice changes.
Managed Training and Programmed Training address model customization instead:
configuration optimization does not itself retrain model weights.
Microsoft describes statistical comparisons, release-pipeline quality gates,
live evaluation, scheduled checks, and a monitoring dashboard spanning quality,
safety, latency, and token usage.

## Capability Status

| Capability | Article status on November 17 |
| --- | --- |
| Insights; external LangGraph, LangChain, CrewAI visibility | GA. |
| Trace annotations, evaluation datasets, golden datasets, safety rubric extensions | Preview. |
| Sending insights to optimizer; skill and cost optimization | Preview. |
| Programmed Training with custom Python training recipes | Preview; supported models and compute matter. |
| Hosted-agent increased concurrency; voice agents | GA. |
| Faster hosted startup; managed Copilot harness; Foundry cost view | Preview. |
| Hosted deployment to AKS | Coming soon in preview. |

The announcement does not establish automatic improvement in production.
Candidate changes remain reviewable; the team chooses when to apply them.
Runtime control for agents outside Foundry is future scope, not blanket current
coverage. Customer tuning results and cost reductions are vendor-reported,
task-specific comparisons, not transferable guarantees.

## Partner Application

**Interpretation:** Package an evaluated-agent operations service: select a
representative baseline, govern trace and training-data use, separate held-out
validation from optimization cases, measure quality/latency/full cost, and
version configuration, skills, datasets, and model bindings. Require reviewed
promotion and rollback; do not use optimization to conceal broken tools or
incorrect source data. Training and operational changes were not performed.

## Related

- [Agent Configuration Optimization](../10-Notes/concepts/agent-configuration-optimization.md)
- [Earlier Agent Optimizer Experiment](microsoft-foundry-agent-optimizer.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Microsoft IQ Context Platform](microsoft-iq-enterprise-context-platform.md)
- [AI Agent ROI Operating Model](ai-agent-roi-operating-model.md)
