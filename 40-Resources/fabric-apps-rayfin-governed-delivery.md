---
title: Governed Fabric Apps Delivery with Rayfin
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [fabric-apps, rayfin, application-development, authorization, governance]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/build-governed-data-apps-with-microsoft-fabric-apps-generally-available/5423011
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - https://learn.microsoft.com/en-us/fabric/apps/overview
  - https://learn.microsoft.com/en-us/fabric/apps/data-permissions
  - https://learn.microsoft.com/en-us/fabric/apps/connectors
  - https://learn.microsoft.com/en-us/fabric/apps/pricing
  - raw/2026-11-20-iq-foundry-onelake-finops/sources.md
status: active
---

# Governed Fabric Apps Delivery with Rayfin

## Source Summary

The November 17 [dedicated announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/build-governed-data-apps-with-microsoft-fabric-apps-generally-available/5423011)
announces **Rayfin and Fabric Apps GA**, with **Fabric HorizonDB separately
preview**. Its complete publisher RSS description was reviewed after HTTP 403.
TypeScript defines data, permissions, functions, and APIs in the app project;
Rayfin deploys frontend and backend into Fabric.
The platform supplies app inventory, CSP, secure embedding, and item governance.
The Microsoft IQ roundup's preview wording differs; use capability-specific
evidence and verify customer availability.

## Authorization Is Layered

The reviewed [overview](https://learn.microsoft.com/en-us/fabric/apps/overview),
[permission guide](https://learn.microsoft.com/en-us/fabric/apps/data-permissions),
and [connector guide](https://learn.microsoft.com/en-us/fabric/apps/connectors)
require separate checks for:

| Layer | Delivery consequence |
| --- | --- |
| App item access | Run/interact, editing, and sharing are distinct permissions. |
| Entity access | Explicit action, row, and field policies govern API exposure. |
| SQL source identity | Documented default is application authentication; delegated access must be chosen explicitly. |
| Semantic models | Delegated only; callers need applicable model permissions, including Build. |
| Static hosting and data | Anonymous options exist; Entra sign-in is not blanket protection for all content. |

**Identity discrepancy:** The announcement says apps use their own identity,
not the deployer's permissions. The connector guide instead describes the
current SQL application identity as the app item owner. Do not infer
deployer-independent least privilege from the announcement; inspect the actual
runtime identity, source grants, and authentication mode.
Schema discovery under developer credentials does not prove deployed access.

Lakehouse SQL connectors are read-only; warehouse and SQL database connectors
support selected writes; semantic models support queries, not writeback.
Client-side types are not an authorization boundary. Keep secrets server-side
and test both permitted and denied requests.

## Capacity and Production Boundaries

[Pricing](https://learn.microsoft.com/en-us/fabric/apps/pricing) separates
capacity-backed apps from the Power BI Pro experience. Capacity-backed
operations consume workspace capacity and associated storage/operation meters;
Pro licensing and limits are a different path, not free unlimited capacity.
Tenant administrators must enable the workload.

Local development is not necessarily offline: the overview says file storage
uses Fabric in development and deployment. Production sign-in uses Fabric SSO;
applications needing other identity providers or complex transactions require
fit assessment. Customers retain responsibility for exposed data, secrets,
permissions, and legal/compliance obligations.

## Partner Application

**Interpretation:** Deliver a bounded governed-data-app pilot from an existing
semantic model or approved data source. Review the generated project, schema
changes, runtime identities, row/field policies, anonymous settings, capacity,
observability, and recovery before deployment. No app was built or deployed.

## Related

- [Fabric Apps](../10-Notes/entities/fabric-apps.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [OneLake Data and Governance](onelake-data-context-governance.md)
- [Shared Storage Access Contract](../10-Notes/concepts/shared-storage-catalog-mediated-access.md)
