---
title: Agent Skill Common Architecture
type: concept
created: 2026-07-10
updated: 2026-07-10
tags:
  - agents
  - ai-skills
  - architecture
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/agents/FabricDataEngineer.agent.md
status: active
---

# Agent Skill Common Architecture

Agent Skill Common Architecture is the pattern used by `skills-for-fabric`: agents orchestrate broad user intent, skills provide endpoint-specific procedures, and common references centralize reusable implementation guidance.

## Pattern

- **Agents:** route and coordinate cross-workload tasks.
- **Skills:** execute focused workload operations.
- **Common:** hold shared CLI, API, query, and implementation guidance.

## Example

`FabricDataEngineer` handles cross-workload data engineering requests, then delegates Spark, SQL DW, Eventhouse, Dataflows, semantic model, MLV, and migration details to specialized skills.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[ai-assistant-skills]]
