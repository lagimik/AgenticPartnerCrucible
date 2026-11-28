---
title: Read-Only Analytics and Action Separation
type: concept
created: 2026-11-27
updated: 2026-11-27
tags: [agentic-ai, analytics, authorization, identity, governance]
sources:
  - raw/2026-11-27-fabric-agent-platform-selection/source.md
  - https://techcommunity.microsoft.com/blog/analyticsonazure/unlocking-data-value-with-fabric-and-microsoft-ai-agents-choose-deploy-optimise/4574895
  - https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool
status: active
---

# Read-Only Analytics and Action Separation

A specialist can answer a data question without owning authority to change the systems described by that answer. The [Fabric platform-choice article](https://techcommunity.microsoft.com/blog/analyticsonazure/unlocking-data-value-with-fabric-and-microsoft-ai-agents-choose-deploy-optimise/4574895) motivates layered composition; [Fabric data-agent documentation](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) establishes the read-only analytical boundary.

## Separate contracts

| Contract | Review question |
| --- | --- |
| Data access | Which identity queries which sources, and who can consume its answers? |
| Analytical meaning | Which certified measures, filters, timestamps, and output limits support the answer? |
| Orchestration | Can the front door rephrase, combine sources, or select a different specialist? |
| Action authority | Which separately approved tools may act, under which identity, with what validation and recovery? |

Read-only is not the same as safe to share. The [Studio Maker authentication option](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool) can expose data through a maker's permissions even when consumers lack their own source access.

**Interpretation:** Treat an analytical answer as evidence for a decision, not an authorization token. Verify its scope and provenance before downstream action; enforce tool permissions, approvals, and recovery independently. A shared underlying dataset does not guarantee identical channel output or identical audience access.

## Related pages

- [Fabric Data Agent](../entities/fabric-data-agent.md)
- [Platform Selection and Governed Delivery](../../40-Resources/fabric-data-agents-platform-selection.md)
- [AI Agent Lifecycle](ai-agent-lifecycle.md)
- [Shared Storage with Catalog-Mediated Access](shared-storage-catalog-mediated-access.md)
