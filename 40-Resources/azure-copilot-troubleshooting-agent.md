---
title: Azure Copilot Troubleshooting Agent
type: resource
created: 2026-09-12
updated: 2026-09-12
tags:
  - azure-copilot
  - troubleshooting
  - agentic-operations
  - aks
  - compute
  - support
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/azure-copilot-announces-general-availability-of-the-troubleshooting-agent/4554549
  - https://learn.microsoft.com/en-us/azure/copilot/troubleshooting-agent
  - raw/2026-09-12-azure-copilot-troubleshooting-agent/source.md
status: active
---

# Azure Copilot Troubleshooting Agent

Azure Copilot Troubleshooting Agent is a generally available, built-in Azure portal capability for moving from an operational symptom to a grounded diagnosis, recommended action, or contextualized support escalation.

## Workflow

```text
Describe issue -> scope resource -> gather diagnostics -> identify likely cause
               -> recommend or apply approved fix -> escalate with context
```

The agent is available through Azure Copilot and Support + Troubleshooting. It uses the signed-in user's resource context, available diagnostic evidence, identity, and Azure role-based access control. Recommendations remain subject to human review.

## Service Coverage

Deep troubleshooting is generally available for:

- **Azure Compute** - Virtual Machines, Virtual Machine Scale Sets, and Azure Compute Fleet across restart, connectivity, boot, performance, allocation, deployment, agent-health, instance-health, update, zone, and capacity scenarios.
- **Azure Kubernetes Service** - Application startup, deployments, scheduling, service connectivity, networking, scaling, upgrades, memory termination, image pulls, throttling, and degraded cluster performance.

Microsoft Learn identifies Azure Local and Microsoft Entra troubleshooting capabilities as public preview. Diagnostic depth and available remediation vary by service, resource type, issue, and available evidence.

## Operating Boundaries

- Automatic mitigation is not available for every issue or resource type.
- The agent can only use diagnostic data and checks available to the selected resource and scenario.
- Users should review recommendations before changing the environment.
- Unresolved investigations can be transferred into a prepopulated Azure Support request with session context.
- There is no separate license, subscription, or per-query charge; normal resource and support-plan charges still apply.

## Partner Relevance

- Add agent-assisted diagnosis to Compute and AKS managed-service runbooks.
- Standardize resource selection, prompt patterns, evidence review, and support escalation.
- Offer readiness services for Azure Copilot access, RBAC, diagnostics, and operational governance.
- Measure investigation quality and time-to-supported-hypothesis rather than assuming autonomous remediation or a guaranteed reduction in resolution time.

## Related Pages

- [[agentic-cloud-operations]]
- [[azure-copilot-observability-agent]]
- [[azure-sre-agent-incident-response-playbook]]
- [Azure Infrastructure Workloads](../100-Crucible/AzureInfrastructureSolutionArea.md)
