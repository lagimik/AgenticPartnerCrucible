# Playwright Workspaces Remote MCP Source Capture

Captured: 2026-09-18

## Provenance

- Announcement: https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/announcing-the-playwright-workspaces-remote-mcp-server-for-agentic-browser-autom/4555698
- Published: 2026-09-17
- Author: Nandini Muralidharan
- Source type: Public Microsoft Tech Community announcement

## Direct Source Summary

Microsoft announced the Playwright Workspaces Remote MCP Server in preview as a managed remote-browser service for MCP-compatible agents. It removes the need to install Playwright, browser binaries, or a local MCP server in the agent environment. A workspace-scoped HTTPS endpoint uses Streamable HTTP and API-key authentication.

The preview exposes 22 tools for navigation, accessibility-based inspection, interaction, tabs, file uploads, screenshots, diagnostics, and session lifecycle. Microsoft recommends an observe-act-wait-verify-close loop rather than long unchecked action sequences. The service can connect to Microsoft Foundry, GitHub Copilot CLI, and other MCP-compatible environments.

VNet injection supports private-site access. Live View, snapshots, screenshots, console messages, and network requests provide bounded operational evidence. The service complements rather than replaces the Playwright SDK, playwright-cli, Foundry's integrated browser automation, and managed Playwright test execution.

## Interpretation

Partners can identify last-mile browser-only workflows, implement bounded and approval-gated browser agents, integrate private applications, establish token and workspace governance, and package reusable reliability, evidence, and session-cleanup controls.

