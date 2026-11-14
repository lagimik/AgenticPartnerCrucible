---
title: Fabric Warehouse CI/CD Preview Lifecycle
type: resource
created: 2026-11-14
updated: 2026-11-14
tags: [microsoft-fabric, warehouse, cicd, dacfx, preview]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/the-next-chapter-for-cicd-in-fabric-warehouse-preview/5401222
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - raw/2026-11-14-fabric-warehouse-cicd/source.md
status: active
---

# Fabric Warehouse CI/CD Preview Lifecycle

## Source Summary

The November 11, 2026 [Fabric Community article](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/the-next-chapter-for-cicd-in-fabric-warehouse-preview/5401222)
describes a common SQL project and DacFx foundation spanning Git, deployment
pipelines, release scripts, APIs, and client tools. The full publisher RSS item
was reviewed because both article URL forms returned HTTP 403.

The central distinction is **database deployment, not artifact copying**:
DacFx compares schema states and determines incremental changes for the target.

## Capabilities Described as Delivered

| Capability | Delivery implication |
| --- | --- |
| Git integration and deployment pipelines | Version Warehouse schemas as SQL database projects and promote incremental changes across environments. |
| Pre- and post-deployment scripts | Designate shared SQL queries as release scripts that travel with the project through Git. |
| Warehouse Item Definition APIs | Create, retrieve, and update definitions programmatically using SQL project or DACPAC formats. |
| SSMS projects and VS Code Schema Compare | Use familiar client tooling on the same SQL project and DacFx foundation. |

The source's lifecycle is:

```text
Develop -> Version in Git -> Review -> Deploy -> Validate -> Promote
Deployment: pre-deployment actions -> DacFx schema changes -> post-deployment actions
```

## Planned, Not Established as Available

The article identifies three next investments without delivery dates:

- Deployment configurations controlling data, object, and error handling by
  environment.
- Warehouse support in the `fabric-cicd` package for source-driven automation
  alongside other Fabric items.
- SQL analytics endpoint Git integration and deployment pipelines using the
  shared SQL project foundation.

Do not infer that existing general Fabric automation already supports these
Warehouse or endpoint-specific plans.

## Partner Application

**Interpretation:** Build a Warehouse ALM assessment or implementation accelerator
around isolated development, versioned SQL projects, reviewed schema changes,
release scripts, API orchestration, and post-deployment checks. Explicitly
test data effects, script repeatability, dependencies, permissions, and recovery
in customer-like environments rather than treating a successful artifact
promotion as proof of application correctness.

## Boundaries and References

The source is labeled Preview; delivered does not imply universal GA.
Linked [Git](https://learn.microsoft.com/fabric/data-warehouse/git-integration),
[pipelines](https://learn.microsoft.com/fabric/data-warehouse/deploy-pipelines),
[scripts](https://learn.microsoft.com/fabric/data-warehouse/deployment-scripts),
and [API documentation](https://learn.microsoft.com/rest/api/fabric/warehouse/items)
were not independently reviewed. Verify supported objects, client versions,
permissions, deployment data effects, and recovery behavior before production
use; the article does not establish automatic rollback or lossless deployment.

## Related Pages

- [State-Aware Warehouse Deployment](../10-Notes/concepts/state-aware-warehouse-deployment.md)
- [Fabric CI/CD Resources](fabric-cicd-resources.md)
- [Agent CI/CD](../10-Notes/concepts/agent-cicd.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Preserved RSS Source Summary](../raw/2026-11-14-fabric-warehouse-cicd/source.md)
