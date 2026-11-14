---
title: Microsoft Fabric CI/CD Resources
type: resource
created: 2026-09-05
updated: 2026-11-14
tags: [microsoft-fabric, cicd, git, deployment-automation]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/new-cicd-resources-for-microsoft-fabric-from-concepts-to-end-to-end-automation/5358502
  - raw/2026-09-05-github-open-issues-72-85/issues.md
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/the-next-chapter-for-cicd-in-fabric-warehouse-preview/5401222
status: active
---

# Microsoft Fabric CI/CD Resources

Fabric Community guide that connects CI/CD concepts to end-to-end automation across Git integration, deployment pipelines, REST APIs, Fabric CLI, and infrastructure as code.

## Delivery Model

```text
Git branch -> pull request and validation -> artifact deployment
           -> environment configuration -> post-deployment verification
```

Use separate workspaces for development, test, and production; parameterize environment-specific values; treat Fabric item definitions as versioned artifacts; and automate promotion and verification. Bulk export/import APIs and command-line tooling support code-driven deployments, recovery, and enterprise release controls.

## Related Pages

- [Warehouse CI/CD Preview Lifecycle](fabric-warehouse-cicd-preview.md) - SQL projects, DacFx, scripts, and definition APIs; Warehouse `fabric-cicd` support and endpoint CI/CD are described as future investments.
- [State-Aware Warehouse Deployment](../10-Notes/concepts/state-aware-warehouse-deployment.md)
- [[agent-cicd]]
- [[microsoft-fabric]]
- [[skills-for-fabric]]
