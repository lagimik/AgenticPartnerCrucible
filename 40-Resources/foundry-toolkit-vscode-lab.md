---
title: "Foundry Toolkit for VS Code Lab"
type: resource
created: 2026-07-13
updated: 2026-07-13
tags:
  - azure-ai-foundry
  - hosted-agents
  - vs-code
  - workshop
  - microsoft-agent-framework
sources:
  - https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
  - raw/2026-07-13-foundry-toolkit-vscode-lab/source.md
status: active
claims:
  - id: claim-001
    text: "Foundry Hosted Agents use the /responses API and are deployed as Docker images pushed to Azure Container Registry."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-foundry-toolkit-vscode-lab/source.md
        kind: documentation
        excerpt: "Uses /responses API for agent communication... deploy to Foundry (Docker image pushed to ACR)"
    captured: 2026-07-13
    updated: 2026-07-13
  - id: claim-002
    text: "Azure AI User or Azure AI Owner role is required to build and deploy agents — standard Owner/Contributor roles only include management permissions."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-foundry-toolkit-vscode-lab/source.md
        kind: documentation
        excerpt: "Azure Owner and Contributor roles only include management permissions, not development (data action) permissions. You need Azure AI User or Azure AI Owner to build and deploy agents."
    captured: 2026-07-13
    updated: 2026-07-13
---

# Foundry Toolkit for VS Code Lab

Microsoft workshop repository for building, testing, and deploying AI agents to Microsoft Foundry Agent Service as Hosted Agents entirely from VS Code.

## Summary

A hands-on workshop with two labs:

| Lab | What you build |
|-----|---------------|
| Lab 01 | "Explain Like I'm an Executive" — single-purpose agent translating jargon to boardroom summaries |
| Lab 02 | "Resume → Job Fit Evaluator" — 4-agent collaborative pipeline |

## Workflow

```
Foundry extension scaffolds agent → customize code → test locally (Agent Inspector) → deploy (Docker → ACR) → verify in Playground
```

## Stack

- Python 3.10+, Microsoft Agent Framework v1.1.0+
- Azure OpenAI (GPT-4.1 / GPT-4.1-mini)
- Azure CLI + Azure Developer CLI (azd)
- Foundry Toolkit VS Code extension

## Key Links

- Repository: https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
- Hosted Agents docs: https://learn.microsoft.com/azure/foundry/agents/concepts/hosted-agents

## Related Pages

- [[azure-ai-foundry]]
- [[microsoft-foundry-labs]]
- [[agentic-ai]]
