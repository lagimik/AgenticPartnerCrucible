---
title: Reliable Agent Recovery with Microsoft Foundry
type: resource
created: 2026-08-14
updated: 2026-08-14
tags:
  - agents
  - reliability
  - microsoft-foundry
  - idempotency
  - observability
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/when-ai-agents-fail-engineering-reliable-recovery-with-microsoft-foundry/4546388
  - raw/2026-08-14-github-open-issues-47-53/issues.md
status: active
---

# Reliable Agent Recovery with Microsoft Foundry

Engineering guidance for safely recovering AI agents that call side-effecting tools, APIs, databases, workflows, or MCP servers.

## Core lesson

A failed response does not prove that an operation failed, and a successful response does not prove that the intended business outcome occurred. A timeout after a write creates **unknown state**: the downstream system may have completed the action even though the agent never received the response.

Blindly retrying can duplicate procurement requests, tickets, messages, approvals, resource provisioning, or other externally visible actions.

## Reliability pattern

```text
Agent -> tool contract -> action ledger -> verify state -> recover, retry safely, or escalate
```

- **Tool contract:** Return retryability, possible side effects, verification requirements, error classification, and business references—not only success or failure.
- **Action ledger:** Durably record operation and correlation IDs, idempotency keys, request hashes, attempts, side-effect state, downstream references, and recovery status.
- **Recovery state machine:** Treat unknown state, verification, safe retry, compensation, and escalation as explicit transitions.
- **Risk-driven human intervention:** Escalate when state cannot be verified, actions are irreversible, sources conflict, authorization fails, or business impact exceeds the autonomy boundary.

## Foundry's role

Microsoft Foundry supplies agent hosting, tools and MCP integration, identity, tracing, evaluation, monitoring, and versioning. Application teams still own tool failure contracts, idempotency, durable action records, business-state verification, recovery orchestration, escalation rules, and failure-injection tests.

## Related pages

- [Agent Recovery Engineering](../10-Notes/concepts/agent-recovery-engineering.md)
- [AI Agent Lifecycle](../10-Notes/concepts/ai-agent-lifecycle.md)
- [Data and AI](../100-Crucible/DataAISolutionArea.md)
