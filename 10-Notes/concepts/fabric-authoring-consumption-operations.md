---
title: Fabric Authoring Consumption Operations
type: concept
created: 2026-07-10
updated: 2026-07-10
tags:
  - microsoft-fabric
  - operating-model
  - ai-skills
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-authoring/.github/plugin/plugin.json
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-consumption/.github/plugin/plugin.json
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-operations/.github/plugin/plugin.json
status: active
---

# Fabric Authoring Consumption Operations

`skills-for-fabric` separates Fabric work into three practical modes:

- **Authoring:** create, change, deploy, and manage Fabric items.
- **Consumption:** query, inspect, explore, and monitor without changing resources.
- **Operations:** diagnose performance, health, refreshes, jobs, and slow queries.

## Why It Matters

This separation gives an AI assistant safer defaults. Read-only exploration can be routed differently from write operations, and diagnostics can use specialized workflows without accidentally changing production artifacts.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
