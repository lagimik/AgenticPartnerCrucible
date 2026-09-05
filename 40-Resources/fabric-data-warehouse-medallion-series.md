---
title: Fabric Data Warehouse Medallion Architecture Series
type: resource
created: 2026-09-05
updated: 2026-09-05
tags: [microsoft-fabric, data-warehouse, medallion-architecture, onelake]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/choosing-your-medallion-pattern-in-fabric-data-warehouse/5328670
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/building-the-bronze-%E2%86%92-silver-%E2%86%92-gold-layers/5360201
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/fabric-data-warehouse-best-practices-for-medallion-architectures/5364080
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Fabric Data Warehouse Medallion Architecture Series

Three-part Fabric Community series covering pattern selection, layer construction, and operational best practices for medallion architectures in Fabric.

## Layer Responsibilities

- **Bronze:** immutable, append-oriented source fidelity for audit and replay.
- **Silver:** cleaned, typed, deduplicated, conformed data with resolved business keys.
- **Gold:** business-ready dimensional or aggregated models optimized for analytics and Power BI.

Fabric supports lakehouse-only designs or hybrid patterns such as Lakehouse for Bronze and Silver with Warehouse for Gold. Choose according to team skills, SQL and Spark preferences, and consumption patterns rather than forcing one storage experience across every layer.

Incremental processing, partitioning, lineage, clear ownership, environment separation, and Delta-table maintenance preserve scalability and auditability.

## Related Pages

- [[medallion-architecture]]
- [[microsoft-fabric]]
- [[skills-for-fabric]]
