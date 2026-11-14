---
title: Azure Databricks
type: entity
created: 2026-11-14
updated: 2026-11-14
tags: [azure-databricks, analytics, unity-catalog, onelake]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939
  - https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake
status: active
---

# Azure Databricks

In the [OneLake storage integration](../../40-Resources/onelake-native-storage-azure-databricks.md),
Azure Databricks retains compute and Unity Catalog management while supported
managed objects use OneLake storage. The Databricks feature is Public Preview,
distinct from Fabric-side GA support.

## Integration Boundaries

Keep direct storage access reserved for the approved Databricks identity.
Fabric readers use mirrored catalogs, subject to object and client limitations:
Fabric Spark cannot read tables with catalog commits, `FILE` columns are omitted
in Fabric, and Databricks-to-Open sharing is unsupported for OneLake-backed
managed tables. File-event setup may require higher workspace permissions than
baseline storage integration.

## Related Pages

- [OneLake Native Storage](../../40-Resources/onelake-native-storage-azure-databricks.md)
- [Shared Storage with Catalog-Mediated Access](../concepts/shared-storage-catalog-mediated-access.md)
- [Microsoft Fabric](microsoft-fabric.md)
