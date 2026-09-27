---
title: Agent-First Platforms with Foundry and Container Apps
type: resource
created: 2026-09-26
updated: 2026-09-26
tags: [agent-platform, microsoft-foundry, container-apps, sandboxes, governance]
sources:
  - https://azure.microsoft.com/en-us/blog/designing-agent-first-platforms-what-changes-when-agents-do-the-work/
  - raw/2026-09-26-github-open-issues-101-113/issues.md
status: active
---

# Agent-First Platforms with Foundry and Container Apps

Agent-first applications continuously reason, generate and execute code, use
tools, inspect results, and resume work without a human inside every loop. The
source separates governance of the agent from the runtime where its work
executes.

## Emerging Pattern

- Build, ground, identify, trace, evaluate, and govern agents with Microsoft
  Foundry and Entra Agent ID.
- Execute generated code and file-based work in dedicated Azure Container Apps
  Sandboxes.
- Give each execution an isolated, hardware-backed environment, scoped identity,
  network controls, and ephemeral credentials.
- Preserve task state for work that pauses and resumes over hours or days.
- Keep sandbox inputs and outputs in the governed agent trace.

This avoids choosing between an over-permissioned shared runtime and a locked
down runtime that cannot complete useful work.

## Partner Relevance

Partners can design agent platforms, isolation policies, identity and egress
controls, evaluation systems, and scalable execution architectures for
regulated or multi-tenant workloads. Customer examples in the source illustrate
the pattern, but architecture and economics still require workload-specific
validation.
