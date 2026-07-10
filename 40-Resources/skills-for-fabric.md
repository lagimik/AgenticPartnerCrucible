---
title: Microsoft Skills for Fabric Repository
type: resource
created: 2026-07-10
updated: 2026-07-10
tags:
  - microsoft-fabric
  - ai-skills
  - github-copilot
  - power-bi
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/package.json
  - raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/CHANGELOG.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-skills/.github/plugin/plugin.json
status: active
---

# Microsoft Skills for Fabric Repository

[[microsoft]] maintains `microsoft/skills-for-fabric`, a MIT-licensed repository of reusable AI assistant instructions for working with [[microsoft-fabric]]. The repository is packaged for [[github-copilot-cli]] and compatible coding agents, with skills that help assistants understand Fabric workloads, APIs, query patterns, and operational best practices.

## Key Takeaways

1. The repository is a packaged skill system, not a single tutorial. It includes plugin bundles such as `fabric-skills`, `fabric-authoring`, `fabric-consumption`, `fabric-operations`, and `powerbi-authoring` for installing focused capability sets.
2. Its operating model is [[agent-skill-common-architecture]]: high-level Fabric agents delegate work to specialized skills, while shared common references keep workload patterns consistent.
3. The guidance is safety-oriented: it separates authoring from read-only consumption, requires Azure/Fabric authentication, favors REST APIs and [[model-context-protocol-mcp]] where appropriate, and emphasizes confirmation gates, parameterization, no hardcoded IDs or secrets, and workload-specific best practices.

## What It Covers

The repo covers Fabric workloads and adjacent Power BI workflows:

- Spark, Lakehouse, notebooks, and Materialized Lake Views.
- Warehouse and SQL Database in Fabric.
- Eventhouse, KQL, Eventstreams, Activator, and Real-Time Intelligence.
- Dataflows Gen2 authoring and consumption.
- [[power-bi]] semantic model consumption and authoring.
- Power BI report planning, design, authoring, and management.
- FabricIQ and Fabric IQ Ontology.
- Synapse, HDInsight, Databricks, and pipeline migrations.
- End-to-end [[medallion-architecture]] patterns.

## Installation Model

The root README recommends adding the public marketplace and installing bundles through GitHub Copilot CLI:

```text
/plugin marketplace add microsoft/skills-for-fabric
/plugin install fabric-skills@fabric-collection
```

Focused bundles can be installed for authoring, consumption, operations, or Power BI authoring. The repo also includes compatibility files for Claude Code, Cursor, Windsurf, Codex/Jules/OpenCode, and Gemini CLI.

## Notes for Shakespeare

This source is useful as a reference pattern for building a second-brain assistant because it demonstrates:

- Explicit routing from broad user intent to specialized skills.
- Procedural safety rules embedded near the tools that need them.
- Separation between immutable source/reference material, reusable instructions, and live tool access.
- Installable bundles that map to user personas and task modes.

## Citations

- Root purpose, installation, bundles, authentication, MCP note, compatibility files, and license: `raw/2026-07-10-github-microsoft-skills-for-fabric/README.md`.
- Package name, version, description, repository, keywords, author, license, and test scripts: `raw/2026-07-10-github-microsoft-skills-for-fabric/package.json`.
- Agent/skill/common architecture and workload routing: `raw/2026-07-10-github-microsoft-skills-for-fabric/AGENTS.md` and `raw/2026-07-10-github-microsoft-skills-for-fabric/CLAUDE.md`.
- Current release context and recently added SQL Database in Fabric skills: `raw/2026-07-10-github-microsoft-skills-for-fabric/CHANGELOG.md`.
- Full bundle packaging: `raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/fabric-skills/.github/plugin/plugin.json`.
