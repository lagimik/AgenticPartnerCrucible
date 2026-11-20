---
title: Oracle-to-PostgreSQL Application Code Migration Preview
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [oracle, postgresql, github-copilot, modernization, migration]
sources:
  - https://azure.microsoft.com/en-us/updates?id=579231
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Oracle-to-PostgreSQL Application Code Migration Preview

## Source Summary

[Update 579231](https://azure.microsoft.com/en-us/updates?id=579231) introduces a
**public-preview** plugin with AI-assisted skills for Oracle-dependent application
code moving to Azure Database for PostgreSQL. GitHub Copilot CLI and Visual
Studio Code can consume it; Modernize CLI users can incorporate the skills into
existing modernization workflows.

The skills identify Oracle-specific dependencies and generate proposed code
changes. Developers review and validate those changes before accepting them.
The release item does not enumerate complete language/driver coverage or verify
automatic schema, stored-procedure, data, or production migration.

## Partner Application

**Interpretation:** Scope this as reviewed application compatibility work, not
a complete database migration service. Inventory dependencies and separate code
conversion from schema/data movement, transaction semantics, query plans,
driver behavior, and operational cutover. Use representative compatibility,
performance, rollback, and data-reconciliation evidence before promotion.

Oracle AI Database/Work IQ integration is a different option that retains Oracle
as an operational source; do not present it as this migration path.
No plugin installation, code conversion, or database operation was performed.

## Related

- [Oracle AI Database](../10-Notes/entities/oracle-ai-database.md)
- [Oracle and Work IQ Integration](oracle-ai-database-work-iq-integration.md)
- [AI-Augmented Modernization](ai-augmented-code-modernization-leader.md)
- [Azure Catalyst Target Assessment](azure-catalyst-webapp-target-assessment.md)
- [Postgres MCP Server](postgres-mcp-server.md)
