---
title: Microsoft Fabric
type: entity
created: 2026-07-10
updated: 2026-07-10
tags:
  - microsoft-fabric
  - analytics
  - data-platform
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md
status: active
---

# Microsoft Fabric

Microsoft Fabric is the data and analytics platform targeted by the `skills-for-fabric` repository. The repo treats Fabric as a multi-workload environment spanning Lakehouse, Warehouse, SQL Database in Fabric, Dataflows Gen2, Eventhouse/KQL, Eventstreams, Activator, semantic models, Power BI reports, FabricIQ, and migration scenarios.

## Operating Patterns

- Use Azure authentication before Fabric operations.
- Use REST APIs for programmatic workspace and item management.
- Use protocol-specific access for workload data: Spark/PySpark, T-SQL, KQL, XMLA/DAX, or MCP-backed query workflows.
- Prefer [[medallion-architecture]] and incremental processing for data engineering.

## Related Pages

- [[skills-for-fabric]]
- [[agent-skill-common-architecture]]
- [[fabric-authoring-consumption-operations]]
- [[model-context-protocol-mcp]]
- [[power-bi]]
