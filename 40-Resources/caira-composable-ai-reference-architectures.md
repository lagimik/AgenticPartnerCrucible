---
title: CAIRA Composable AI Reference Architectures
type: resource
created: 2026-08-28
updated: 2026-08-28
tags:
  - agentic-ai
  - reference-architecture
  - infrastructure-as-code
  - microsoft-foundry
  - azure
sources:
  - https://github.com/microsoft/CAIRA
  - raw/2026-08-28-github-open-issues-65-70/issues.md
status: active
---

# CAIRA Composable AI Reference Architectures

CAIRA is a Microsoft reference library for coding agents that build Azure AI solutions. Its skill directs an agent to inspect the repository and copy or adapt only the components needed for a scenario.

## Reference Components

- Terraform for Microsoft Foundry accounts, projects, and model deployments
- Terraform for Azure Container Apps hosting an API and React frontend
- TypeScript APIs using the OpenAI Agents SDK or Foundry Agent Service
- C# APIs using Microsoft Agent Framework
- A minimal React frontend with a backend-for-frontend proxy

## Operating Model

Each component is independent and designed to be readable, testable, replaceable, and locally validated. The contributor workflow includes code, Terraform, container, dependency-audit, Trivy, and CAIRA skill tests.

The weekly validation workflow can use Azure OIDC and a short-lived Foundry token with the least-privilege Cognitive Services OpenAI User role.

## Related Pages

- [[azure-ai-foundry]]
- [[ai-agent-lifecycle]]
- [[agent-skill-common-architecture]]
- [Data and AI](../100-Crucible/DataAISolutionArea.md)
