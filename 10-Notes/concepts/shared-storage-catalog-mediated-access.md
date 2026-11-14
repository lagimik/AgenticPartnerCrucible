---
title: Shared Storage with Catalog-Mediated Access
type: concept
created: 2026-11-14
updated: 2026-11-14
tags: [data-governance, interoperability, storage, unity-catalog, access-control]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939
  - https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake
status: active
---

# Shared Storage with Catalog-Mediated Access

A common physical data location does not imply a common permission model or
universal client compatibility. Separate the storage identity, catalog
authorization, and consumer access path.

## OneLake and Unity Catalog Example

The [OneLake Databricks integration](../../40-Resources/onelake-native-storage-azure-databricks.md)
reserves the storage item's ReadWrite role for the approved Databricks identity.
Fabric workspace roles alone do not grant data access, and Fabric readers
use mirrored catalog items. Adding readers directly to the storage role permits
access outside Unity Catalog governance.

## Design Contract

**Interpretation:** Identify the authoritative catalog and prevent alternate
storage access paths from bypassing it. Review permission changes separately
for storage, event infrastructure, and readers. Validate consumer support for
table-state protocols and column types before claiming interoperability.

Catalog mirroring without a data copy does not establish that every workload
can read every object: the reviewed setup guide documents Fabric Spark
restrictions for catalog commits and omitted `FILE` columns.

## Related Pages

- [OneLake Native Storage Resource](../../40-Resources/onelake-native-storage-azure-databricks.md)
- [Azure Databricks](../entities/azure-databricks.md)
- [Microsoft Fabric](../entities/microsoft-fabric.md)
