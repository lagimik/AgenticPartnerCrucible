---
title: Fabric Data Agent
type: entity
created: 2026-11-27
updated: 2026-11-27
tags: [microsoft-fabric, data-agents, analytics, onelake, identity]
sources:
  - raw/2026-11-27-fabric-agent-platform-selection/source.md
  - https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq
status: active
---

# Fabric Data Agent

A [generally available Fabric item](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) for conversational analytics over configured data sources. It generates read-only SQL, DAX, or KQL queries; it does not perform downstream business actions or change data.

Core feature GA does not confer GA on every source, protection capability, or external integration. It is distinct from the [Data Engineering Agent](../../40-Resources/fabric-project-osmos-data-engineering-agent.md), which can execute Spark tasks.

## Identity boundary

Agent sharing does not inherently grant underlying-source access. However, the [Copilot Studio tool connection](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool) can use User or Maker authentication; Maker mode exposes answers through the maker's permissions rather than each consumer's. The [Foundry Fabric IQ connection](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq) uses delegated user authentication.

The orchestration model outside Fabric does not change the data agent's internal model. Source selection, semantic meaning, identity, output limits, and consuming-platform data handling remain separate configuration concerns.

## Related pages

- [Platform Selection and Governed Delivery](../../40-Resources/fabric-data-agents-platform-selection.md)
- [Read-Only Analytics and Action Separation](../concepts/read-only-analytics-and-action-separation.md)
- [Microsoft Fabric](microsoft-fabric.md)
- [Microsoft Foundry](microsoft-foundry.md)
- [Microsoft IQ Solution Accelerator](../../40-Resources/microsoft-iq-solution-accelerator.md)
