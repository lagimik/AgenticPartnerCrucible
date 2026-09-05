---
title: Microsoft Fabric CI/CD Resources
type: resource
created: 2026-09-05
updated: 2026-09-05
tags: [microsoft-fabric, cicd, git, deployment-automation]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/new-cicd-resources-for-microsoft-fabric-from-concepts-to-end-to-end-automation/5358502
  - raw/2026-09-05-github-open-issues-72-85/issues.md
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

- [[agent-cicd]]
- [[microsoft-fabric]]
- [[skills-for-fabric]]
