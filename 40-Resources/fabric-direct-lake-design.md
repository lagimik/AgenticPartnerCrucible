---
title: Fabric Direct Lake Storage Mode Design
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-fabric, power-bi, direct-lake, semantic-models]
sources:
  - https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-overview
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Fabric Direct Lake Storage Mode Design

[Microsoft Learn](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-overview)
describes Direct Lake as a Power BI semantic-model table storage mode over
Delta tables in OneLake. It loads required columns for VertiPaq queries rather
than importing an entire dataset on each refresh.

## Source Summary

Framing refreshes metadata references to current Delta files; it is not the same
as an Import data refresh. Data preparation moves upstream into lakehouse or
warehouse processes. Automatic updates or programmatic framing still matter
for freshness; Direct Lake is not a blanket no-maintenance promise.

| Design choice | Direct Lake on OneLake | Direct Lake on SQL |
| --- | --- | --- |
| Source scope | One or more compatible Fabric sources | One supported source through its SQL analytics endpoint |
| DirectQuery fallback | No fallback | Supported when enabled, including applicable SQL views or SQL RLS scenarios |
| Security boundary | SQL-endpoint RLS is not applied to direct file access | SQL security can affect access and cause fallback |
| Guardrail excess | Refresh can fail and leave the model unqueryable until corrected | Can fall back with warnings and slower queries if fallback is enabled |

Do not assume SQL endpoint permissions protect a model that reads OneLake files
directly. Design OneLake access and semantic-model RLS/OLS explicitly.

## Partner Design Guidance

Prototype with representative data volumes, concurrency, security roles,
freshness requirements, and fallback settings. Validate Delta layout and
capacity guardrails rather than promising Import-like performance for every
workload. Excessive paging can impair performance even when data fits on disk.

Direct Lake requires Fabric capacity. Import and DirectQuery remain valid
choices; self-service data preparation and source constraints may favor them.
Feature-specific preview limits and composite-model support evolve, so confirm
the current capability matrix rather than generalizing across both variants.

## Related

- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Power BI](../10-Notes/entities/power-bi.md)
- [Capacity observability and protection](fabric-capacity-observability-and-protection.md)
- [Medallion architecture guidance](fabric-data-warehouse-medallion-series.md)
