---
title: Azure AI Gateway
type: entity
created: 2026-11-20
updated: 2026-11-20
tags: [azure-ai-gateway, api-management, models, mcp]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580080
  - https://learn.microsoft.com/en-us/azure/ai-gateway/ai-gateway-resource
status: active
---

# Azure AI Gateway

Azure's fully managed service for governed model and MCP traffic, announced GA
in November 2026. Its dedicated `Microsoft.ApiManagement/aigateways` resource
replaces the former APIM `AIGateway` SKU representation, not other APIM SKUs.
Gateway GA does not establish feature parity, unrestricted private endpoints,
backend authorization, or free model consumption.

## Related

- [GA, Migration Deadline, and Capability Boundaries](../../40-Resources/azure-ai-gateway-ga.md)
- [APIM AI Gateway Capabilities](../../40-Resources/azure-api-management-ai-gateway-capabilities.md)
- [Microsoft Agent 365](microsoft-agent-365.md)
- [Runtime Governance Integration](../../40-Resources/agent-365-apim-runtime-governance.md)
- [Azure Agent Grid](azure-agent-grid.md)
- [AI Gateway Pattern](../concepts/ai-gateway-pattern.md)
