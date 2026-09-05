---
title: Medallion Architecture
type: concept
created: 2026-07-10
updated: 2026-09-05
tags:
  - data-engineering
  - lakehouse
  - microsoft-fabric
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/agents/FabricDataEngineer.agent.md
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Medallion Architecture

Medallion architecture organizes data into progressive quality layers: Bronze for raw data, Silver for cleaned and validated data, and Gold for analytics-ready data.

## In Skills for Fabric

`skills-for-fabric` treats medallion architecture as a preferred Fabric data engineering pattern, especially for Lakehouse and Spark workflows. `FabricDataEngineer` is responsible for orchestrating cross-workload medallion designs and delegating implementation details to specialized skills.

## Layer Contracts

- **Bronze preserves source fidelity.** Keep data append-oriented and replayable; capture source metadata and avoid business transformations.
- **Silver establishes correctness.** Clean, type, deduplicate, standardize, and conform data into reusable domain structures.
- **Gold serves consumption.** Build dimensional, aggregated, or denormalized models tuned for reporting, semantic models, and business access.

## Fabric Pattern Selection

The layers are logical responsibilities, not a mandate to use one Fabric workload everywhere. A lakehouse-only design suits Spark and Delta-centric teams; a hybrid design can use Lakehouse for Bronze and Silver and Fabric Warehouse for SQL-oriented Gold consumption. Choose from team skills, workload access patterns, operational ownership, and performance requirements.

Use incremental processing, partitioning, lineage, environment isolation, and table maintenance across the pipeline. Do not mix layer responsibilities merely to reduce the number of workspaces or artifacts.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[agent-skill-common-architecture]]
- [[fabric-data-warehouse-medallion-series]]
