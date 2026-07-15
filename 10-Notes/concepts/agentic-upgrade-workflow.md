---
title: Agentic Upgrade Workflow
type: concept
created: 2026-07-13
updated: 2026-07-13
tags:
  - agentic-ai
  - modernization
  - dotnet
  - github-copilot
  - workflow-pattern
sources:
  - raw/2026-07-13-modernize-dotnet-github-copilot-app/source.md
status: active
---

# Agentic Upgrade Workflow

A multi-phase autonomous workflow pattern where an AI agent drives a complex migration or upgrade end-to-end, with each phase informing the next.

## Pattern

```
Assess → Plan → Task → Execute → Validate
```

Each phase produces structured output consumed by the next. New information (broken builds, dependency conflicts, ordering constraints) feeds back into planning.

## Characteristics

- **Iterative feedback** – Failures during execution reshape remaining tasks.
- **Structured artifacts** – Each phase produces machine-readable plans, not free-form chat.
- **Interactive canvas** – A live dashboard surfaces the full workflow state for human review and steering.
- **Multi-surface** – Same workflow runs in IDE, CLI, or web app.

## Example: .NET Upgrade Agent

The GitHub Copilot upgrade agent implements this pattern for .NET modernization:

1. Assess framework version, NuGet packages, breaking APIs, project dependencies.
2. Generate structured upgrade plan.
3. Break plan into implementation tasks.
4. Execute transformations, fix build failures, validate.

## Related Pages

- [[modernize-dotnet-github-copilot-app]]
- [[agentic-ai]]
- [[github-copilot-cli]]
