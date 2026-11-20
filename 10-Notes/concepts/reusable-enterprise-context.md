---
title: Reusable Enterprise Context
type: concept
created: 2026-11-20
updated: 2026-11-20
tags: [enterprise-context, governance, agent-skills, evaluation]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/bringing-trusted-fabric-iq-context-to-wherever-people-and-agents-work/5423049
  - https://azure.microsoft.com/en-us/blog/introducing-the-new-microsoft-iq-putting-your-organizations-intelligence-to-work-in-every-agent/
  - https://azure.microsoft.com/en-us/blog/continuous-improvement-comes-to-microsoft-foundry/
status: active
---

# Reusable Enterprise Context

Reusable enterprise context packages authoritative sources, business meaning,
skills, tools, and access rules for multiple agents instead of rebuilding an
isolated grounding stack for each workflow. Microsoft's
[IQ announcement](../../40-Resources/microsoft-iq-enterprise-context-platform.md)
provides a concrete platform example, not a guarantee that every connector
preserves the same permissions or freshness.

## Design Contract

**Interpretation:** Give each reusable context asset an owner, source provenance,
version, freshness requirement, permitted users/actions, and evaluation cases.
Separate collaboration evidence, transaction data, policy knowledge, and web
information. Resolve inconsistent business definitions explicitly.

Reuse does not imply shared authority: test denied access, source identity,
tool permissions, and consequential-action approvals for every consumer.
Promote improved skills or context only after representative evaluation and
review; retain rollback and traceable evidence.

## Related

- [Fabric IQ Context Reuse](../../40-Resources/fabric-iq-trusted-context.md) - Shared metrics and business relationships, with consumer-specific access and release boundaries.
- [Microsoft IQ](../entities/microsoft-iq.md)
- [Agent Configuration Optimization](agent-configuration-optimization.md)
- [Shared Storage with Catalog-Mediated Access](shared-storage-catalog-mediated-access.md)
- [Foundry Continuous Improvement](../../40-Resources/foundry-continuous-improvement.md)
