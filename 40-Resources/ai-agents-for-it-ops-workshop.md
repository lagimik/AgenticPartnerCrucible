---
title: AI Agents for IT and Operations Workshop
type: resource
created: 2026-08-21
updated: 2026-08-21
tags:
  - ai-operations
  - microsoft-foundry
  - aks
  - workshop
  - infrastructure
sources:
  - https://github.com/microsoft/AIAgentsforITOps
  - raw/2026-08-21-github-open-issues-55-63/issues.md
status: active
---

# AI Agents for IT and Operations Workshop

This Microsoft workshop teaches infrastructure management for AI agents rather than agent development. It covers managed identity and RBAC, private networking, Key Vault, observability, and cost management.

## Two Paths

| Path | Agent runtime | Best fit |
| --- | --- | --- |
| Custom agent | AKS with direct Azure OpenAI and custom RAG | Teams needing full hosting, scaling, and implementation control |
| Foundry-hosted agent | Microsoft Foundry with a declarative knowledge base; AKS hosts the sample UI | Teams preferring managed lifecycle, tracing, evaluation, and hosting |

Both paths use the same conference-expert scenario so teams can compare operational ownership without changing the user experience.

## Important Limitation

The repository states that both paths are deployable, but later labs for the Foundry-hosted path are still being written. Workshop environments also incur ongoing Azure costs and should be deleted after use.

## Related Pages

- [[agentic-cloud-operations]]
- [[microsoft-foundry-agent-selection]]
- [[azure-ai-foundry]]
