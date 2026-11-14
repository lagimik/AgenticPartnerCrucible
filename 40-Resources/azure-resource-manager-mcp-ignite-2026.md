---
title: Azure Resource Manager MCP Expansion at Ignite 2026
type: resource
created: 2026-11-14
updated: 2026-11-14
tags: [azure, mcp, infrastructure, governance, finops, agents]
sources:
  - https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/what%E2%80%99s-new-in-the-azure-resource-manager-mcp-server-at-ignite-2026/4571824
  - raw/2026-11-14-arm-mcp-ignite/source.md
status: active
---

# Azure Resource Manager MCP Expansion at Ignite 2026

## Source Summary

Steven Bucher's [November 13 Microsoft Community Hub article](https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/what%E2%80%99s-new-in-the-azure-resource-manager-mcp-server-at-ignite-2026/4571824)
describes ARM MCP moving beyond discovery into resource changes, deployment
management, exact-state verification, and cost analysis.

## Announced Operations

| Stage | Source-listed tools and purpose |
| --- | --- |
| Discover | `generate_query`, `validate_query`, and `execute_query` for Resource Graph discovery. |
| Plan | Resource/action type and schema discovery, plus `whatif_deployment`. |
| Change | `create_or_update_resource_group`, `create_or_update_resource`, `execute_resource_action`, and `create_deployment`. |
| Verify | `get_resource`, `get_deployment_status`, and `get_async_operation_status`; `cancel_deployment` stops a running deployment. |
| Analyze cost | `query_costs`, `query_aks_costs`, `get_retail_prices`, `start_pricesheet_download`, and `get_pricesheet_status`. |

These are blog-reported names, not independently discovered live schemas.
Resource actions include potentially sensitive operations such as key retrieval.
Cancellation is described as stopping deployment, not reverting completed work.

The article connects Bicep MCP authoring/build steps to ARM MCP deployment
and management. Grouped and filtered cost queries support spend-driver analysis;
retail price lookups must remain distinct from negotiated billing data.

## Experimental Skills

Remote workflow discovery uses `list_skills` and, in the main explanation,
`get_skill`. Skills require explicit `x-mcp-toolset: Skills` opt-in, are off by
default, and may change. Workflows span optimization, cost investigation,
pricing estimates, machine configuration, Azure Policy, Resource Graph,
resource management, and ARM deployment.

The final onboarding section instead says `get_skills`; verify the live
schema before implementation rather than assuming either spelling.

## Partner Application

**Interpretation:** Offer a bounded infrastructure-operations pilot with
schema-informed plans, reviewed changes, exact-resource verification, and
cost-driver reporting. Establish permissions, approval gates, audit trails,
and workload-health checks outside model instructions before allowing writes.
Treat experimental skills as optional workflow guidance, not additional
authorization.

## Evidence Boundaries

The article does not establish universal GA, complete provider-action coverage,
automatic rollback, or customer-specific savings. Its page displays November 13
publication but November 12 update metadata. Linked
[ARM MCP documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-resource-manager-mcp-overview)
and [Bicep MCP documentation](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/bicep-mcp-server)
were not independently reviewed; no server was connected or configured during
ingestion.

## Related Pages

- [Azure Resource Manager MCP Server](../10-Notes/entities/azure-resource-manager-mcp-server.md)
- [Model Context Protocol](../10-Notes/concepts/model-context-protocol-mcp.md)
- [AI Governance](../10-Notes/concepts/ai-governance.md)
- [Azure Resource Inventory](azure-resource-inventory-ari.md)
- [Preserved Source Summary](../raw/2026-11-14-arm-mcp-ignite/source.md)
