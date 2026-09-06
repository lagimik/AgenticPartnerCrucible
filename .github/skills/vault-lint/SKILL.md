---
name: vault-lint
description: "Audits vault quality and claims. Use for linting, finding broken links, orphans, stale pages, weak sources, duplicates, and contradictions. - Brought to you by lagimik/AgenticPartnerCrucible"
---

# Vault Lint

## Overview

Audit the vault for structural, metadata, sourcing, linking, and claim-quality
problems. Report findings without changing files unless the user requests fixes.

## Prerequisites

* A requested audit scope, or the whole vault when no scope is specified
* Access to wiki pages, `index.md`, and cited local sources

## Quick Start

Inventory the requested scope, run the structural and claims checks, verify
suspected issues against source files, and report findings by severity.

## Workflow

1. Define the audit scope and identify applicable page instructions.
2. Check wiki pages for missing or invalid frontmatter, required fields, dates,
   types, lifecycle states, sources, and naming conventions.
3. Find unresolved internal links, orphan pages, stale index entries, and pages
   that cannot be reached from `index.md` or a map of content.
4. Find duplicate pages, overlapping concepts, pages containing multiple
   durable ideas, and contradictions between pages.
5. Check factual pages for missing, weak, inaccessible, or mismatched sources.
6. Apply all claim checks below.
7. Report findings first, ordered by severity, with page references and concise
   remediation guidance.
8. Change files only when the user requests fixes. For any repair, update dates,
   discovery links, and `log.md` as required by the workspace contract.

## Claim Checks

Flag these conditions:

* Any claim with `status: disputed`
* Missing or empty evidence
* Evidence entries missing `source`, `kind`, or `excerpt`
* Claims that conflict across pages, especially high-confidence or evergreen
  claims
* Evergreen claims whose `updated` date is more than 90 days old
* Confidence values outside `0.0` through `1.0`
* Status values other than `provisional`, `evergreen`, or `disputed`
* Duplicate claim IDs within a page
* Evidence paths that do not resolve

## Severity Guide

| Severity | Use |
| --- | --- |
| High | Data loss risk, publication boundary breach, or materially false guidance |
| Medium | Broken discovery, contradictory claims, invalid metadata, or unsupported important assertions |
| Low | Staleness, weak linking, naming drift, or maintainability concerns |

## Failure Handling

* Distinguish confirmed defects from heuristic findings requiring review.
* Do not call a page orphaned until both wikilinks and Markdown links have been
  considered.
* Do not resolve contradictions by deleting evidence or silently choosing one
  source.
* If the audit cannot cover the full vault, state the completed scope and gaps.

> Brought to you by lagimik/AgenticPartnerCrucible