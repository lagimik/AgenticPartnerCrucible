---
title: Microsoft IQ Solution Accelerator
type: resource
created: 2026-10-27
updated: 2026-10-27
tags: [fabric-iq, foundry-iq, work-iq, supply-chain, solution-accelerator]
sources:
  - https://github.com/microsoft/microsoft-iq-solution-accelerator
  - https://github.com/microsoft/microsoft-iq-solution-accelerator/blob/main/docs/TechnicalArchitecture.md
  - https://github.com/microsoft/microsoft-iq-solution-accelerator/blob/main/docs/DeploymentGuide.md
  - raw/2026-10-27-github-open-issues-125-134/issues.md
  - raw/2026-10-27-github-open-issues-125-134/sources.md
status: active
---

# Microsoft IQ Solution Accelerator

## Source Summary

The public [Microsoft IQ Solution Accelerator](https://github.com/microsoft/microsoft-iq-solution-accelerator)
demonstrates supply-chain disruption detection, impact analysis, and coordinated
response using Fabric IQ data and ontology, Foundry IQ enterprise knowledge,
and Work IQ context. A Copilot Studio workflow coordinates a Foundry chat
agent for contracts and policies and a Fabric ontology data agent for
customers, inventory, suppliers, and demand.

The repository explicitly describes synthetic demonstration data and preview
dependencies, including MCP integration. It is best suited to evaluation,
experimentation, and demonstrations rather than assumed production readiness.

## Prerequisites and Delivery Boundaries

Review the current [deployment guide](https://github.com/microsoft/microsoft-iq-solution-accelerator/blob/main/docs/DeploymentGuide.md)
before running anything: subscription resource-creation and role-assignment
permissions, Fabric tenant settings for Ontology and Graph previews, model
capacity and region, and product-specific licensing all matter.
The README's product cost table is not a comprehensive deployment estimate.

**Interpretation:** Start with a bounded disruption workshop, map customer
data and decision authority, and adapt schemas, knowledge sources, and
workflow approvals. Validate permission boundaries, evaluation cases, cost,
operational ownership, and teardown before moving beyond a demonstration.
No accelerator deployment or customer-data connection was performed.

## Related Pages

- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Model Context Protocol](../10-Notes/concepts/model-context-protocol-mcp.md)
- [AI Agent ROI Operating Model](ai-agent-roi-operating-model.md)
