---
title: AI Agent Lifecycle
type: concept
created: 2026-07-13
updated: 2026-08-14
tags:
  - agentic-ai
  - responsible-ai
  - mlops
  - governance
  - architecture-pattern
sources:
  - raw/2026-07-13-ai-agent-lifecycle/source.md
  - raw/2026-08-07-github-open-issues-42-45/issues.md
  - raw/2026-08-14-github-open-issues-47-53/issues.md
status: active
---

# AI Agent Lifecycle

A 6-stage continuous lifecycle for enterprise AI agents that treats deployment as the beginning — not the end — of the agent's journey.

## The Lifecycle

```
Design → Build → Test → Deploy → Operate → Iterate ──┐
  ↑                                                     │
  └─────────────────────────────────────────────────────┘
```

## Stages

| Stage | Purpose | Key Output |
|-------|---------|-----------|
| Design | Define permissions, prohibitions, accountability | Risk classification |
| Build | Agent + safety controls built together | Golden dataset |
| Test | Automated + human + red team (3 waves) | Quality gate sign-off |
| Deploy | Shadow → pilot → full (staged) | Verified production behavior |
| Operate | Continuous 5-signal monitoring | Training signals from corrections |
| Iterate | Loop back to appropriate stage | Continuous improvement |

## Key Principles

- **Safety controls IN, not ON** — built at the same time as the agent
- **Golden dataset** — SME-validated scenarios as ground truth across the lifecycle
- **Quality gate** — formal sign-off before any customer sees the agent
- **Staged rollout** — shadow mode → pilot (5%) → full
- **The loop is the product** — the iterate stage is what separates safe agents from drifting ones

## Why the Loop Matters

Regulators ask: "is it safe NOW and can you prove it has been improving?" The iterate loop answers yes through continuous evaluation, versioned datasets, and experiment tracking.

## Iterate Triggers

| Signal | Action |
|--------|--------|
| Quality score drops | Loop to Build (update RAG) |
| New attack detected | Loop to Build (patch guardrail) |
| Human overrides spike | Loop to Design (rethink HITL threshold) |
| New regulation | Loop to Design (full cycle restart) |

## Configuration Optimization

The iterate stage can use evaluation results and execution traces to propose versioned changes to agent instructions, skills, tool descriptions, or model selection. Representative datasets and trusted evaluators are prerequisites, and a human owner should approve which candidate becomes the next deployed version.

## Recovery Engineering

The operate stage must track the state of side-effecting business operations, not only response quality. Tool contracts, idempotency keys, durable action ledgers, downstream verification, explicit recovery state machines, and risk-driven escalation prevent retries from creating duplicate or unsafe outcomes.

## Related Pages

- [[ai-agent-lifecycle-guide]]
- [[agentic-ai]]
- [[ai-governance]]
- [[azure-ai-foundry]]
- [[agent-configuration-optimization]]
- [[agent-recovery-engineering]]
