# Foundry Toolkit + Foundry Hosted Agents Workshop

**Source:** https://github.com/microsoft-foundry/Foundry_Toolkit_for_VSCode_Lab/
**Captured:** 2026-07-13
**Issue:** lagimik/AgenticPartnerCrucible#4

---

Build, test, and deploy AI agents to Microsoft Foundry Agent Service as Hosted Agents — entirely from VS Code using the Microsoft Foundry extension and Foundry Toolkit.

## Architecture Flow

Foundry extension scaffolds the agent → customize code & instructions → test locally with Agent Inspector → deploy to Foundry (Docker image pushed to ACR) → verify in Playground.

## Labs

| Lab | Description |
|-----|-------------|
| Lab 01 - Single Agent | Build the "Explain Like I'm an Executive" Agent, test locally, deploy to Foundry |
| Lab 02 - Multi-Agent Workflow | Build the "Resume → Job Fit Evaluator" - 4 agents collaborate to score resume fit and generate a learning roadmap |

## Stack

- Python 3.10+
- Microsoft Agent Framework v1.1.0+
- Azure OpenAI (GPT-4.1 / GPT-4.1-mini)
- Azure CLI + Azure Developer CLI (azd)
- Docker (optional)
- Foundry Toolkit VS Code extension

## Lab 01: "Explain Like I'm an Executive" Agent

Single-purpose agent that translates technical jargon into boardroom-ready summaries: what happened, business impact, next step.

## Lab 02: Multi-Agent Workflow

4-agent Resume → Job Fit Evaluator pipeline. Agents collaborate to score resume fit and generate learning roadmaps.

## Structure

```
workshop/
├── lab01-single-agent/
│   ├── docs/ (00-prerequisites through 08-troubleshooting)
│   └── agent/ (agent.yaml, Dockerfile, main.py, requirements.txt)
└── lab02-multi-agent/
    ├── docs/ (00-prerequisites through 08-troubleshooting)
    └── PersonalCareerCopilot/ (agent.yaml, Dockerfile, main.py, requirements.txt)
```

## Required Permissions

| Scenario | Required roles |
|----------|---------------|
| Create new Foundry project | Azure AI Owner on Foundry resource |
| Deploy to existing project (new resources) | Azure AI Owner + Contributor on subscription |
| Deploy to fully configured project | Reader on account + Azure AI User on project |

Note: Azure Owner/Contributor roles only include management permissions, not development (data action) permissions. You need Azure AI User or Azure AI Owner to build and deploy agents.

## Key Points

- Hosted Agents are currently in preview
- The `agent/` folder is automatically scaffolded by the Foundry extension
- Uses `/responses` API for agent communication
- Agent Inspector provides local testing at localhost:8088
