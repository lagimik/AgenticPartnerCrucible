---
title: Microsoft Foundry and PyRIT for AI Red Teaming
type: resource
created: 2026-08-07
updated: 2026-08-07
tags:
  - ai-security
  - red-teaming
  - microsoft-foundry
  - pyrit
  - evaluation
sources:
  - https://techcommunity.microsoft.com/blog/azuredevcommunityblog/beyond-model-evaluation-choosing-between-microsoft-foundry-and-pyrit-for-ai-red-/4538110
  - raw/2026-08-07-github-open-issues-42-45/issues.md
status: active
---

# Microsoft Foundry and PyRIT for AI Red Teaming

Microsoft Community Hub guidance for selecting managed Microsoft Foundry evaluation and red teaming or the open-source PyRIT framework based on the target and required control.

## Summary

Microsoft Foundry supports quality evaluation and managed cloud red teaming for supported Foundry projects, Azure OpenAI deployments connected to a project, and Foundry agents. It is the stronger fit for built-in evaluators, taxonomy-based and multi-turn attacks, scheduled runs, and operational evaluation within the supported Microsoft ecosystem.

PyRIT is designed for flexible adversarial testing of custom application endpoints, external APIs, proprietary agent flows, RAG layers, tools, and business logic. It is the stronger fit when testers need direct control over attack orchestration, prompts, payloads, jailbreaks, data leakage tests, or multi-turn conversations.

## Decision rule

- Use **Microsoft Foundry** for managed evaluation and red teaming of supported Foundry and Azure OpenAI targets.
- Use **PyRIT** for custom endpoints, non-Foundry application layers, and bespoke adversarial orchestration.
- Use **both** when a production system needs repeatable platform evaluation plus realistic end-to-end application testing.

## Partner relevance

- Separates model quality testing from full application and agent security validation.
- Helps scope AI assurance engagements around the actual system boundary.
- Supports a layered offer: baseline managed evaluation, followed by custom adversarial testing where needed.

## Related pages

- [AI Red-Teaming Tool Selection](../10-Notes/concepts/ai-red-teaming-tool-selection.md)
- [AI Governance](../10-Notes/concepts/ai-governance.md)
- [Data and AI](../100-Crucible/DataAISolutionArea.md)
- [Security](../100-Crucible/SecuritySolutionArea.md)
