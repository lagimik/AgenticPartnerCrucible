---
title: Model Context Protocol MCP
type: concept
created: 2026-07-10
updated: 2026-11-14
tags:
  - mcp
  - ai-tools
  - integration
sources:
  - https://techcommunity.microsoft.com/blog/azuregovernanceandmanagementblog/what%E2%80%99s-new-in-the-azure-resource-manager-mcp-server-at-ignite-2026/4571824
  - https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/mcp-setup/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/.mcp.json
status: active
---

# Model Context Protocol MCP

Model Context Protocol, or MCP, provides live tool access to external systems and APIs. In `skills-for-fabric`, skills provide instructions and patterns while MCP servers provide live access where supported.

## FabricIQ Example

The repo includes FabricIQ MCP configuration for Power BI data analysis. The documented FabricIQ server supports artifact discovery, report metadata inspection, semantic model schema inspection, value search, query execution, and report ID resolution.

## Related Pages

- [ARM MCP Operations and Cost Analysis](../../40-Resources/azure-resource-manager-mcp-ignite-2026.md) - Discovery, schema-based planning, changes, and exact-state verification, with experimental Skills opt-in.
- [Azure Resource Manager MCP Server](../entities/azure-resource-manager-mcp-server.md)
- [Microsoft Release Communications MCP](../../40-Resources/microsoft-release-communications-mcp.md) - Public release discovery, pagination, details, and live-schema naming caveats.
- [[skills-for-fabric]]
- [[power-bi]]
- [[github-copilot-cli]]
- [[ai-assistant-skills]]
- [[multitenant-ai-agent-governance-architecture]]
- [[agent-execution-sandbox-isolation]]
- [[postgres-mcp-server]]
