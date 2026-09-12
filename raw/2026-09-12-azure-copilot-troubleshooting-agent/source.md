# Azure Copilot Troubleshooting Agent Source Capture

Captured: 2026-09-12

## Provenance

- Announcement: https://techcommunity.microsoft.com/blog/appsonazureblog/azure-copilot-announces-general-availability-of-the-troubleshooting-agent/4554549
- Product documentation: https://learn.microsoft.com/en-us/azure/copilot/troubleshooting-agent
- Announcement title: Azure Copilot announces general availability of the Troubleshooting Agent
- Published: 2026-09-09
- Announcement author account: `christinchen` (Microsoft)

## Direct Source Summary

Azure Copilot Troubleshooting Agent is generally available through Azure Copilot and Support + Troubleshooting in the Azure portal. It uses the signed-in user's Azure context, supported resource diagnostics, identity, and role-based access control to investigate operational issues, explain evidence, recommend actions, and prepare a contextualized support request when an issue remains unresolved.

Deep troubleshooting for Azure Compute and Azure Kubernetes Service is generally available. Compute coverage includes virtual machines, virtual machine scale sets, and Azure Compute Fleet. AKS coverage includes application startup, deployments, scheduling, networking, scaling, upgrades, memory, image pulls, throttling, and cluster performance. Microsoft Learn identifies Azure Local and Microsoft Entra troubleshooting as public preview.

The documented workflow is:

```text
Trigger -> scope -> diagnose -> resolve -> escalate
```

Automatic mitigation and diagnostic depth vary by service, resource type, issue category, and available evidence. Users remain responsible for reviewing recommendations and deciding which actions to take.

The agent has no separate license, subscription, or per-query charge. Standard charges for the underlying Azure resources and existing support plans continue to apply.

## Evidence Excerpts

- "The Troubleshooting Agent is generally available in Azure Copilot and Support + Troubleshooting in the Azure portal."
- "Azure Compute and Azure Kubernetes Service (AKS) are the first services to offer these enhanced troubleshooting experiences."
- "The experience respects your identity and Azure role-based access control (RBAC)."
- "There is no separate license or per-query charge."
- "You remain in control of reviewing recommendations and deciding which actions to take."

## Interpretation

For partners, the immediate opportunity is to incorporate the agent into Compute and AKS support runbooks, standardize evidence review and escalation handoffs, and offer readiness work around Azure Copilot access, RBAC, diagnostics, and operational procedures. The sources do not provide a quantified reduction in resolution time and do not support positioning the capability as universal autonomous remediation.
