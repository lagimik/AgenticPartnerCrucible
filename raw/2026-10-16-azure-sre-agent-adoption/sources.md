---
title: Azure SRE Agent Enterprise Adoption Series - Source Notes
description: Provenance and summaries of the two public enterprise adoption guides.
ms.date: 2026-10-16
ms.topic: reference
---

## Provenance

The user supplied both public Microsoft Community Hub URLs on 2026-10-16.
Both pages were accessible without authentication and reviewed on that date.
Their article content was read from the pages' structured BlogPosting metadata
because the simplified page extraction returned only the titles.
The author handle is `dchelupati`; both articles were published on 2026-10-15.
These are source summaries, not verbatim article copies or independent product
validation.

## Part 1 - Deploying Your First Azure SRE Agent

- Source: https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-1-deploying-your-first-azure-/4564306
- Summary: Start with one recurring operational problem that the team understands
  and can judge, rather than designing the final enterprise topology first.
  Connect only the required telemetry, code, deployment history, and runbooks;
  begin with diagnostic or read-only managed-identity access and scoped Azure
  RBAC. Replay known incidents, then work alongside responders on live issues.
  Establish a baseline and measure the outcome in the incident, monitoring, or
  deployment system already used by the team.
- Customization: Begin with built-in capabilities and reuse existing plugins.
  Skills supply organizational procedures; tools supply deterministic execution,
  external access, or exact output; a custom subagent packages a focused,
  independently invocable or triggered workflow.
- Automation: Use response plans for incidents or alerts, scheduled tasks for
  recurring work, and HTTP triggers for external workflows. Begin in Review
  mode; consider Autonomous mode only for actions the team has already approved
  operators to perform without case-by-case review.
- Boundary: Adoption guidance, not a measured performance guarantee, automatic
  authorization to make production changes, or a requirement to customize.

## Part 2 - From One Team to Enterprise-Wide Adoption

- Source: https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-2-from-one-team-to-enterprise/4564311
- Summary: A shared SRE Agent shares context, knowledge, investigation history,
  memory, workflows, and configuration; user roles do not partition that state.
  Select built-in Reader, Standard User, Author, and Administrator roles by
  responsibility. Author alone does not grant chat or approval access; Azure
  Owner and Contributor alone do not grant SRE Agent data-plane access.
- Governance: Combine tool access policies, approval expiry, deterministic
  hooks, appropriate network controls, AAU usage budgets, Application Insights
  audit telemetry, and Azure Activity Log. Instructions guide behavior but are
  not hard enforcement; VNet mode has documented traffic exceptions.
- Topology: No fixed subscription, resource, or team count requires a new agent.
  Separate agents when context visibility, expertise, identity and permissions,
  action policies, workflow ownership, or residency requirements differ; retain
  a non-production boundary for material changes.
- Collaboration: Pass a structured handoff with task, impact, evidence, checks,
  findings, uncertainty, and requested action. Use existing incident/ticket
  automation, HTTP triggers, or MCP-compatible clients while preserving a
  shared outcome record and each team's authority.
- Deployment: Export a proven working configuration, review it for sensitive
  content, keep credentials outside Git, and version the approved baseline.
  Exports include synthesized knowledge and workspace memories by default.
  Standardize shared controls with infrastructure as code; reuse approved
  capabilities through a private plugin marketplace pinned to Git commits.
- Boundary: Architecture recommendations, not proof of tenant isolation,
  regulatory compliance, universal topology, or permission to share memories
  and knowledge across organizational boundaries.

## Partner Interpretation

A staged readiness and pilot engagement can lead into workflow automation,
shared-agent access assessment, topology design, and agent-as-code operations.
This service packaging is a vault interpretation of the guidance, not a
Microsoft-defined offer or a claimed customer outcome.
