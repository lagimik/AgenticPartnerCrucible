---
title: Agent CI/CD
type: concept
created: 2026-07-10
updated: 2026-09-05
tags:
  - agents
  - devops
sources:
  - raw/2026-07-10-ingestlinks/
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Agent CI/CD

Agent CI/CD is the practice of treating agent prompts, skills, configuration, evaluations, and deployment assets as lifecycle-managed software artifacts.

The same operating model applies to analytics platforms: definitions belong in source control, changes flow through pull requests and automated validation, environment values remain parameterized, and deployment includes post-release verification.

## Fabric Implementation

Microsoft Fabric combines Git integration, deployment pipelines, REST APIs, Fabric CLI, and infrastructure as code. Separate development, test, and production workspaces; version item definitions; automate promotion; and make rollback and recovery part of the release design.

## Related

- [[moc-ingested-link-library]]
- [[fabric-cicd-resources]]
- [[microsoft-fabric]]
