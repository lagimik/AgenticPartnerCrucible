---
title: Oracle AI Database and Work IQ Integration
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [oracle, work-iq, microsoft-foundry, mcp, enterprise-integration]
sources:
  - https://azure.microsoft.com/en-us/blog/microsoft-and-oracle-bring-agentic-ai-into-flow-of-enterprise-work/
  - raw/2026-11-20-iq-foundry-onelake-finops/sources.md
status: active
---

# Oracle AI Database and Work IQ Integration

## Source Summary

The [November 17 Microsoft and Oracle announcement](https://azure.microsoft.com/en-us/blog/microsoft-and-oracle-bring-agentic-ai-into-flow-of-enterprise-work/)
connects Oracle transaction data with Work IQ collaboration context for Excel,
Teams, Copilot, and Foundry agent scenarios.

| Audience | Announced motion |
| --- | --- |
| Operations | Workload Virtual Instances join application, database, infrastructure, and health evidence in Azure Workload Center for Oracle, in limited preview. |
| Business users | Oracle AI Database Excel plug-in described as available today; transaction analysis enriched with work context and reviewed action plans. |
| Developers | Foundry agents use managed MCP servers and A2A coordination; MCP can target Oracle AI Database in OCI or Database@Azure. |

The article describes Entra authentication, Oracle Deep Data Security, approved
SQL/PLSQL operations and tools, application-role restrictions, and auditability.
These are distinct layers: connecting an agent does not grant unrestricted
database access or authority to commit business actions.

## Evidence and Delivery Boundaries

Workload Center access is **limited preview**, not unrestricted GA.
The Excel plug-in's availability statement does not verify its customer
licensing, tenant approval, database versions, or network prerequisites.
The source's regional count and latency comparison are dated vendor claims;
the latter depends on proximity placement and is not a workload benchmark.
FedRAMP Class D certification is described as **coming soon**, not certified
at capture time. Linked plug-in and deployment prerequisites were not
independently tested.

The no-copy agent-access framing is not a guarantee that no query result,
worksheet, trace, cache, or response leaves the database. Review every data
path, identity, retention rule, and allowed operation.

## Partner Application

**Interpretation:** Offer an Oracle-to-agent integration assessment rather than
assuming an Oracle migration. Inventory approved reports and procedures, map
user and application roles, design permission-scoped read pilots, and review
audit evidence, write approvals, latency, and operating ownership.
Validate limited-preview eligibility before proposing Workload Center.
No database connection, migration, or access change was performed.

## Related

- [Oracle-to-PostgreSQL Application Migration](oracle-postgresql-application-code-migration.md) - Separate public-preview code-conversion motion, not this Oracle-preserving integration.
- [Oracle AI Database](../10-Notes/entities/oracle-ai-database.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Microsoft IQ Context Platform](microsoft-iq-enterprise-context-platform.md)
- [Oracle-to-Power BI Analytics](oracle-to-power-bi-modern-analytics.md)
- [Model Context Protocol](../10-Notes/concepts/model-context-protocol-mcp.md)
