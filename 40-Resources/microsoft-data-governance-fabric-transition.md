---
title: Microsoft Data Governance Transition to Fabric
type: resource
created: 2026-11-14
updated: 2026-11-14
tags: [data-governance, microsoft-fabric, onelake, purview, transition]
sources:
  - https://techcommunity.microsoft.com/blog/microsoft-security-blog/a-next-step-in-the-evolution-of-the-microsoft-data-governance-strategy/4572227
  - raw/2026-11-14-microsoft-data-governance-strategy/source.md
status: active
claims:
  - id: claim-001
    text: "Microsoft announces that support for Purview Data Governance will end November 12, 2027."
    confidence: 0.99
    status: provisional
    evidence:
      - source: https://techcommunity.microsoft.com/blog/microsoft-security-blog/a-next-step-in-the-evolution-of-the-microsoft-data-governance-strategy/4572227
        kind: announcement
        excerpt: "Support for Purview Data Governance will end Nov. 12, 2027."
    captured: 2026-11-14
    updated: 2026-11-14
---

# Microsoft Data Governance Transition to Fabric

## Source Summary

The [November 12, 2026 Microsoft announcement](https://techcommunity.microsoft.com/blog/microsoft-security-blog/a-next-step-in-the-evolution-of-the-microsoft-data-governance-strategy/4572227)
positions **Fabric and the OneLake catalog as Microsoft's data-governance
foundation**. It announces retirement of **Purview Data Governance**, with
support ending **November 12, 2027**, and transition support starting with the
announcement.

**This does not retire all Microsoft Purview.** Purview remains focused on data
security and compliance: classification, sensitivity labeling, protection,
data-loss prevention, and compliance across Microsoft 365, Azure, Fabric, and AI.

## Governance and Protection Responsibilities

| Scope | Announcement position |
| --- | --- |
| Governance foundation | Fabric OneLake catalog brings stewardship, lineage, policies, discovery, and trust signals close to data consumption. |
| External estate | Supported shortcuts, mirroring, and connectors extend the model beyond data physically stored in OneLake. |
| Security and compliance | Purview continues protecting data and supporting compliance, integrated with existing Microsoft platforms. |
| Gaps beyond current Fabric capabilities | Microsoft acknowledges broader needs and names third-party governance integrations. |

The source says governance is included in Fabric capacity instead of separate
meters. This is a packaging statement, not evidence of unlimited consumption,
zero capacity cost, or customer-specific savings.

## Transition Motion

Microsoft directs customers with contractual obligations or highly regulated
requirements to engage their account teams early for individual assessment.
It says detailed transition guidance is available, but the reviewed article
does not link a migration runbook or specify feature parity and exception terms.

**Partner interpretation:** Inventory affected governance services, catalogs,
lineage, stewardship processes, policies, connectors, integrations, and
contractual dependencies. Map each requirement to verified Fabric or third-party
capabilities, identify gaps, and agree an evidence-based transition plan before
the announced support-end date. Preserve security/compliance controls rather
than treating governance transition as their removal.

## Boundaries

Do not infer automatic migration, lossless metadata transfer, full feature
parity, universal external-source coverage, or a need to physically move every
data source into OneLake. Supported integration and workload-specific control
behavior need verification.

Existing [OneLake Govern guidance](fabric-onelake-govern-and-skills.md) records
Govern GA with the Policies Center still preview; the strategy announcement
does not override those capability-specific limits.
The source's November 11 update label precedes its November 12 publication
display. Linked transition materials, roadmap, and third-party integrations
were not independently verified during this ingestion.

## Related Pages

- [Purview Data Governance Partner Resources](purview-data-governance-partner-resources.md) - Landing page modified before this announcement; asset contents and transition alignment remain unverified.
- [Microsoft Purview](../10-Notes/entities/microsoft-purview.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Governance and Data Protection Responsibility Split](../10-Notes/concepts/governance-data-protection-responsibility-split.md)
- [OneLake Govern and Skills](fabric-onelake-govern-and-skills.md)
- [Purview Reference Architecture Diagrams](064-microsoft-purview-referential-architecture-diagrams-microsoft-community-hub.md)
- [Preserved Source Summary](../raw/2026-11-14-microsoft-data-governance-strategy/source.md)
