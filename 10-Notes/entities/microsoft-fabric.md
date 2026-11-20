---
title: Microsoft Fabric
type: entity
created: 2026-07-10
updated: 2026-11-20
tags:
  - microsoft-fabric
  - analytics
  - data-platform
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/bringing-trusted-fabric-iq-context-to-wherever-people-and-agents-work/5423049
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/onelake-the-unified-foundation-for-data-context-governance-and-ai/5423035
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/build-governed-data-apps-with-microsoft-fabric-apps-generally-available/5423011
  - https://techcommunity.microsoft.com/blog/microsoft-security-blog/a-next-step-in-the-evolution-of-the-microsoft-data-governance-strategy/4572227
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939
  - https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/the-next-chapter-for-cicd-in-fabric-warehouse-preview/5401222
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

- [Fabric IQ](fabric-iq.md) - Business-context layers and separately scoped GA, Beta, preview, and coming-soon consumers.
- [OneLake Data, Context, and Governance](../../40-Resources/onelake-data-context-governance.md) - Lake-first governance, Atlan complement, native Iceberg writes, and separately preview sharing/context features.
- [Fabric Apps](fabric-apps.md) - Dedicated GA announcement with source-identity, authorization, anonymous-access, and capacity boundaries.
- [Microsoft IQ](microsoft-iq.md) - Enterprise-context platform, distinct from the demonstration accelerator.
- [Microsoft Data Governance Transition](../../40-Resources/microsoft-data-governance-fabric-transition.md) - Fabric governance strategy and Purview Data Governance support-end announcement, with security/compliance and transition-gap boundaries.
- [OneLake native storage for Databricks](../../40-Resources/onelake-native-storage-azure-databricks.md) - Fabric-side GA, Databricks preview, sole-identity storage access, and catalog-commit/Spark limits.
- [Warehouse CI/CD Preview](../../40-Resources/fabric-warehouse-cicd-preview.md) - State-aware SQL project deployment, release scripts, and APIs, with explicit delivered-versus-planned boundaries.
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
