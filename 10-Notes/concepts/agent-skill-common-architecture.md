---
title: Agent Skill Common Architecture
type: concept
created: 2026-07-10
updated: 2026-11-28
tags:
  - agents
  - ai-skills
  - architecture
sources:
  - raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html
status: active
---

# Agent Skill Common Architecture

Agent Skill Common Architecture is a reusable design pattern: agents orchestrate broad user intent, skills provide endpoint-specific procedures, and common references centralize reusable implementation guidance. This is an architectural interpretation, not a verified description of individual `skills-for-fabric` agent files.

## Pattern

- **Agents:** route and coordinate cross-workload tasks.
- **Skills:** execute focused workload operations.
- **Common:** hold shared CLI, API, query, and implementation guidance.

## Example

A data engineering agent can route Spark, Warehouse, Eventhouse, Dataflows, semantic model, and migration work to focused procedures. The preserved Fabric README documents these skill areas, but does not establish a particular agent's delegation behavior.

## Evidence Boundary

The retained README supports reusable skills and workload bundles. Individual
agent and common-reference files were unavailable during the November 21 review
and were restored at the historical pinned revision on November 27; see the
[repository evidence notes](../../40-Resources/skills-for-fabric.md#evidence-boundaries).
That restoration does not verify current delegation behavior.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
