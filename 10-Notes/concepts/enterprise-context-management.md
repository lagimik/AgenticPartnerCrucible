---
title: Enterprise Context Management
type: concept
created: 2026-11-27
updated: 2026-11-27
tags: [enterprise-context, grounding, permissions, reusable-expertise, governance]
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - raw/2026-11-27-ignite-2026-book-of-news/source.md
status: active
---

# Enterprise Context Management

**Interpretation of the Ignite IQ architecture:** maintain permission-aware
access to business knowledge, work signals and reusable expertise so multiple
agents can apply consistent context without copying everything into each
agent's prompt or giving every agent the same authority.

## Pattern

Separate four concerns:

1. **Evidence:** source data, documents, measures, relationships and freshness.
2. **Meaning:** semantic models, ontologies, entity resolution and citations.
3. **Expertise:** versioned guidance, plugins, skills and tool definitions.
4. **Authority:** caller identity, source access, tool permissions and approvals.

Inherited organization/business-unit/project guidance can reduce repeated
configuration, but guidance is not a security boundary. Retain source
provenance, explicit change ownership, audit trails and evaluation baselines.
Decide which context is required for a task rather than exposing the entire
estate to every agent.

## Boundaries

Access to a semantic model does not authorize changing its source systems.
A shared context layer does not grant universal cross-platform connectors.
Persistent memory requires lifecycle and access controls. Generated summaries,
inferred relationships and ranked web sources remain evidence to evaluate,
not guaranteed truth.

Validated learning is related but separate: observed outcomes and approved
configuration changes feed later work through
[agent configuration optimization](agent-configuration-optimization.md).
Do not allow unreviewed context to become inherited instruction or tool authority.

## Related

- [Microsoft IQ](../entities/microsoft-iq.md)
- [Ignite IQ architecture](../../40-Resources/ignite-2026/microsoft-iq.md)
- [Read-only analytics and action separation](read-only-analytics-and-action-separation.md)
- [Shared storage with catalog-mediated access](shared-storage-catalog-mediated-access.md)
- [Agent Skill Common Architecture](agent-skill-common-architecture.md)
- [AI governance](ai-governance.md)
