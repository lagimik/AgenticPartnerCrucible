---
title: Azure SRE Agent - Enterprise Adoption and Governance
type: resource
created: 2026-10-16
updated: 2026-10-16
tags: [azure-sre-agent, governance, agent-topology, agent-as-code, operations]
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-2-from-one-team-to-enterprise/4564311
  - raw/2026-10-16-azure-sre-agent-adoption/sources.md
status: active
---

# Azure SRE Agent - Enterprise Adoption and Governance

## Source Summary

[Part 2 of Microsoft's enterprise adoption guide](https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-2-from-one-team-to-enterprise/4564311),
published October 15, 2026, addresses sharing an agent, choosing agent boundaries,
coordinating work, and operating a version-controlled deployment baseline.

## Shared Agent Does Not Mean Partitioned Context

An SRE Agent shares connected knowledge, investigation history, memory, skills,
connectors, workflows, and configuration among its users. User roles govern
actions within that agent; they do not create private context partitions.

Use Reader for viewing, Standard User for chat and operational use, Author for
building, and Administrator for administration and sensitive approvals. Author
alone does not grant chat or approval access, and Azure Owner or Contributor
alone does not grant SRE Agent data-plane permissions.

Combine roles with tool access policies, approval expiration, deterministic
hooks, AAU consumption limits, and audit review. Application Insights records
agent activity and approvals; Azure Activity Log records resource-management
changes. Common instructions guide behavior but do not enforce a hard boundary.
VNet mode has documented platform and connector traffic exceptions, so do not
treat it as proof that all traffic follows customer-controlled egress.

## Choose Boundaries by Context and Authority

There is no fixed subscription, resource, or team count requiring another agent.
Share an agent only where users may share its context and teams can align on:

- Domain guidance and operational expertise.
- User visibility and resource access.
- Managed identity, credentials, and resource scopes.
- Autonomous actions, review requirements, and approvers.
- Workflow ownership and release coordination.
- Residency, processing, tenant, and legal requirements.

Separate agents when these requirements diverge. Maintain a non-production
agent for testing material changes before production. Examples include a shared
platform agent collaborating with application-team agents, or team-owned agents
coordinating directly without a central runtime.

## Collaborate Without Combining Authority

Pass the task, impact, evidence links, checks already performed, findings,
uncertainty, and requested analysis or action as a structured handoff. Use
incident or ticket automation, HTTP triggers, or MCP-compatible clients and
orchestrators. Preserve the end-to-end outcome in a shared incident or change
record while each team retains its own context and action boundary.

## Operate the Agent as Code

Export a working, refined agent and review it before committing an approved
baseline to Git. The guide notes that exports include synthesized knowledge and
workspace memories by default: treat these as potentially sensitive operational
data, not harmless configuration. Keep credentials and secrets outside Git.

Use Bicep or Terraform and parameterized baselines for shared identity, network,
security, audit, and deployment controls. Reuse approved skills and MCP
integrations through a private plugin marketplace with installations pinned to
Git commits, without forcing all agents to share runtime context.

## Partner Application and Boundaries

**Interpretation:** Extend a successful pilot into a shared-context access
assessment, agent-topology decision, handoff design, and agent-as-code service
with change review, drift checks, and controlled capability updates.

These are architecture recommendations, not a universal topology or compliance
certification. Recheck current product permissions, networking exceptions,
residency behavior, and export contents before deployment or cross-team reuse.

## Related Pages

- [Azure SRE Agent](../10-Notes/entities/azure-sre-agent.md)
- [Part 1 - First Deployment and Workflow Adoption](./azure-sre-agent-first-deployment.md)
- [Configuration Guide](./azure-sre-agent-configuration-guide.md)
- [Agentic Cloud Operations](../10-Notes/concepts/agentic-cloud-operations.md)
- [Agent Scaling Design](../10-Notes/concepts/agent-scaling-design.md)
