---
title: Microsoft Skills for Fabric Repository
type: resource
created: 2026-07-10
updated: 2026-11-27
tags:
  - microsoft-fabric
  - ai-skills
  - github-copilot
  - power-bi
sources:
  - raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/govern-your-microsoft-fabric-data-estate-from-one-place-with-the-onelake-catalog/5377369
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started
status: active
---

# Microsoft Skills for Fabric Repository

The preserved July 10 README describes `microsoft/skills-for-fabric` as a MIT-licensed repository of reusable AI assistant instructions for working with [[microsoft-fabric]]. It documents installation through [[github-copilot-cli]] and compatibility with other coding agents, with guidance on Fabric workloads, APIs, query patterns, and operational best practices.

## Key Takeaways

1. The repository is a packaged skill system, not a single tutorial. It includes plugin bundles such as `fabric-skills`, `fabric-authoring`, `fabric-consumption`, `fabric-operations`, and `powerbi-authoring` for installing focused capability sets.
2. The README separates authoring, read-only consumption, and diagnostics into focused bundles. [[agent-skill-common-architecture]] is a related design interpretation, not verified agent implementation behavior.
3. Most operations require Azure authentication and workload-specific endpoints or token audiences. Skills provide guidance; [[model-context-protocol-mcp]] servers provide live access where supported. Bundle labels alone do not enforce read-only permissions.

## What It Covers

The repo covers Fabric workloads and adjacent Power BI workflows:

- Spark, Lakehouse, and notebooks.
- Warehouse and SQL data warehouse workflows.
- Eventhouse, KQL, and Eventstreams.
- Dataflows Gen2 authoring and consumption.
- [[power-bi]] semantic model consumption and authoring.
- Power BI report planning, design, authoring, management, and PBIP workflows.
- Catalog search and migration scenarios.
- End-to-end [[medallion-architecture]] patterns.

## Installation Model

The captured README recommends adding the public marketplace and installing bundles through GitHub Copilot CLI:

```text
/plugin marketplace add microsoft/skills-for-fabric
/plugin install fabric-skills@fabric-collection
```

Focused bundles can be installed for authoring, consumption, operations, or Power BI authoring. The captured README excludes `powerbi-authoring` from the full bundle and shows it as a separate installation. It also lists compatibility files for Claude Code, Cursor, Windsurf, Codex/Jules/OpenCode, and Gemini CLI. Recheck current repository instructions before installing.

## November 2026 Additions

[Govern Skills](fabric-onelake-govern-and-skills.md) add Health, Protect, and
Trust procedures for evidence-led governance audits and reviewed remediation.
The OneLake catalog Govern experience is GA, but Policies Center remains
preview; skill installation does not confer administrative permissions.

[Project Osmos](fabric-project-osmos-data-engineering-agent.md) adds preview
Fabric-hosted tasks that plan, execute, and validate data engineering work.
Tasks continue beyond local client disconnection and consume model and Spark
resources. Eligible nontrial capacity, workspace permissions, required tenant
settings, explicit write boundaries, and human acceptance are prerequisites.

These are different motions: governance skills guide assessment and remediation;
Osmos runs persistent data engineering tasks, not ordinary report authoring.

## Notes for Shakespeare

This source is useful as a reference pattern for building a second-brain assistant because it demonstrates:

- Explicit routing from broad user intent to specialized skills.
- Procedural safety rules embedded near the tools that need them.
- Separation between immutable source/reference material, reusable instructions, and live tool access.
- Installable bundles that map to user personas and task modes.

## Evidence Boundaries

The July 10 HTML capture preserves the rendered README. Individual checkout
files cited by older notes were unavailable during the November 21 review;
the November 27 restoration below supplies historical evidence for those
files. Architectural recommendations remain interpretations, and current
installation, implementation, and permission enforcement require separate
verification.

### Capture Provenance

The missing cited files were restored on 2026-11-27 from the original
`microsoft/skills-for-fabric` submodule revision `b961296e97a89a39e81e10501c2ef846ad0c54db`.
Their Git blob hashes were verified against that revision; existing raw
files were not overwritten. This restores historical evidence, not a
revalidation of the repository's current release or installation behavior.
The existing pinned submodule is registered in `.gitmodules` so a fresh clone
can retrieve it with `git submodule update --init -- raw/2026-07-10-github-microsoft-skills-for-fabric`.
Do not run an updating checkout over locally modified raw material.

## Citations

- Preserved repository README: `raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/content.html`.
- Capture provenance: `raw/2026-07-10-ingestlinks/023-github-com-microsoft-skills-for-fabric/metadata.json`.
- Later governance and engineering additions: the public sources linked from [OneLake Govern and Skills](fabric-onelake-govern-and-skills.md) and [Project Osmos](fabric-project-osmos-data-engineering-agent.md).
