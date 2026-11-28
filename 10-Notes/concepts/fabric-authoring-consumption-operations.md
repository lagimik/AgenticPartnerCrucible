---
title: Fabric Authoring Consumption Operations
type: concept
created: 2026-07-10
updated: 2026-11-28
tags:
  - microsoft-fabric
  - operating-model
  - ai-skills
sources:
  - raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html
status: active
---

# Fabric Authoring Consumption Operations

The preserved July 10 `skills-for-fabric` README describes three practical bundle modes:

- **Authoring:** create, change, deploy, and manage Fabric items.
- **Consumption:** query, inspect, explore, and monitor without changing resources.
- **Operations:** diagnose performance, health, refreshes, jobs, and slow queries.

## Why It Matters

This separation gives an AI assistant safer defaults. Read-only exploration can be routed differently from write operations, and diagnostics can use specialized workflows without accidentally changing production artifacts.

Bundle descriptions express intended use, not an enforced permission boundary.
Historical plugin manifests were restored at the pinned revision on November 27;
see the [capture provenance](../../40-Resources/skills-for-fabric.md#capture-provenance).
Verify installed tools and resource permissions before relying on read-only behavior.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
