---
title: Power BI
type: entity
created: 2026-07-10
updated: 2026-07-10
tags:
  - power-bi
  - business-intelligence
  - microsoft-fabric
sources:
  - raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/agents/FabricIQ.agent.md
  - raw/2026-07-10-github-microsoft-skills-for-fabric/plugins/powerbi-authoring/.github/plugin/plugin.json
status: active
---

# Power BI

Power BI appears in `skills-for-fabric` as both a Fabric-adjacent consumption target and an authoring surface. The repo includes skills for semantic model consumption and authoring, FabricIQ-backed Power BI data analysis, and Power BI report planning, design, authoring, and management.

## Related Pages

- [[skills-for-fabric]]
- [[microsoft-fabric]]
- [[model-context-protocol-mcp]]

## Source Notes

- `FabricIQ.agent.md` routes Power BI report and semantic model questions through artifact discovery, schema inspection, value resolution, DAX generation, and execution.
- The `powerbi-authoring` plugin includes semantic model authoring plus Power BI report planning, design, authoring, and management skills.
