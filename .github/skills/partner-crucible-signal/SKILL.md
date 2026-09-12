---
name: partner-crucible-signal
description: "Scans configured RSS and Atom feeds for new Microsoft partner delivery signals. Use for Partner Crucible signal reports. - Brought to you by lagimik/AgenticPartnerCrucible"
argument-hint: "[source_json=path] [report_date=YYYY-MM-DD]"
---

# Partner Crucible Signal

## Overview

Scan configured RSS and Atom feeds for recent articles that help Microsoft
system integrators, consultants, advisors, managed service providers, and
implementation partners identify opportunities, build services, guide
adoption, or prepare executive conversations.

## Prerequisites

* An active Partner Crucible workspace
* A workspace-root `SOURCES.md` that identifies the source JSON file
* A source JSON file containing RSS or Atom feed URLs
* Network access to the configured feeds and article metadata

## Quick Start

Read `SOURCES.md`, resolve its source JSON file, fetch every configured feed,
and create this report using the runtime-provided current date:

```text
raw/partner-crucible-signal-history/rss-partner-signal-YYYY-MM-DD.md
```

Do not invent, supplement, or substitute feed sources. Do not overwrite an
existing current-date report until its links have been excluded from historical
duplicate detection and the complete scan is ready to replace it.

## Inputs

| Input | Requirement |
| --- | --- |
| `source_json` | Source JSON path identified by `SOURCES.md`; an explicit user path may disambiguate multiple paths but must be listed in `SOURCES.md` |
| `report_date` | Runtime-provided current date unless the user explicitly requests a historical run |
| `history_reports` | All `raw/partner-crucible-signal-history/rss-partner-signal-*.md` files except the current run's output file |

Treat the runtime-provided current date as authoritative. Resolve relative
paths in `SOURCES.md` from the workspace root. Accept common JSON structures,
including arrays of feed objects or objects containing a feed array, but use
only entries with an explicit RSS or Atom URL.

## Required Workflow

1. Read workspace-root `SOURCES.md` and identify the source JSON file it
   declares. If the file is missing, ambiguous, or invalid, stop without
   creating a report and state the configuration problem.
2. Parse the source JSON with a structured JSON parser. Extract every declared
   RSS or Atom feed URL and its source name when present. Do not infer feeds
   from unrelated URLs.
3. Resolve `report_date` and the inclusive seven-day window ending on that
   date.
4. Read all prior
   `raw/partner-crucible-signal-history/rss-partner-signal-*.md` reports.
   Exclude the output file for `report_date` if it already exists.
5. Extract prior article links and normalize each link by removing its query
   string and fragment, trimming trailing slashes, lowercasing the host, and
   preserving the path. Preserve the URL scheme unless resolving an otherwise
   exact HTTP and HTTPS duplicate.
6. Fetch every configured feed. Continue past an individual feed failure and
   record the failed source for the final response.
7. Consider entries dated within the seven-day window. Include an undated
   entry only when its title and summary clearly satisfy the selection
   criteria. Exclude entries with a known date outside the window.
8. Normalize each candidate link with the same rules used for history. Remove
   duplicate normalized links within the run and remove links found in prior
   reports.
9. Evaluate the remaining candidates against the selection criteria. Use the
   feed title, summary, publication date, and linked page metadata when needed;
   do not copy full article text.
10. Sort selected articles by date descending, with undated entries last, then
    write or replace only the current run's report.
11. Validate the output filename, table columns, links, date window, and both
    levels of duplicate detection before finishing.

## Selection Criteria

Select an article only when it supports an actionable SI or advisory partner
conversation, service, or delivery motion. Prioritize:

* Microsoft Azure, AI, Copilot, Copilot Studio, Fabric, Power Platform,
  Dynamics 365, Microsoft 365, Security, and industry clouds
* New capabilities, previews, generally available releases, roadmap signals,
  licensing or packaging changes, governance, compliance, resiliency,
  migration, modernization, and operational guidance
* Assessments, workshops, migrations, implementation accelerators, managed
  services, security posture improvement, data modernization, business
  application transformation, AI governance, and change management

Exclude generic company news, consumer-only stories, event promotion without a
delivery implication, and content that does not suggest an actionable partner
conversation. When relevance is marginal, omit the article.

## Output Format

Create
`raw/partner-crucible-signal-history/rss-partner-signal-<report_date>.md` with
YAML frontmatter and this body structure:

```markdown
---
title: Partner Crucible Signal - YYYY-MM-DD
description: Partner-relevant signals from configured RSS and Atom feeds
date: YYYY-MM-DD
---

## Partner Signals

| Date | Source | Article | Link | Reason this is of interest |
| --- | --- | --- | --- | --- |
| YYYY-MM-DD | Source name | Article title | [Read article](https://example.com/article) | One concise sentence describing the SI or advisory partner angle. |
```

Use the feed's source name when available; otherwise use the feed title or
hostname. Format known dates as `YYYY-MM-DD` and use `Undated` when no reliable
date exists. Escape pipe characters in table cells. Each reason must be one
concise sentence grounded in the article metadata and must name the practical
partner angle.

If no qualifying candidates remain after historical deduplication, replace the
table with:

```markdown
No new partner-relevant articles were identified from the configured feeds.
```

If no relevant articles were found at all, use:

```markdown
No partner-relevant articles were identified from the configured feeds.
```

Do not add previously reported links, full article text, speculative claims,
or content from unconfigured sources.

## Validation Checklist

Before completing the task, verify:

* `SOURCES.md` identified the parsed source JSON
* Every configured RSS or Atom feed was attempted
* The runtime current date determined the default report date
* Known publication dates fall within the inclusive seven-day window
* Undated entries have clearly relevant titles and summaries
* Current-run links are unique after normalization
* Prior reports were checked, excluding the current output file
* Previously reported links do not appear in the new table
* The report uses the five required columns in the required order
* Every reason is one concise, actionable partner-focused sentence
* The report remains a whiteboard-level summary

## Failure Handling

* If `SOURCES.md` or its declared JSON file cannot be resolved, do not invent
  sources or create a misleading empty report.
* If the source JSON cannot be parsed or contains no RSS or Atom URLs, stop and
  report the issue.
* If some feeds fail, complete the report from successful feeds and list the
  failed sources in the response, not in the report table.
* If every feed fails, do not replace an existing report; report the failures.
* If an article date is malformed, treat it as undated rather than guessing.
* If article relevance cannot be supported by available metadata, omit it.

## Response Format

Return the created or updated report path, the number of feeds attempted, the
number of new articles selected, and any feed failures. Use `Feed failures:
none` when every configured feed was fetched successfully.

> Brought to you by lagimik/AgenticPartnerCrucible