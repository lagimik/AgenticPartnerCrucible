---
title: Medallion Architecture
type: concept
created: 2026-07-10
updated: 2026-11-21
tags:
  - data-engineering
  - lakehouse
  - microsoft-fabric
sources:
  - raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Medallion Architecture

Medallion architecture organizes data into progressive quality layers: Bronze for raw data, Silver for cleaned and validated data, and Gold for analytics-ready data.

## In Skills for Fabric

The preserved `skills-for-fabric` README includes medallion architecture workflows and a NYC taxi medallion example. It does not establish a preferred pattern for every workload or verify a specific agent's orchestration responsibilities.

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
