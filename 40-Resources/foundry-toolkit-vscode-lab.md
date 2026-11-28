---
title: "Foundry Toolkit for VS Code Lab"
type: resource
created: 2026-07-13
updated: 2026-11-28
tags:
  - azure-ai-foundry
  - hosted-agents
  - vs-code
  - workshop
  - microsoft-agent-framework
sources:
  - https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
  - raw/2026-07-13-foundry-toolkit-vscode-lab/source.md
status: stale
claims:
  - id: claim-001
    text: "This workshop's hosted-agent path uses /responses communication and deploys Docker images through Azure Container Registry; it is not a statement about every supported Foundry deployment path."
    confidence: 0.95
    status: provisional
    evidence:
      - source: raw/2026-07-13-foundry-toolkit-vscode-lab/source.md
        kind: documentation
        excerpt: "Uses /responses API for agent communication... deploy to Foundry (Docker image pushed to ACR)"
    captured: 2026-07-13
    updated: 2026-11-27
  - id: claim-002
    text: "The workshop requires Foundry data-action roles, with scope-dependent combinations of Azure AI Owner, Azure AI User, Reader and Contributor; subscription Owner/Contributor alone is not sufficient for its development flow."
    confidence: 0.95
    status: provisional
    evidence:
      - source: https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
        kind: documentation
        excerpt: "Deploy to fully configured project | Reader on account + Azure AI User on project"
    captured: 2026-07-13
    updated: 2026-11-27
---

# Foundry Toolkit for VS Code Lab

## Review Scope

The November 21 review flagged the age of the July capture. The November 27
README review updated prerequisites and role boundaries, as recorded below.
Claims remain provisional for this changing workshop and preview deployment
path; the review was not an execution test.

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

- Python 3.12+, Microsoft Agent Framework v1.1.0+
- Azure OpenAI (GPT-4.1 / GPT-4.1-mini)
- Azure CLI + Azure Developer CLI (azd)
- Foundry Toolkit VS Code extension

## Revalidation

The upstream README was rechecked on 2026-11-27. It labels Hosted Agents as
preview with limited regions, now lists Python 3.12+, and distinguishes role
requirements for project creation, new-resource deployment and an already
configured project. The claims remain provisional because this is a changing
workshop and preview deployment path, not universal service guidance.

## Key Links

- Repository: https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
- Hosted Agents docs: https://learn.microsoft.com/azure/foundry/agents/concepts/hosted-agents

## Related Pages

- [[azure-ai-foundry]]
- [[microsoft-foundry-labs]]
- [[agentic-ai]]
