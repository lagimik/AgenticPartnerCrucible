---
title: Azure Agent Grid Preview and Enrollment Boundaries
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [agent-grid, zero-trust, network-security, workload-identity, mcp]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580684
  - https://learn.microsoft.com/en-us/azure/agent-grid/overview
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Azure Agent Grid Preview and Enrollment Boundaries

## Source Summary

[Update 580684](https://azure.microsoft.com/en-us/updates?id=580684) labels Agent
Grid **public preview**. The [Learn overview](https://learn.microsoft.com/en-us/azure/agent-grid/overview)
explicitly describes **limited-preview access requiring enrollment approval**.
Retain both source statements and use documented eligibility for pilot planning.

Agent Grid enforces identity-based network policies outside an enrolled agent's
trust boundary without customer sidecars or agent-code changes. Workloads receive
short-lived SPIFFE identities and mTLS connectivity. Controls include FQDN/URL
filtering, TLS inspection, per-tool MCP filtering, and Prompt Shields through a
customer-owned Content Safety resource. Flow logs and maps provide enforcement
evidence.

## Preview Coverage

| Boundary | Documented scope |
| --- | --- |
| Enrollment | Attaching compute does not govern its traffic; only enrolled members are intercepted. |
| Compute | ACI sandbox groups and AKS sandbox/traditional workloads; not Foundry hosted agents, Container Apps, or Copilot Studio. |
| Network | ACI requires public IPs; VNet-integrated ACI groups and private AKS clusters unsupported; TCP/IPv4 only. |
| Placement | Compute and grid in the same subscription and region. |
| Regions | Central US, West US 2, Sweden Central, Australia East, Indonesia Central. |
| Identity | Workload certificates are not connected to Entra Agent ID in this preview. |
| Inspection | TLS/content policy source must be a member; TLS inspection uses an Azure-managed CA. |

ARM/CLI may retain the former internal name Agent Fabric. A network policy is
not source authorization, business approval, or proof that every prompt
injection will be detected.

## Partner Application

**Interpretation:** Confirm limited-preview access and supported placement before
designing a bounded pilot. Inventory enrolled versus merely attached workloads,
approved destinations/tools, trust configuration, inspection data handling, and
diagnostic retention. Exercise allow/deny flows and verify observed enforcement.
No grid or workload was enrolled.

## Related

- [Azure Agent Grid](../10-Notes/entities/azure-agent-grid.md)
- [Azure AI Gateway](azure-ai-gateway-ga.md)
- [Agent 365 Runtime Governance](agent-365-apim-runtime-governance.md)
- [SAFE Agent Controls](safe-agent-controls-foundry.md)
- [Project Perception](project-perception-agentic-security-stack.md)
