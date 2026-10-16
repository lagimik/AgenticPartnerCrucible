---
title: Analytics Hub - Public Source Notes
description: Summaries of public Analytics Hub sources linked from issue 125.
ms.date: 2026-10-16
ms.topic: reference
---

## Provenance

Issue https://github.com/lagimik/AgenticPartnerCrucible/issues/125 supplied
https://microsoft.github.io/Analytics-Hub/. Public pages and the repository
README were reviewed on 2026-10-16 without accessing tenant data or downloading
report templates. These notes summarize sources rather than reproduce them.

## Public Sources Reviewed

- Landing page: https://microsoft.github.io/Analytics-Hub/
- Report chooser: https://microsoft.github.io/Analytics-Hub/choose-report/
- FAQ: https://microsoft.github.io/Analytics-Hub/faq/
- Repository README: https://github.com/microsoft/Analytics-Hub

The landing page's simplified extraction returned only a featured report.
Its HTML and the public README were also reviewed to establish the broader scope.

## Source Summary

Analytics Hub is a Microsoft-maintained collection of open-source Power BI
templates, add-ons, exporters, and related tools for Copilot and AI adoption.
It spans license readiness, usage and engagement, super-user patterns, sentiment,
estimated value, and cost, including Microsoft 365 Copilot, agents, and developer
Copilot scenarios.

The chooser starts with a goal and optional product filters, then directs users
to report-specific setup guidance and downloads. The README maps different
questions to different data: Viva Insights for behavioral and super-user
analysis; Purview and Entra for chat, agent, and readiness views; Microsoft 365
Admin Center plus survey data for adoption and sentiment; GitHub Enterprise or
local sessions for developer scenarios. These sources are not interchangeable.

Each tool has its own prerequisites, permissions, and licensing dependencies.
Power BI templates require Power BI Desktop. The README explicitly says the
PAX exporter is not a prerequisite for every Purview-based report; manual
exports or included lightweight collection scripts may be used.

The FAQ cautions that cross-company Copilot benchmarks can mislead because
rollout, culture, product enablement, and change-management conditions vary.
It recommends progress against the organization's own baseline and a stated
internal hypothesis instead.

## Boundaries and Withheld Material

The collection's production-readiness, licensing, and environment/data-flow
claims were not independently validated for each tool. Template outputs,
estimated value, and behavioral associations are not causal proof of realized
financial returns.

Public navigation labels some destinations Microsoft-only or team-only.
Those destinations were not accessed or published. No tenant exports, customer
data, templates, internal demos, or team results were ingested.

## Partner Interpretation

Partners can offer goal-led report selection, data-access readiness, governed
deployment, cohort baseline analysis, and recurring adoption reviews. Treat
value assumptions and data completeness as explicit review items, not
guaranteed benefits or universal industry benchmarks.
