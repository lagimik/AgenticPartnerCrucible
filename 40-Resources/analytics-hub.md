---
title: Analytics Hub for Copilot Adoption and Value Measurement
type: resource
created: 2026-10-16
updated: 2026-10-16
tags: [copilot, adoption, power-bi, viva-insights, value-measurement]
sources:
  - https://microsoft.github.io/Analytics-Hub/
  - https://microsoft.github.io/Analytics-Hub/choose-report/
  - https://microsoft.github.io/Analytics-Hub/faq/
  - https://github.com/microsoft/Analytics-Hub
  - raw/2026-10-16-github-open-issues-125/issues.md
  - raw/2026-10-16-github-open-issues-125/sources.md
status: active
---

# Analytics Hub for Copilot Adoption and Value Measurement

## Source Summary

[Analytics Hub](https://microsoft.github.io/Analytics-Hub/) collects
Microsoft-maintained open-source Power BI templates, exporters, add-ons, and
related tools for Copilot and AI adoption analysis. The public
[repository overview](https://github.com/microsoft/Analytics-Hub) spans readiness,
usage, super-user behavior, sentiment, estimated value, and developer scenarios.

## Select by Question and Available Evidence

Use the [report chooser](https://microsoft.github.io/Analytics-Hub/choose-report/)
to select a goal and product, then review the report's own setup instructions.

| Question | Example evidence route described by the overview |
| --- | --- |
| How do sustained usage and super-user patterns develop? | Viva Insights behavioral and collaboration data. |
| How are Copilot Chat and agents used, and who is ready for licenses? | Purview activity with Entra attributes and license context. |
| How does adoption compare with employee sentiment? | Microsoft 365 Admin Center data and survey responses. |
| How are developers using GitHub Copilot? | GitHub Enterprise metrics or tool-specific local-session analysis. |

These sources support different questions; one export is not a universal
replacement for another.

## Readiness and Interpretation

Check each tool's data schema, roles, licensing, privacy requirements, and setup
instructions. Power BI templates require Power BI Desktop. The overview says
PAX is optional rather than a prerequisite for all Purview-based reports:
manual exports or report-specific lightweight collectors may be sufficient.

The [FAQ](https://microsoft.github.io/Analytics-Hub/faq/) cautions against
cross-company benchmarks without comparable rollout and organizational context.
Use the customer's own baseline and an explicit hypothesis to judge progress.
Estimated value and observed usage associations are not proof of realized
financial returns or causal productivity gains.

## Partner Application

**Interpretation:** Package a goal-led measurement engagement: select the report,
validate data access and completeness, deploy with appropriate privacy controls,
baseline cohorts, and review adoption and value assumptions on a recurring
cadence. Keep reported usage, estimated benefits, and verified business outcomes
separate.

## Access and Review Boundaries

The public hub and README were reviewed, not every downloadable tool or tenant
integration. Public access to the hub does not remove report-specific licensing
or permission requirements. No tenant data was collected or templates executed.
Microsoft-only and team-only navigation destinations were excluded.

## Related Pages

- [Copilot Adoption Measurement](../10-Notes/concepts/copilot-adoption-measurement.md)
- [Power BI](../10-Notes/entities/power-bi.md)
- [AI Agent ROI Operating Model](./ai-agent-roi-operating-model.md)
- [Modern Work Copilot](../100-Crucible/ModernWorkSolutionArea-Copilot.md#copilot-adoption)
