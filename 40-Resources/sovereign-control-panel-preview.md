---
title: Sovereign Control Panel Preview Assessment Boundaries
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [sovereignty, azure, assessment, residency, business-continuity]
sources:
  - https://learn.microsoft.com/en-ca/azure/azure-sovereign-clouds/public/sovereign-control-panel
  - https://learn.microsoft.com/en-us/azure/azure-sovereign-clouds/public/sovereign-control-panel
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Sovereign Control Panel Preview Assessment Boundaries

## Source Summary

The [SCP overview](https://learn.microsoft.com/en-ca/azure/azure-sovereign-clouds/public/sovereign-control-panel)
describes a public-preview Azure portal assessment of selected subscriptions
and management groups. It groups findings into data residency, encryption at
rest/in transit, network exposure, and business-continuity compatibility.
Residency360 extends discovery to supported linked data-bearing copies.

The global service stores **view data and metadata in Sweden**. Preview
assessment is geared to European cloud regions; the tenant itself need not be
European. Assessment geography and view-hosting region are separate.

## Assessment Is Not Enforcement

Selected policy assignments are **non-enforcing**. Choosing controls does not
configure resources or establish guardrails; Azure governance processes remain
responsible for enforcement. Public-preview remediation is limited to eligible
primary-resource residency; linked copies are assessment-only. Some service/
region gaps have no remediation.

RBAC, resource-provider registration, supported controls, and completed reports
bound coverage. Reports are not real-time. To change existing scope or controls,
create a replacement view.

Continuity results assess resource compatibility/constraints, not resource
movement, configured recovery, or proof of end-to-end workload continuity.
RTO, RPO, and operating duration are unavailable in preview.

## Partner Application

**Interpretation:** Move from sovereignty discovery to a dated, explicit
assessment scope and evidence register. Review Swedish metadata hosting with
accountable owners; record unevaluated resources and linked copies. Plan approved
remediation separately and validate application-level recovery exercises.
Do not market an SCP result as legal advice or compliance certification.
No assessment policy or remediation was applied.

## Related

- [Sovereign Cloud Explorer](sovereign-cloud-explorer.md)
- [Sovereign AI Control and Choice](sovereign-ai-control-choice.md)
- [Digital Sovereignty Adoption](digital-sovereignty-adoption-caf.md)
- [Azure Infrastructure Workloads](../100-Crucible/AzureInfrastructureSolutionArea.md)
