---
title: Hypervelocity Engineering Core
type: resource
created: 2026-08-21
updated: 2026-08-21
tags:
  - github-copilot
  - agentic-sdlc
  - developer-tools
  - workflow
sources:
  - https://github.com/microsoft/hve-core
  - raw/2026-08-21-github-open-issues-55-63/issues.md
status: active
---

# Hypervelocity Engineering Core

HVE Core is Microsoft's opinionated, rapidly evolving agentic software-development framework for GitHub Copilot. It packages specialized agents, reusable prompts, coding instructions, and validated skills into repeatable workflows.

## Operating Model

- **Agents** specialize research, planning, implementation, and review.
- **Prompts** provide repeatable workflow entry points.
- **Instructions** apply engineering standards automatically.
- **Skills** add reusable capabilities and tools.
- **RPI** organizes work into Research, Plan, Implement, and Review.

## Adoption Guidance

HVE Core should be treated as a pattern library rather than a stable production dependency. Teams should copy or adapt useful patterns into an agentic SDLC they own, assess compatibility risk, and use reviewed or immutable release channels when repeatability matters.

## Distribution

HVE Core is available as a VS Code extension and a GitHub Copilot CLI plugin. The repository documents current, reviewed prerelease, reviewed stable, and immutable versioned channels.

## Related Pages

- [[agentic-upgrade-workflow]]
- [[github-copilot-cli]]
- [[ai-assistant-skills]]
