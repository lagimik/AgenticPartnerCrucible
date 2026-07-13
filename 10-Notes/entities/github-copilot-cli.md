---
title: GitHub Copilot CLI
type: entity
created: 2026-07-10
updated: 2026-07-13
tags:
  - github-copilot
  - ai-coding-agent
  - cli
  - dotnet-modernization
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-skills/.github/plugin/plugin.json
  - raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
status: active
---

# GitHub Copilot CLI

GitHub Copilot CLI is the recommended installation surface for the `skills-for-fabric` plugin bundles. The source README shows plugin marketplace commands for adding `microsoft/skills-for-fabric` and installing complete or focused bundles.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
- [[modernize-dotnet-github-copilot-app]]
- [[agentic-upgrade-workflow]]

## Source Notes

- The README describes `/plugin marketplace add microsoft/skills-for-fabric` and `/plugin install fabric-skills@fabric-collection`.
- Plugin manifests define bundle names, versions, skills, agents, and MCP server configuration.

## .NET Upgrade Agent

The GitHub Copilot upgrade agent (`microsoft/upgrade-agent-plugins`) runs .NET modernization workflows across Visual Studio, VS Code, GitHub Copilot CLI, and the GitHub Copilot app. The upgrade canvas provides a live interactive view of the assess → plan → task → execute → validate pipeline.
