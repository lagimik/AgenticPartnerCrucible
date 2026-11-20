---
title: Agent 365 Governance with APIM and Azure AI Gateway
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [agent-365, api-management, azure-ai-gateway, mcp, runtime-governance]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580055
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Agent 365 Governance with APIM and Azure AI Gateway

## Source Summary

[Update 580055](https://azure.microsoft.com/en-us/updates?id=580055) announces
November 2026 GA integration between centralized Microsoft Agent 365 governance
and runtime controls in Azure API Management and Azure AI Gateway.

- Discover supported gateways and registered MCP servers into Agent 365 inventory.
- Define governance policies and enforce server- and individual-tool blocking
  through supported gateway paths.
- Observe agent-to-tool interactions for auditing and investigations.
- Use supported Defender and Purview capabilities for threat and sensitive-data
  risks in tool requests and responses.

## Control Boundaries

Discovery requires supported registered resources; it is not universal agent or
tool discovery. Inventory, policy definition, routed enforcement, backend
authorization, and activity evidence are separate. The GA integration does not
make every Defender/Purview feature GA or protect unregistered/direct traffic.
Resource-specific gateway capabilities and migration limitations still apply.

## Partner Application

**Interpretation:** Trace a supported agent through registry, gateway, MCP server,
tool, and backend identity. Test an approved read and a denied write/tool call,
inspect enforcement and audit evidence, and check direct-route exposure.
Keep consequential business-action approval distinct from technical tool access.
No policies or customer permissions were changed.

## Related

- [Microsoft Agent 365](../10-Notes/entities/microsoft-agent-365.md)
- [Azure AI Gateway](../10-Notes/entities/azure-ai-gateway.md)
- [Gateway GA and Migration](azure-ai-gateway-ga.md)
- [Agent 365 Runtime Protection](microsoft-agent-365-runtime-protection.md)
- [Agent Grid Network Controls](azure-agent-grid-preview.md)
