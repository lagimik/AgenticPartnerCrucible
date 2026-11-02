---
title: Fabric Assessment Tool for Migration Discovery
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-fabric, migration, synapse, databricks, assessment]
sources:
  - https://github.com/microsoft/fabric-toolbox/tree/main/tools/fabric-assessment-tool
  - https://github.com/microsoft/fabric-toolbox/blob/main/tools/fabric-assessment-tool/README.md
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Fabric Assessment Tool for Migration Discovery

The [Fabric Toolbox assessment tool](https://github.com/microsoft/fabric-toolbox/tree/main/tools/fabric-assessment-tool)
inventories source-platform assets for Fabric data engineering and warehouse
migration planning. The reviewed README supports Synapse and Databricks;
inventory and visualization are not automated migration or compatibility proof.

## Source Summary

- `fat assess` exports workspace and resource metadata into structured JSON.
- `fat visualize` turns collected results into offline HTML views for
  administration, data engineering, warehousing, and integration.
- The reviewed requirements list Python 3.10-3.12 and pip, with Azure CLI or
  Fabric Notebook authentication; Notebook authentication requires an explicit
  subscription ID.
- Notebook extraction is metadata-first unless source download is requested.
  Logs are written only when the optional log-file argument is configured.

## Delivery Boundaries

Permissions determine what the assessment can see. The README warns that some
Databricks resources can return empty results without sufficient access; an
empty inventory is not proof that no assets exist. Review incomplete and failed
workspace counts and reconcile the inventory with platform owners.

Dedicated SQL pool statistics have separate authentication and permissions.
Optional `--create-dmv` can create the `vTableSizes` view: approve that schema
change separately rather than describing every assessment as read-only.
Treat exported metadata and optional notebook source as customer-controlled
material; do not publish assessment results.

**Partner interpretation:** use discovery evidence to scope migration waves,
dependencies, and follow-up validation; do not infer production readiness from
successful extraction alone. No assessment was run during this ingest.

## Related

- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Direct Lake design](fabric-direct-lake-design.md)
- [Medallion architecture guidance](fabric-data-warehouse-medallion-series.md)
