---
title: The next chapter for CI/CD in Fabric Warehouse (Preview) - source capture
source_url: https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/the-next-chapter-for-cicd-in-fabric-warehouse-preview/5401222
retrieved_item_url: https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/The-next-chapter-for-CI-CD-in-Fabric-Warehouse-Preview/ba-p/5401222
retrieved_from: https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
publisher: Microsoft Fabric Community
published: 2026-11-11
captured: 2026-11-14
capture_type: publisher-rss-source-summary
---

# Source Capture

Both the supplied article URL and the RSS item URL returned HTTP 403.
The publisher's configured RSS feed supplied the complete matching item,
including its title, November 11 publication timestamp, body, and documentation
links. This capture preserves a paraphrased summary rather than reproducing the
article. No author attribution was available in the reviewed item metadata.

## Source Summary

The preview-titled article describes Fabric Warehouse releases as state-aware
database deployments rather than copies of artifacts. SQL database projects
provide the versioned definition, while DacFx compares source and target schemas
and generates incremental changes through Git integration and deployment
pipelines.

The article places the following under delivered capabilities:

- Git-based SQL project development and incremental deployment pipelines.
- Shared SQL queries designated as pre- or post-deployment scripts, retained
  in the SQL project and versioned with the Warehouse.
- Item Definition APIs for creating, retrieving, and updating Warehouse
  definitions using SQL project or DACPAC formats.
- SQL database project support in SSMS and Schema Compare in VS Code.

The announced next investments are environment-specific deployment
configurations for data, objects, and errors; Warehouse support in the
`fabric-cicd` package; and Git/pipeline CI/CD for SQL analytics endpoints.
The source does not provide delivery dates for those investments.

## Evidence Boundaries

The overall article is labeled Preview; its delivered-versus-planned structure
does not establish GA for every individual capability. Linked documentation was
not independently reviewed during ingestion. Permissions, supported object
types, data effects, tool versions, and rollback behavior require separate
verification before production adoption.

## Source-Linked Documentation

- https://learn.microsoft.com/fabric/data-warehouse/git-integration
- https://learn.microsoft.com/fabric/data-warehouse/deploy-pipelines
- https://learn.microsoft.com/fabric/data-warehouse/deployment-scripts
- https://learn.microsoft.com/rest/api/fabric/warehouse/items
