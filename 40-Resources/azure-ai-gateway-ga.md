---
title: Azure AI Gateway GA and Resource Migration
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [azure-ai-gateway, api-management, mcp, governance, migration]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580080
  - https://learn.microsoft.com/en-us/azure/ai-gateway/ai-gateway-resource
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Azure AI Gateway GA and Resource Migration

## Source Summary

[Update 580080](https://azure.microsoft.com/en-us/updates?id=580080) announces
Azure AI Gateway GA in November 2026 as a fully managed service for model and
MCP traffic. It describes centralized access, stable model aliases, intelligent
selection, weighted/priority routing, session affinity, failover, usage and
estimated-cost attribution, budgets, quotas, and rate limits.
Foundry, Agent 365, Entra ID, and Application Insights provide integrations.
The dated 10,000 free gateway requests per subscription/month offer does not
make backend model or tool consumption free.

## Resource Transition and Evidence Boundaries

The [migration guide](https://learn.microsoft.com/en-us/azure/ai-gateway/ai-gateway-resource)
replaces only APIM's former `AIGateway` SKU representation with
`Microsoft.ApiManagement/aigateways`, using ARM API `2026-11-01`. Other APIM SKUs
remain functional. Complete migration **before January 15, 2027**; the guide
says old AIGateway resources are permanently removed after retirement.

| Cutover concern | Required distinction |
| --- | --- |
| Resource and identity | A new resource ID requires new scoped role assignments; a new system identity needs backend permissions. |
| Client connection | Read `properties.frontend.defaultHostname`, add HTTPS, and update clients/allowlists/monitoring; key authentication uses `Authorization: Bearer`. |
| Configuration | Recreate and verify models, aliases, MCP servers/tools, policies, telemetry, and networking; do not assume automatic parity. |
| Network access | Private endpoints are approval-gated public preview, not implied GA. |
| Content safety | The update advertises guardrails, but migration documentation says the content safety policy is unsupported; select and verify an alternative control. |

Earlier Learn guidance describes the **APIM gateway extension** as not a separate
offering. Retain that historical scope without applying it to the new dedicated
service or inferring that every APIM policy carries over.

## Partner Application

**Interpretation:** Inventory the resource type and consumers before proposing
cutover. Validate denied access, model aliases, representative MCP calls, safety
controls, backend permissions, and actual cost attribution. Retain the old
endpoint during a bounded rollback period and retire it only after stable traffic
evidence. This curation did not migrate or remove any resources.

## Related

- [Azure AI Gateway](../10-Notes/entities/azure-ai-gateway.md)
- [APIM AI Gateway Capabilities](azure-api-management-ai-gateway-capabilities.md)
- [Agent 365 Runtime Governance Integration](agent-365-apim-runtime-governance.md)
- [AI Gateway Pattern](../10-Notes/concepts/ai-gateway-pattern.md)
- [Agent Grid Network Controls](azure-agent-grid-preview.md)
