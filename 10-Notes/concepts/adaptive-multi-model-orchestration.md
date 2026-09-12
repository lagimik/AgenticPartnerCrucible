---
title: Adaptive Multi-Model Orchestration
type: concept
created: 2026-09-12
updated: 2026-09-12
tags:
  - multi-model
  - orchestration
  - model-routing
  - evaluation
  - agentic-ai
sources:
  - raw/2026-09-12-github-open-issues-87-91/issues.md
  - https://github.blog/ai-and-ml/github-copilot/project-hydrafusion-frontier-quality-via-multi-model-orchestration/
status: active
---

# Adaptive Multi-Model Orchestration

Adaptive multi-model orchestration selects a bounded sequence of model roles at runtime rather than routing every request to one model. The orchestrator chooses the least complex workflow expected to meet a defined quality bar.

## Core Pattern

```text
Classify task -> select workflow -> execute bounded legs -> validate -> apply or fail safely
```

Useful workflow shapes include:

- Direct execution for tasks one model can solve efficiently.
- Cascading from an efficient model to stronger inference only when an acceptance gate fails.
- Draft, independent read-only critique, and one bounded revision for tasks that benefit from review.

## Design Requirements

- Capability-aware routing based on task needs rather than provider preference.
- Quality gates tied to verified outcomes.
- Independent review contexts that cannot modify shared state.
- Explicit time, retry, escalation, and cancellation budgets.
- Fail-safe application so incomplete or invalid work is not committed.
- End-to-end accounting across every model call and fallback.
- Versioned policies evaluated against representative, frozen baselines.

## Economic Principle

Optimize cost per verified outcome. A compound workflow can cost more than one cheap call while still being more efficient than sending every task to a frontier model. Conversely, critique or escalation is waste when it does not improve acceptance rates enough to justify latency and cost.

## Related Pages

- [[project-hydrafusion-multi-model-orchestration]]
- [[token-economics]]
- [[agent-configuration-optimization]]
- [[ai-agent-lifecycle]]
