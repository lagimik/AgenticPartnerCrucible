---
title: GitHub Copilot CLI
type: entity
created: 2026-07-10
updated: 2026-11-21
tags:
  - github-copilot
  - ai-coding-agent
  - cli
  - dotnet-modernization
sources:
  - raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html
  - raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
  - https://github.blog/ai-and-ml/github-copilot/evaluating-performance-and-efficiency-of-the-github-copilot-agentic-harness-across-models-and-tasks/
status: active
---

# GitHub Copilot CLI

GitHub Copilot CLI is the recommended installation surface for the `skills-for-fabric` plugin bundles. The source README shows plugin marketplace commands for adding `microsoft/skills-for-fabric` and installing complete or focused bundles.

## Related Pages

- [GitHub](github.md)
- [Copilot Benchmarks and Workload Validation](../../40-Resources/github-copilot-benchmarks.md) - Harness measurements are not universal model rankings.
- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
- [[modernize-dotnet-github-copilot-app]]
- [[agentic-upgrade-workflow]]

## Source Notes

- The README describes `/plugin marketplace add microsoft/skills-for-fabric` and `/plugin install fabric-skills@fabric-collection`.
- The preserved README describes bundle purposes and notes that some bundles include MCP configuration. Individual plugin manifests are unavailable; verify installed versions and tool schemas before use.

## .NET Upgrade Agent

The GitHub Copilot upgrade agent (`microsoft/upgrade-agent-plugins`) runs .NET modernization workflows across Visual Studio, VS Code, GitHub Copilot CLI, and the GitHub Copilot app. The upgrade canvas provides a live interactive view of the assess → plan → task → execute → validate pipeline.
