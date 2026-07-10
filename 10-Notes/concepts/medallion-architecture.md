---
title: Medallion Architecture
type: concept
created: 2026-07-10
updated: 2026-07-10
tags:
  - data-engineering
  - lakehouse
  - microsoft-fabric
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/agents/FabricDataEngineer.agent.md
status: active
---

# Medallion Architecture

Medallion architecture organizes data into progressive quality layers: Bronze for raw data, Silver for cleaned and validated data, and Gold for analytics-ready data.

## In Skills for Fabric

`skills-for-fabric` treats medallion architecture as a preferred Fabric data engineering pattern, especially for Lakehouse and Spark workflows. `FabricDataEngineer` is responsible for orchestrating cross-workload medallion designs and delegating implementation details to specialized skills.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[agent-skill-common-architecture]]
