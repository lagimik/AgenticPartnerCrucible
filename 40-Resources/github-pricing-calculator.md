---
title: GitHub Pricing Calculator
type: resource
created: 2026-11-14
updated: 2026-11-14
tags: [github, pricing, finops, copilot]
sources:
  - https://github.com/pricing/calculator
  - https://github.com/lagimik/AgenticPartnerCrucible/issues/152
  - raw/2026-11-14-github-open-issues-146-152/issues.md
status: active
---

# GitHub Pricing Calculator

## Source Summary

GitHub's public [calculator](https://github.com/pricing/calculator) estimates
plan seats and usage across Copilot, Codespaces, Actions, Packages, LFS and
security/quality products. Copilot and Code Quality expose AI-credit inputs;
security and quality licensing also use active-committer dimensions.

The FAQ says estimates are in USD, exclude free entitlements and are not binding
quotes. Actual pricing depends on purchase date, currency and agreement.

## Partner Interpretation

Use the tool to structure a workload estimate, recording developer seats,
committer counts, runner choices, compute hours, retained storage, credit usage
and egress assumptions separately. Review negotiated terms and entitlements
before a proposal; do not promote zero-valued initial controls as a free service.

Stopped Codespaces can still retain billable storage. Code Quality's license and
credit subtotal excludes its Actions scan minutes, which need a separate estimate.
These source-described boundaries matter when reconciling an end-to-end workload.

## Evidence Boundaries

Controls and FAQ were reviewed, not a configured estimate or customer bill.
No purchase, account access or contractual reconciliation was performed.
Prefer the live calculator over copied unit prices.

## Related

- [GitHub](../10-Notes/entities/github.md)
- [GitHub Copilot Benchmarks](github-copilot-benchmarks.md)
- [Digital Apps and Innovation](../100-Crucible/DigitalAppsandInnovationSolutionArea.md#github)
