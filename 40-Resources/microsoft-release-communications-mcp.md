---
title: Microsoft Release Communications MCP Server
type: resource
created: 2026-10-27
updated: 2026-10-27
tags: [mcp, roadmap, azure, microsoft-365, change-management]
sources:
  - https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide
  - https://www.microsoft.com/releasecommunications/mcp
  - raw/2026-10-27-github-open-issues-125-134/issues.md
  - raw/2026-10-27-github-open-issues-125-134/sources.md
status: active
---

# Microsoft Release Communications MCP Server

## Source Summary

[Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/mrc-mcp?view=o365-worldwide)
documents a public, free remote MCP server for the AI at Work Roadmap
(formerly Microsoft 365 Roadmap) and Azure Updates. It requires no
authentication or server license and uses Streamable HTTP at
`https://www.microsoft.com/releasecommunications/mcp`.
Microsoft API Terms of Use still apply.

The service supports filtered list queries, title search, pagination, and
full-detail retrieval by item ID. Lists return up to 50 items with truncated
descriptions; the underlying release information refreshes daily. A direct
browser visit can return HTTP 405 without indicating that MCP is unavailable.

## Evidence and Query Boundaries

Distinguish post publication/modification from feature availability or retirement
dates. Fetch every page for complete coverage and retrieve item details when
the list summary is insufficient. Roadmap estimates remain estimates.

The reviewed Learn page lists `get_recent_roadmaps` and `get_roadmap_by_id`;
the live schema verified in this workspace on October 24 exposed
`get_recent_m365_roadmaps` and `get_m365_roadmap_by_id`.
Discover live schemas instead of hard-coding documentation names.
This is a naming discrepancy, not evidence that either collection is empty.

## Partner Application

**Interpretation:** Build customer change-readiness briefings, retirement
inventories, and release-impact reviews from public item evidence. Match each
item to the customer's cloud, platform, licensing, and deployment scope before
recommending action. The service is not tenant-specific Message Center access.

## Related Pages

- [Model Context Protocol](../10-Notes/concepts/model-context-protocol-mcp.md)
- [Signal Source Configuration](../SOURCES.md)
- [Signal MCP Procedure](../.github/skills/partner-crucible-signal/references/RELEASE_COMMUNICATIONS_MCP.md)
