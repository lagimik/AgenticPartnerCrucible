---
title: Claude Cost Management and Tagging in Microsoft Foundry
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-foundry, claude, finops, cost-allocation, tagging]
sources:
  - https://azure.microsoft.com/en-us/updates?id=577260
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Claude Cost Management and Tagging in Microsoft Foundry

[Azure update 577260](https://azure.microsoft.com/en-us/updates?id=577260),
published October 27, 2026, announces **general availability** of Claude cost
management and tagging in Foundry. Its complete description and Launched status
were checked through the public Release Communications detail tool.

## Source Summary

- Claude charges appear under the associated Foundry resource, rather than only
  under a separate SaaS attribution.
- Claude deployments and Foundry resources support organizational tags.
- Cost records include `model` and `usage_type` dimensions, enabling model-level
  grouping and separation of input- and output-token costs.
- Azure Cost Management Cost analysis can group costs by resource or tag.

## Partner Interpretation

Define business-owner and workload tags, inspect resource attribution in real
cost records, and reconcile model and token-type dimensions before introducing
showback or chargeback. Tag support is an allocation mechanism, not a budget,
spending cap, or automatic reduction in model cost.

This announcement does not establish historical cost backfill or a universal
processing-latency guarantee. Verify customer billing data and current service
behavior before promising either.

## Related

- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [AI spend taxonomy in FOCUS](focus-ai-spend-taxonomy.md)
- [Token economics](../10-Notes/concepts/token-economics.md)
