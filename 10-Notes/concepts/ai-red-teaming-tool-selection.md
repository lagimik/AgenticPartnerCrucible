---
title: AI Red-Teaming Tool Selection
type: concept
created: 2026-08-07
updated: 2026-08-07
tags:
  - ai-security
  - red-teaming
  - evaluation
  - tool-selection
  - agents
sources:
  - raw/2026-08-07-github-open-issues-42-45/issues.md
  - https://techcommunity.microsoft.com/blog/azuredevcommunityblog/beyond-model-evaluation-choosing-between-microsoft-foundry-and-pyrit-for-ai-red-/4538110
status: active
---

# AI Red-Teaming Tool Selection

AI red-teaming tools should be selected according to the target boundary and the degree of orchestration control required, not only according to the model provider.

## Decision model

| Target and need | Preferred approach |
| --- | --- |
| Supported Foundry or Azure OpenAI target; built-in evaluators; managed or scheduled runs | Microsoft Foundry managed red teaming |
| Custom API, external service, bespoke RAG or agent flow, or non-Foundry integration layer | PyRIT |
| Production application requiring platform baselines and end-to-end adversarial validation | Use both |

## Core distinction

Model-focused evaluation asks whether responses are grounded, relevant, safe, and improving. Application-focused red teaming asks whether attackers can exploit system prompts, retrieval, tools, data access, business rules, or multi-turn behavior. A model can evaluate well while the surrounding application remains vulnerable.

## Related pages

- [Microsoft Foundry and PyRIT for AI Red Teaming](../../40-Resources/foundry-pyrit-ai-red-teaming.md)
- [AI Governance](ai-governance.md)
- [AI Agent Lifecycle](ai-agent-lifecycle.md)
