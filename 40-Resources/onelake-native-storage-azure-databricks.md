---
title: OneLake Native Storage for Azure Databricks
type: resource
created: 2026-11-14
updated: 2026-11-14
tags: [onelake, azure-databricks, unity-catalog, governance, interoperability]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake
  - raw/2026-11-14-onelake-databricks-storage/source.md
status: active
---

# OneLake Native Storage for Azure Databricks

## Source Summary

The November 13 [Fabric announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939)
states that OneLake external-location support is **GA in Fabric**, while the
[reviewed Databricks setup guide](https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake)
labels the Databricks capability **Public Preview**. The complete announcement
was reviewed through publisher RSS after its article URL returned HTTP 403.

Supported Unity Catalog-managed data can be written directly into OneLake:
Databricks supplies compute and catalog management, Fabric supplies the
capacity-backed workspace/storage item, and OneLake supplies physical storage.
This is not the same as read-only federation over existing OneLake data.

## Identity and Reader Boundaries

OneLake security is enabled by default on Azure Databricks Storage items.
Fabric workspace roles alone do not grant access to their data.
Give the approved Databricks managed identity or service principal baseline
Viewer access to the workspace and make it the **only member** of the storage
item's ReadWrite OneLake role.

Do not add Fabric readers, groups, or other identities to that role:
direct storage access bypasses Unity Catalog governance. Fabric readers use
a mirrored Azure Databricks catalog item, created through Databricks
Publish to Fabric or Fabric catalog mirroring. The announcement describes this
as metadata exposure without copying underlying data, not unrestricted access
to every object or feature.

## Deployment Prerequisites

The setup guide requires Unity Catalog, serverless compute or Databricks Runtime
18.1+, appropriate credential/location creation privileges, and active Fabric
capacity. Enable the tenant setting for creating Azure Databricks Storage items
and the workspace setting for OneLake user-delegated SAS tokens.

The external location must use GUID-based workspace/item paths:

```text
abfss://<WorkspaceID>@onelake.dfs.fabric.microsoft.com/<DatabricksStorageID>/Files/
```

Configure a Unity Catalog storage credential and external location, then use
it as catalog or schema managed storage. Display-name paths are rejected.

**File-event exception:** New external locations enable file events by default.
Automatic eventstream management requires Contributor or higher on the Fabric
workspace; provided eventstreams require Member or higher on their workspace.
Do not assume the baseline Viewer role suffices for event setup, or that higher
workspace roles authorize direct storage readers.

## Compatibility and Evidence Boundaries

| Boundary | Implementation consequence |
| --- | --- |
| Fabric Spark cannot read tables with catalog commits through mirrored catalogs | Test notebooks and Spark jobs; the guide says commits are enabled by default in new catalogs/schemas through automatic upgrades. |
| Disabling catalog commits disables dependent features | Treat the documented workaround as an explicit design tradeoff, not a harmless default change. |
| Databricks-to-Open sharing unsupported for OneLake-backed managed tables | Assess external sharing separately. |
| Fabric omits `FILE` columns | Validate consumer schema completeness and file-access requirements. |

The announcement's broad notebook-read claim is qualified by the guide's
Spark restriction. Its security section names only the managed identity,
while the guide and announcement setup overview also allow the approved service
principal; preserve single-identity access regardless of that choice.

## Partner Application

**Interpretation:** Scope an interoperability pilot around duplicate-data
reduction, catalog ownership, sole-identity storage access, mirrored consumer
paths, file-event permissions, and workload-specific compatibility tests.
Do not infer automatic migration, zero-copy support for all scenarios,
performance improvements, or customer savings from shared storage alone.
No deployment, permission change, or table-feature change was performed.

## Related Pages

- [Shared Storage with Catalog-Mediated Access](../10-Notes/concepts/shared-storage-catalog-mediated-access.md)
- [Azure Databricks](../10-Notes/entities/azure-databricks.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [OneLake Govern and Skills](fabric-onelake-govern-and-skills.md)
- [Preserved Source Summary](../raw/2026-11-14-onelake-databricks-storage/source.md)
