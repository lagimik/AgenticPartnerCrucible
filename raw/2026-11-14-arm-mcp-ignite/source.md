---
title: ARM MCP server Ignite 2026 expansion - source capture
source_url: https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/what%E2%80%99s-new-in-the-azure-resource-manager-mcp-server-at-ignite-2026/4571824
publisher: Microsoft Community Hub
author: Steven Bucher
published: 2026-11-13
captured: 2026-11-14
capture_type: source-summary
---

# Source Capture

Paraphrased summary of the retrieved public article, not a full-text copy.
The page displays November 13 publication and an earlier November 12 update
label; both are preserved here without inferring a chronology correction.

## Source Summary

The Azure Resource Manager MCP server expansion adds resource and resource-group
create/update operations, provider-defined resource actions, exact resource
reads, stronger ARM deployment workflows, and cost analysis.

The article describes Resource Graph discovery followed by schema-informed
planning, PUT/POST changes, and verification using exact resource state and
deployment/async-operation status. Bicep MCP can author and build Bicep into ARM
templates, while ARM MCP deploys and manages them.

Cost tools cover general and AKS costs, public retail prices, and asynchronous
negotiated price-sheet retrieval. General cost queries support filtering and
grouping.

## Experimental Skills

Remote SKILL.md workflows are experimental, disabled by default, and enabled
through the `x-mcp-toolset: Skills` request header. The article lists workflows
for VM selection, optimization, costs, policy, machine inventory/compliance,
resource management, and deployment. It warns that workflows, tool names, and
behavior can change.

The article first names `list_skills` and `get_skill`, but its final onboarding
steps say `get_skills`. This inconsistency remains unresolved: no live schema
was queried during ingestion.

## Boundaries

The source describes capabilities, not a universal availability, authorization,
or rollback guarantee. What-if previews and operation completion should not be
treated as proof of application health. Public retail pricing and negotiated
billing data are different evidence sources.

The linked documentation and server were not independently inspected.
No server was installed, experimental header enabled, cost data queried,
credentials retrieved, or infrastructure modified.

## Source-Linked References

- https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-resource-manager-mcp-overview
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/bicep-mcp-server
- https://github.com/Azure/Azure-Resource-Manager-MCP/issues
