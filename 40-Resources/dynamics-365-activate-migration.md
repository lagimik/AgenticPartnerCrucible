---
title: Dynamics 365 Activate ERP and Salesforce Migration
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [dynamics-365-activate, salesforce, sap-ecc, erp, migration]
sources:
  - https://www.microsoft.com/en-us/dynamics-365/blog/it-professional/2026/11/19/dynamics-365-activate-erp-crm-migration/
  - https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/dynamics-365-activate-overview
  - https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/migrate-salesforce-to-dynamics-365-access-setup
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Dynamics 365 Activate ERP and Salesforce Migration

## Source Summary

The [November 19 announcement](https://www.microsoft.com/en-us/dynamics-365/blog/it-professional/2026/11/19/dynamics-365-activate-erp-crm-migration/)
describes an AI-assisted discovery, requirements, configuration, and migration
experience with project-team review and sign-off.

| Motion | Availability and described work |
| --- | --- |
| ERP, including SAP ECC | **Private preview**: inventory customizations, configuration, roles, integrations, and dependencies; map processes to the Business Process Catalog; version approved configuration and validate mapped data. |
| Salesforce CRM | **GA**: discover objects, fields, flows, Apex, and integrations; review Dataverse mappings and security roles; approve schema deployment; load and reconcile records, files, and attachments. |

Salesforce migration includes trial runs, incremental deltas, resumable loads,
monitoring, and automated record-count reconciliation. The article's migration
scale/history and partner testimonials are attributed evidence, not a customer
outcome guarantee. Counts alone do not prove process, financial, integration,
or security correctness.

## Access and Scope

The [overview](https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/dynamics-365-activate-overview)
currently documents Salesforce migration.
[Setup guidance](https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/migrate-salesforce-to-dynamics-365-access-setup)
covers Salesforce to **Sales or Customer Service**, English only, **US
workspaces**, and Microsoft Entra work accounts. Self-service workspace creation
needs no Microsoft approval; joining projects requires appropriate workspace
membership and project sharing. It does not unlock ERP private preview.

The earlier roadmap signal 581155 remained in development despite a November
GA estimate; this dated dedicated announcement explicitly establishes Salesforce
GA, not GA for ERP or every legacy-source scenario.

## Partner Application

**Interpretation:** Define what to retain, simplify, redesign, or exclude rather
than automatically recreating legacy customization. Separate discovery approval,
schema approval, data acceptance, security verification, and go-live decisions.
Use trial loads, business reconciliations, role tests, integration checks, and
approved rollback criteria. Confirm geography and private-preview eligibility
before committing scope. No customer data or migration workspace was accessed.

## Related

- [Dynamics 365 Activate](../10-Notes/entities/dynamics-365-activate.md)
- [Dynamics 365](../10-Notes/entities/dynamics-365.md)
- [Product-Centric ERP](dynamics-365-product-centric-erp-leader-2026.md)
- [Service-Centric ERP](dynamics-365-service-centric-erp-leader-2026.md)
- [Dynamics 365 CRM in the Flow of Work](dynamics-365-crm-flow-and-process-agents.md)
