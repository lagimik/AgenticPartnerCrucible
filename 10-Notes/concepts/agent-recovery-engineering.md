---
title: Agent Recovery Engineering
type: concept
created: 2026-08-14
updated: 2026-08-14
tags:
  - agents
  - reliability
  - idempotency
  - recovery
  - human-in-the-loop
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/when-ai-agents-fail-engineering-reliable-recovery-with-microsoft-foundry/4546388
  - raw/2026-08-14-github-open-issues-47-53/issues.md
status: active
---

# Agent Recovery Engineering

Agent recovery engineering makes the state and safety of business operations explicit when probabilistic agents call deterministic systems.

## Failure distinctions

| Failure | Meaning | Response |
| --- | --- | --- |
| Model failure | Poor decision or response | Evaluate and improve behavior |
| Tool failure | Dependency errors or does not respond | Classify before retrying |
| Unknown state | Side effect may have occurred | Verify downstream state |
| Business failure | Technical call succeeded but outcome did not | Verify the business result |
| Recovery failure | Recovery worsened the incident | Stop, investigate, and improve controls |

## Design rules

1. Do not interpret a timeout as proof of failure.
2. Do not let the model infer transaction state.
3. Give side-effecting tools explicit operational contracts.
4. Use stable idempotency keys for externally visible actions.
5. Record attempted operations in a durable action ledger.
6. Model recovery as a state machine, not a vague retry instruction.
7. Escalate based on uncertainty, irreversibility, conflict, authorization, and impact.
8. Evaluate duplicate prevention, state verification, retry safety, escalation correctness, and recovery outcomes.

## Related pages

- [Reliable Agent Recovery with Microsoft Foundry](../../40-Resources/reliable-agent-recovery-foundry.md)
- [AI Agent Lifecycle](ai-agent-lifecycle.md)
- [Agent Configuration Optimization](agent-configuration-optimization.md)
