---
title: Partner Crucible Signal Sources
description: Source configuration for Partner Crucible RSS, Atom, and MCP signal scans
---

## Signal Source Configuration

The Partner Crucible signal scan uses the source definitions in
[`rss-partner-signal-sources.json`](rss-partner-signal-sources.json).

The `feeds` array declares RSS and Atom feeds. The `mcp_sources` array declares
MCP endpoints separately; they are not feeds. Microsoft Release Communications
provides Azure Updates and Microsoft 365 Roadmap signals through
`https://www.microsoft.com/releasecommunications/mcp` using Streamable HTTP.
Its public read-only queries required no authentication when verified on
2026-10-24.

Only sources declared in that JSON file are in scope for the scan. Query both
configured MCP collections alongside every feed, applying the same seven-day
announcement window and partner-relevance criteria. Connection and query
instructions are in the
[signal skill reference](.github/skills/partner-crucible-signal/references/RELEASE_COMMUNICATIONS_MCP.md).