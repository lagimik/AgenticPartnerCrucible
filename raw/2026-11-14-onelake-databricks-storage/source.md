---
title: OneLake native storage for Azure Databricks - source capture
source_url: https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/use-onelake-as-native-storage-for-azure-databricks/5377939
retrieved_from: https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
documentation_url: https://learn.microsoft.com/en-us/azure/databricks/connect/unity-catalog/cloud-storage/external-locations-onelake
publisher: Microsoft Fabric Community
published: 2026-11-13
captured: 2026-11-14
capture_type: publisher-rss-and-documentation-summary
---

# Source Capture

The supplied article URL returned HTTP 403. The publisher RSS feed provided
the complete matching item, ID 5377939, dated November 13. Its linked Microsoft
Learn setup guide, also dated November 13, was independently retrieved.
This capture preserves paraphrased summaries, not full-text reproductions.
No article author attribution was available in the reviewed RSS metadata.

## Announcement Summary

OneLake external-location support for Azure Databricks Unity Catalog is
generally available on the Fabric side and remains preview on the Databricks
side. Supported Unity Catalog objects can use OneLake as physical storage.
Databricks retains compute and Unity Catalog management; Fabric supplies a
capacity-backed workspace and Azure Databricks Storage item.

Storage items are locked by default through OneLake security. Workspace roles
do not themselves grant data access. Only the approved Databricks identity
should belong to the storage item's ReadWrite security role. Fabric readers
use a mirrored Azure Databricks catalog item rather than direct storage access.
The announcement describes catalog mirroring as exposing selected metadata
without copying underlying data.

## Setup Guide Evidence

The reviewed guide explicitly labels the Databricks feature Public Preview.
It requires Unity Catalog, serverless compute or Databricks Runtime 18.1+,
storage-credential and external-location creation privileges, active Fabric
capacity, tenant permission to create Databricks Storage items, and the
workspace's OneLake user-delegated SAS setting.

Baseline workspace access for the approved managed identity or service
principal is Viewer, plus sole membership in a ReadWrite OneLake role on the
storage item. The external location uses workspace and item GUIDs in its ABFSS
path; display-name paths are rejected.

File events are enabled by default for new external locations. Automatic
eventstream management needs Contributor or higher on the workspace;
a provided eventstream requires Member or higher on its workspace.

## Limitations and Source Differences

- Fabric Spark cannot read mirrored tables with catalog commits; those commits
  are enabled by default for managed tables in new catalogs/schemas through
  automatic upgrades. Disabling them also disables dependent table features.
- Databricks-to-Open sharing is unsupported for managed tables stored in
  OneLake.
- Fabric omits `FILE` columns from mirrored catalogs.
- The announcement's security section mentions only the access connector
  managed identity, while its setup overview and the guide also allow the
  approved service principal as the sole storage-role member.
- The announcement broadly lists notebooks as readers; the guide narrows that
  claim with the catalog-commit restriction.

These are implementation boundaries, not evidence of universal interoperability,
zero cost, or automatic migration. No resources or permissions were changed.
