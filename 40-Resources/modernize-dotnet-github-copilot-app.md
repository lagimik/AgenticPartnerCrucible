---
title: "Modernize .NET in the GitHub Copilot App"
type: resource
created: 2026-07-13
updated: 2026-07-13
tags:
  - dotnet
  - github-copilot
  - modernization
  - upgrade-agent
sources:
  - https://devblogs.microsoft.com/dotnet/modernize-dotnet-in-github-copilot-app/
  - raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
status: active
claims:
  - id: claim-001
    text: "The GitHub Copilot upgrade agent follows a structured workflow: assess, plan, task, execute, validate."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
        kind: documentation
        excerpt: "The GitHub Copilot upgrade agent assesses your application, generates a structured upgrade plan, creates implementation tasks, and executes the work."
    captured: 2026-07-13
    updated: 2026-07-13
  - id: claim-002
    text: "The upgrade agent is available in Visual Studio, VS Code, GitHub Copilot CLI, and the GitHub Copilot app."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
        kind: documentation
        excerpt: "GitHub Copilot upgrade is also available across the developer tools you already use: Visual Studio, Visual Studio Code, GitHub Copilot CLI."
    captured: 2026-07-13
    updated: 2026-07-13
  - id: claim-003
    text: "The upgrade canvas in the GitHub Copilot app provides a live, interactive view of the full modernization workflow."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
        kind: documentation
        excerpt: "the upgrade canvas gives you a live view of the modernization workflow as it unfolds"
    captured: 2026-07-13
    updated: 2026-07-13
---

# Modernize .NET in the GitHub Copilot App

Microsoft DevBlogs article describing the GitHub Copilot upgrade agent for .NET modernization with an interactive upgrade canvas.

## Summary

The GitHub Copilot upgrade agent automates .NET application upgrades through a multi-phase workflow:

1. **Assessment** – Identifies target framework, NuGet dependencies, breaking API changes, project independence, and ordering.
2. **Planning** – Generates a structured upgrade plan from the assessment.
3. **Task creation** – Breaks the plan into actionable implementation tasks.
4. **Execution** – Applies code transformations, fixes build failures, validates results.

The **Upgrade Dashboard** canvas in the GitHub Copilot app surfaces the full workflow in a single interactive view—assessment, plan, tasks, progress, code changes, failures, and results.

## Availability

| Surface | How to start |
|---------|-------------|
| GitHub Copilot App | Install `microsoft/upgrade-agent-plugins`, open Upgrade Dashboard canvas |
| Visual Studio | Right-click solution/project → Modernize |
| VS Code | Install GitHub Copilot upgrade extension, select Upgrade agent |
| GitHub Copilot CLI | Install upgrade plugin, run from terminal |

## Key Links

- Blog post: https://devblogs.microsoft.com/dotnet/modernize-dotnet-in-github-copilot-app/
- Plugin repo: https://github.com/microsoft/upgrade-agent-plugins

## Related Pages

- [[github-copilot-cli]]
- [[agentic-upgrade-workflow]]
