---
title: Agent Configuration Optimization
type: concept
created: 2026-08-07
updated: 2026-09-12
tags:
  - agents
  - evaluation
  - optimization
  - observability
  - lifecycle
sources:
  - raw/2026-08-07-github-open-issues-42-45/issues.md
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/from-good-to-great-we-put-agent-optimizer-to-the-test-in-microsoft-foundry/4543982
  - raw/2026-09-12-github-open-issues-87-91/issues.md
status: active
---

# Agent Configuration Optimization

Agent configuration optimization uses representative datasets, evaluators, and execution traces to improve instructions, skills, tool descriptions, or model selection without relying on manual prompt tuning alone.

## Pattern

```text
Run cases -> evaluate -> inspect traces -> propose candidate -> test cheaply -> evaluate fully -> human approval
```

Reflection-based optimization extracts failure causes from natural-language traces rather than treating an aggregate score as the only signal. Candidate changes should remain reviewable, and promotion should preserve explicit human control.

## Preconditions

- Representative production cases
- Evaluators aligned to desired behavior
- Traceability across reasoning and tool calls
- Versioned agent configuration
- A promotion gate controlled by a human owner

Optimization improves configuration defects; it should not hide bad tool data, broken integrations, or other infrastructure failures.

For multi-model systems, the versioned configuration also includes routing thresholds, workflow shapes, quality gates, model bindings, fallback behavior, and execution budgets. Evaluate candidate policies against frozen baselines and account for all model calls, not only the final solver.

## Related pages

- [Microsoft Foundry Agent Optimizer](../../40-Resources/microsoft-foundry-agent-optimizer.md)
- [AI Agent Lifecycle](ai-agent-lifecycle.md)
- [AI Governance](ai-governance.md)
- [Adaptive Multi-Model Orchestration](adaptive-multi-model-orchestration.md)
