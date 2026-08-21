---
title: Giving AI Spend a Name in FOCUS
type: resource
created: 2026-08-21
updated: 2026-08-21
tags:
  - finops
  - focus
  - ai-cost
  - tokens
  - chargeback
sources:
  - https://techcommunity.microsoft.com/blog/finopsblog/who-ordered-all-these-tokens-giving-ai-spend-a-name-in-focus/4547978
  - raw/2026-08-21-github-open-issues-55-63/issues.md
status: active
---

# Giving AI Spend a Name in FOCUS

This FinOps article applies the FinOps Open Cost and Usage Specification (FOCUS) to AI costs that are otherwise scattered across ambiguous billing categories and free-text meter names.

## Enrichment Pattern

FOCUS provides a vendor-neutral cost foundation, but AI analysis still needs an enrichment layer. Parse or map billing records into consistent dimensions such as:

- Model or agent name
- Token type, including input, output, cached, reasoning, and embedding
- Product line or use case
- Unit of measure
- Source system or provider

## Outcome

A normalized AI taxonomy enables showback, chargeback, unit economics, model comparison, and spend attribution across Copilots, first-party agents, partner services, and custom applications.

## Related Pages

- [[token-economics]]
- [[economics-of-agent-optimization]]
