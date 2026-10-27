---
name: partner-crucible-signal
description: "Scans configured RSS, Atom, and Microsoft Release Communications MCP sources for new Microsoft partner delivery signals. Use this skill whenever asked for Partner Crucible signal reports or scans, including Azure Updates and Microsoft 365 Roadmap signals. - Brought to you by lagimik/AgenticPartnerCrucible"
argument-hint: "[source_json=path] [report_date=YYYY-MM-DD]"
---

# Partner Crucible Signal

## Overview

Scan configured RSS, Atom, and MCP sources for recent announcements that help Microsoft
system integrators, consultants, advisors, managed service providers, and
implementation partners identify opportunities, build services, guide
adoption, or prepare executive conversations.

## Prerequisites

* An active Partner Crucible workspace
* A workspace-root `SOURCES.md` that identifies the source JSON file
* A source JSON file containing RSS or Atom feed URLs and/or `mcp_sources`
* Network access to the configured sources and announcement metadata
* For Microsoft Release Communications, public read-only Streamable HTTP access;
  no authentication was required when verified on 2026-10-24

## Quick Start

Read `SOURCES.md`, resolve its source JSON file, query every configured source,
and create this report using the runtime-provided current date:

```text
raw/partner-crucible-signal-history/rss-partner-signal-YYYY-MM-DD.md
```

Do not invent, supplement, or substitute sources. Do not overwrite an
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
only entries with an explicit RSS or Atom URL as feeds. Parse `mcp_sources`
separately: each entry declares `name`, `url`, `transport`, and `collections`.
The supported Release Communications transport is `streamable-http`; collection
names are `azure_updates` and `m365_roadmap`. Do not interpret an MCP endpoint as
RSS or infer new endpoints from unrelated URLs.

## Required Workflow

1. Read workspace-root `SOURCES.md` and identify the source JSON file it
   declares. If the file is missing, ambiguous, or invalid, stop without
   creating a report and state the configuration problem.
2. Parse the source JSON with a structured JSON parser. Extract every declared
   RSS or Atom feed URL and its source name when present, plus every declared
   MCP endpoint and collection. Do not infer sources from unrelated URLs.
3. Resolve `report_date` and the inclusive seven-day window ending on that
   date.
4. Read all prior
   `raw/partner-crucible-signal-history/rss-partner-signal-*.md` reports.
   Exclude the output file for `report_date` if it already exists.
5. Extract prior article links and normalize each link by removing its query
   string and fragment, trimming trailing slashes, lowercasing the host, and
   preserving the path. Extract stable item IDs from identity-bearing release
   links before removing query strings; compare these by collection and ID
   instead of collapsing distinct roadmap or update items onto one landing
   page. Preserve the URL scheme unless resolving an otherwise exact HTTP and
   HTTPS duplicate.
   Apply the same collection-and-ID identity to roadmap RSS links using
   `?id=<id>` so different items remain distinct and RSS/MCP overlaps collapse.
6. Fetch every configured feed and query every configured MCP collection.
   For Microsoft Release Communications, follow
   [the query and identity rules](references/RELEASE_COMMUNICATIONS_MCP.md).
   Follow pagination to completion; do not treat a partial collection as a
   complete scan. Continue past individual source failures and record them
   for the final response.
7. Consider entries dated within the seven-day window. Include an undated
   entry only when its title and summary clearly satisfy the selection
   criteria. Exclude entries with a known date outside the window. For MCP
   items, use post creation or modification dates, not feature availability
   or retirement dates, to determine window eligibility.
8. Normalize each candidate link with the same rules used for history. Remove
   duplicate normalized links within the run and remove links found in prior
   reports, including collection-and-ID matches. A modified date alone does
   not override historical deduplication.
9. Evaluate the remaining candidates against the selection criteria. Use the
   source title, summary, publication or modification date, status, and linked
   page metadata when needed; retrieve MCP item details when list summaries
   are truncated. Do not copy full article text.
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
description: Partner-relevant signals from configured RSS, Atom, and MCP sources
date: YYYY-MM-DD
---

## Partner Signals

| Date | Source | Article | Link | Reason this is of interest |
| --- | --- | --- | --- | --- |
| YYYY-MM-DD | Source name | Article title | [Read article](https://example.com/article) | One concise sentence describing the SI or advisory partner angle. |
```

Use the feed's source name when available; otherwise use the feed title or
hostname. For MCP items, use the configured source name plus collection, such
as `Microsoft Release Communications - Azure Updates`. Link to the public
item, never the MCP endpoint; retain identity-bearing query parameters in
report links. Format known dates as `YYYY-MM-DD` and use `Undated` when no reliable
date exists. Escape pipe characters in table cells. Each reason must be one
concise sentence grounded in the article metadata and must name the practical
partner angle. For MCP entries, explain whether the row date is post creation
or modification and keep planned availability distinct from confirmed release
status; see the reference for date labeling and public-link rules.

If no qualifying candidates remain after historical deduplication, replace the
table with:

```markdown
No new partner-relevant articles were identified from the configured sources.
```

If no relevant articles were found at all, use:

```markdown
No partner-relevant articles were identified from the configured sources.
```

Do not add previously reported links, full article text, speculative claims,
or content from unconfigured sources.

## Validation Checklist

Before completing the task, verify:

* `SOURCES.md` identified the parsed source JSON
* Every configured RSS or Atom feed was attempted
* Every configured MCP collection was attempted and all result pages retrieved
* MCP window eligibility uses post dates, not feature availability dates
* The runtime current date determined the default report date
* Known publication dates fall within the inclusive seven-day window
* Undated entries have clearly relevant titles and summaries
* Current-run links are unique after normalization
* Prior reports were checked, excluding the current output file
* Previously reported links do not appear in the new table
* MCP items are deduplicated by collection and stable item ID as well as links
* Public item links retain required identity parameters and are not MCP URLs
* The report uses the five required columns in the required order
* Every reason is one concise, actionable partner-focused sentence
* The report remains a whiteboard-level summary

## Failure Handling

* If `SOURCES.md` or its declared JSON file cannot be resolved, do not invent
  sources or create a misleading empty report.
* If the source JSON cannot be parsed or contains no supported sources, stop
  and report the issue. Feed-only configurations remain supported.
* If some feeds or MCP collections fail, complete the report from successful
  sources and list failures in the response, not in the report table.
* Treat MCP protocol errors, tool `isError` results, invalid payloads, and
  incomplete pagination as failures, not empty successful collections.
* If every source fails, do not create a misleading empty report or replace an
  existing report; report the failures.
* If an article date is malformed, treat it as undated rather than guessing.
* If article relevance cannot be supported by available metadata, omit it.

## Response Format

Return the created or updated report path, the number of feeds attempted,
the number of MCP endpoints and collections attempted, the number of new
articles selected, and any failures. Use `Feed failures: none` when every
configured feed was fetched successfully and `MCP failures: none` when every
configured collection was queried completely. Explicitly identify partial
collection results.

For a request only to add or configure a source, update the configuration,
this skill's applicable guidance, and `log.md`; verify connectivity and query
schemas without generating a report or claiming that a full scan ran.

## Post-Run Reflection

Check for missed result pages, date-field confusion, identity-link collisions,
and source failures before finishing. Propose workflow corrections only when
supported by observed behavior; do not change user-governed rules silently.

## References

| Reference | Load when |
| --- | --- |
| [Microsoft Release Communications MCP](references/RELEASE_COMMUNICATIONS_MCP.md) | A configured MCP source provides Azure Updates or Microsoft 365 Roadmap items |

> Brought to you by lagimik/AgenticPartnerCrucible