---
title: Microsoft IQ Enterprise Context Platform
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [microsoft-iq, enterprise-context, work-iq, fabric-iq, foundry-iq, web-iq]
sources:
  - https://azure.microsoft.com/en-us/blog/introducing-the-new-microsoft-iq-putting-your-organizations-intelligence-to-work-in-every-agent/
  - https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/
  - raw/2026-11-20-iq-foundry-onelake-finops/sources.md
  - raw/partner-crucible-signal-history/rss-partner-signal-2026-11-20.md
status: active
---

# Microsoft IQ Enterprise Context Platform

## Source Summary

The [November 17 announcement](https://azure.microsoft.com/en-us/blog/introducing-the-new-microsoft-iq-putting-your-organizations-intelligence-to-work-in-every-agent/)
positions Microsoft IQ as an enterprise-context management platform. Its four
layers contribute different evidence:

| Layer | Context |
| --- | --- |
| Work IQ | Collaboration, documents, conversations, decisions, and connected business applications. |
| Fabric IQ | Governed business data, entities, relationships, and rules. |
| Foundry IQ | Institutional knowledge, policies, and authoritative documents. |
| Web IQ | Timely external information, with source-selection controls. |

Business plugins package sources, skills, tools, and business know-how for reuse
across supported agents and platforms. This is the platform announcement,
not the earlier [synthetic supply-chain accelerator](microsoft-iq-solution-accelerator.md).

## Availability and Control Boundaries

The announcement mixes GA, preview, and future capabilities. Foundry IQ graphs
and several Fabric IQ integrations are preview; Fabric data agents in Copilot
are coming soon; Foundry IQ Serverless GA is announced for December 2026.
Do not treat the umbrella platform as blanket GA.

**Unresolved source differences:** The article labels granular Work IQ MCP
policies and real-time meeting context GA, whereas roadmap items 570671 and
572674 in the [preserved signal report](../raw/partner-crucible-signal-history/rss-partner-signal-2026-11-20.md)
are in development with January 2027 GA estimates. The article calls Fabric
apps preview while the [dedicated Apps announcement](fabric-apps-rayfin-governed-delivery.md)
announces GA. These may represent scope or publication differences; verify the
exact capability and tenant rather than silently choosing a status.

[Work IQ documentation](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)
describes user-scoped requests and fine-grained policy evaluation, audit logs,
and connector participation requirements. API usage is metered independently
of Copilot user licensing. Plugin packaging does not authorize every source,
tool, or action and does not erase dependency costs.

## Partner Application

**Interpretation:** Start with one measurable process. Identify authoritative
data, institutional knowledge, external sources, business rules, and action
owners; curate a reusable plugin and test permission trimming, freshness,
cross-source consistency, approvals, and cost per successful outcome.
Keep model capability separate from customer-owned context and decision rights.
No plugin was deployed or enterprise system connected.

## Related

- [Microsoft IQ](../10-Notes/entities/microsoft-iq.md)
- [Reusable Enterprise Context](../10-Notes/concepts/reusable-enterprise-context.md)
- [Foundry Continuous Improvement](foundry-continuous-improvement.md)
- [OneLake Data, Context, and Governance](onelake-data-context-governance.md)
- [Oracle Data in Agent Workflows](oracle-ai-database-work-iq-integration.md)
