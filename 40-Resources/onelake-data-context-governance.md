---
title: OneLake Data, Context, and Governance
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [onelake, governance, interoperability, iceberg, fabric-iq]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/onelake-the-unified-foundation-for-data-context-governance-and-ai/5423035
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - https://learn.microsoft.com/en-us/fabric/onelake/table-apis/iceberg-table-apis-overview
  - https://learn.microsoft.com/en-us/fabric/onelake/table-apis/table-apis-overview
  - raw/2026-11-20-iq-foundry-onelake-finops/sources.md
status: active
---

# OneLake Data, Context, and Governance

## Source Summary

The November 17 [OneLake announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/onelake-the-unified-foundation-for-data-context-governance-and-ai/5423035)
was reviewed through its **complete publisher RSS description** after the article
returned HTTP 403. It positions OneLake catalog as Microsoft's lake-first
data-governance product, covering native and connected data.

This is explicitly **not a feature-for-feature replacement** for Purview Data
Governance. Purview data security and compliance continue. Atlan is announced
as a complementary partner for broader-estate governance and metadata transition
tooling; tool coverage and lossless migration were not verified.
The separate [transition resource](microsoft-data-governance-fabric-transition.md)
retains the sourced November 12, 2027 support-end date.

## Capability Boundaries

| Capability | Publisher status |
| --- | --- |
| Catalog federation via supported catalogs | GA; supported paths avoid data movement, not all source types or operations. |
| Iceberg Table API read/write with credential vending | GA; native-table and client compatibility requirements apply. |
| IQ Sharing including Fabric IQ ontologies | Preview. |
| OneLake knowledge sources and security integration with Foundry IQ | Preview. |
| Semantic views using open YAML business definitions | Preview. |
| Salesforce Data 360 shortcuts | Preview. |
| Further data quality, glossary, lineage, and policy work | Forward-looking investment, not delivered scope. |

The roundup labels Databricks native storage GA, but does not establish removal
of the Databricks-side preview and reader restrictions in the
[previously reviewed setup guide](onelake-native-storage-azure-databricks.md).
Keep engine-specific status separate.

## Implementation Evidence

[Iceberg API documentation](https://learn.microsoft.com/en-us/fabric/onelake/table-apis/iceberg-table-apis-overview)
permits native Iceberg writes through storage writes plus catalog commits with
concurrency checks. Virtual Iceberg metadata over Delta is for reading; update
Delta through a Delta-compatible writer. Commits through table shortcuts are
unsupported. Vended credentials require compatible clients and correct
storage-prefix matching.

The [Table API overview](https://learn.microsoft.com/en-us/fabric/onelake/table-apis/table-apis-overview)
separates catalog metadata from **preview secured row reads** and requires
operation-specific permissions. Credential vending is not evidence that every
external engine enforces every Fabric row/column policy identically.

## Partner Application

**Interpretation:** Assess governance requirements and source coverage before
mapping catalog, federation, sharing, or third-party tools. Pilot exact
table formats, read/write paths, identity boundaries, lineage, and semantic
definitions; preserve ongoing Purview protection. No data movement, catalog
change, or governance migration was performed.

## Related

- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Shared Storage with Catalog-Mediated Access](../10-Notes/concepts/shared-storage-catalog-mediated-access.md)
- [Reusable Enterprise Context](../10-Notes/concepts/reusable-enterprise-context.md)
- [OneLake Govern and Skills](fabric-onelake-govern-and-skills.md)
- [Governed Fabric Apps](fabric-apps-rayfin-governed-delivery.md)
