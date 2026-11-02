---
title: Microsoft Fabric
type: entity
created: 2026-07-10
updated: 2026-11-02
tags:
  - microsoft-fabric
  - analytics
  - data-platform
sources:
  - https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-overview
  - https://learn.microsoft.com/en-us/fabric/enterprise/capacity-overage-overview
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/govern-your-microsoft-fabric-data-estate-from-one-place-with-the-onelake-catalog/5377369
  - https://github.com/microsoft/microsoft-iq-solution-accelerator
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

- [Assessment tool](../../40-Resources/fabric-assessment-tool.md) - Source-estate discovery for migration planning, not automatic migration.
- [Direct Lake design](../../40-Resources/fabric-direct-lake-design.md) - OneLake versus SQL access, fallback, framing, and capacity boundaries.
- [Capacity operations](../../40-Resources/fabric-capacity-observability-and-protection.md) - Admission controls, paid overage, and real-time evidence.
- [OneLake Govern and Skills](../../40-Resources/fabric-onelake-govern-and-skills.md) - GA governance surface and evidence-led remediation, with nested preview limits.
- [Project Osmos](../../40-Resources/fabric-project-osmos-data-engineering-agent.md) - Preview persistent Spark execution and validation, with nontrial-capacity and permission requirements.
- [Microsoft IQ Solution Accelerator](../../40-Resources/microsoft-iq-solution-accelerator.md) - Fabric ontology and data in a cross-IQ supply-chain demonstration with preview dependencies.
- [[skills-for-fabric]]
- [[agent-skill-common-architecture]]
- [[fabric-authoring-consumption-operations]]
- [[model-context-protocol-mcp]]
- [[power-bi]]
