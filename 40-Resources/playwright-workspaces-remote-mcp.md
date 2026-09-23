---
title: Playwright Workspaces Remote MCP
type: resource
created: 2026-09-18
updated: 2026-09-18
tags: [playwright, mcp, microsoft-foundry, browser-automation, agentic-ai, governance]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/announcing-the-playwright-workspaces-remote-mcp-server-for-agentic-browser-autom/4555698
  - raw/2026-09-18-playwright-workspaces-remote-mcp/source.md
status: active
---

# Playwright Workspaces Remote MCP

Preview managed-browser service that exposes remote Playwright capabilities to Microsoft Foundry, GitHub Copilot CLI, and other MCP-compatible agents without local browser infrastructure.

## Operating Pattern

```text
observe -> act -> wait -> verify -> close
```

- Inspect with accessibility snapshots or focused element finding.
- Perform one bounded action.
- Wait for an explicit condition.
- Verify the resulting state before continuing.
- Close the remote session and retain only necessary diagnostic evidence.

## Architecture and Governance

- Workspace-scoped HTTPS endpoint using Streamable HTTP and API-key authentication
- Browser tools for navigation, interaction, tabs, uploads, screenshots, diagnostics, and lifecycle
- VNet injection for private application access
- Live View and bounded snapshot, console, network, and screenshot evidence
- Token rotation, workspace isolation, least privilege, action allowlists, approval gates, retention controls, and emergency session termination

## Partner Motion

- Last-mile automation discovery for browser-only workflows
- Controlled browser-agent proof of value
- Foundry and Copilot CLI integration
- Private-application networking and identity
- Reliability, observability, and incident runbooks
- Reusable governed browser-agent accelerator

## Related Pages

- [[model-context-protocol-mcp]]
- [[pydantic-ai-playwright-browser-automation]]
- [[safe-agent-controls-foundry]]

