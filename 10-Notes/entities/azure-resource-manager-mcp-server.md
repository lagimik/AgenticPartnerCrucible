---
title: Azure Resource Manager MCP Server
type: entity
created: 2026-11-14
updated: 2026-11-14
tags: [azure, arm, mcp, infrastructure, finops]
sources:
  - https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/what%E2%80%99s-new-in-the-azure-resource-manager-mcp-server-at-ignite-2026/4571824
  - raw/2026-11-14-arm-mcp-ignite/source.md
status: active
---

# Azure Resource Manager MCP Server

The [Ignite 2026 expansion announcement](../../40-Resources/azure-resource-manager-mcp-ignite-2026.md)
describes MCP-based Azure control-plane access for discovery, schema-informed
changes, ARM deployment management, exact resource reads, and cost analysis.
It is distinct from the public read-only
[Release Communications MCP](../../40-Resources/microsoft-release-communications-mcp.md).

## Operating Boundaries

Discover, plan, change, and verify form a connected workflow, but tool exposure
is not authorization. Validate live schemas, provider support, identity
permissions, and approval controls before enabling consequential operations.

The article's remote Skills feature is experimental and opt-in through
`x-mcp-toolset: Skills`; it is not enabled by default. Its inconsistent
`get_skill`/`get_skills` naming requires live-schema verification.
No connection or product-availability verification was performed here.

## Related Pages

- [Ignite Expansion Resource](../../40-Resources/azure-resource-manager-mcp-ignite-2026.md)
- [Model Context Protocol](../concepts/model-context-protocol-mcp.md)
- [AI Governance](../concepts/ai-governance.md)
