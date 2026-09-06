---
description: "Required schema and authoring rules for vault wiki pages"
applyTo: '00-Inbox/**/*.md,10-Notes/**/*.md,20-Projects/**/*.md,30-Areas/**/*.md,40-Resources/**/*.md,50-Archive/**/*.md'
---

# Wiki Page Instructions

Apply these rules to pages in the wiki layer. They do not define the separate
format used by `AGENTS.md`, `index.md`, `log.md`, or `100-Crucible/` pages.

## Required Frontmatter

Every wiki page starts with this YAML structure:

```yaml
---
title: Page Title
type: entity | concept | project | area | resource | moc | inbox | archive
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []
sources: []
status: draft | active | stale | archived
---
```

Use ISO 8601 dates. Preserve `created` after initial creation and change
`updated` only after a meaningful edit.

| Field | Requirement |
| --- | --- |
| `title` | Human-readable page title |
| `type` | Page category matching its purpose and location |
| `created` | Date the page was created |
| `updated` | Date the page was last meaningfully changed |
| `tags` | Short topical terms used for discovery |
| `sources` | Raw paths, public URLs, or durable references supporting the page |
| `status` | Lifecycle state: `draft`, `active`, `stale`, or `archived` |

## Page Types

| Type | Location | Use |
| --- | --- | --- |
| `entity` | `10-Notes/entities/` | A person, organization, product, place, system, partner, platform, or named thing |
| `concept` | `10-Notes/concepts/` | A reusable idea, framework, term, mental model, or pattern |
| `project` | `20-Projects/` | A time-bound effort with outcomes |
| `area` | `30-Areas/` | An ongoing responsibility or domain |
| `resource` | `40-Resources/` | Reference material worth retaining |
| `moc` | `40-Resources/` | A map linking related pages |
| `inbox` | `00-Inbox/` | An unprocessed capture |
| `archive` | `50-Archive/` | Retired or completed material |

## Optional Claims

Add a `claims` block only for assertions that are factual,
decision-relevant, likely to be reused, or likely to become stale.

```yaml
claims:
  - id: claim-001
    text: "A concise assertion supported by the cited evidence."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/YYYY-MM-DD-source/source.md
        kind: documentation
        excerpt: "A short supporting excerpt."
    captured: YYYY-MM-DD
    updated: YYYY-MM-DD
```

Each claim requires:

* An ID unique within the page, using `claim-001`, `claim-002`, and so on
* Assertion text and confidence from `0.0` through `1.0`
* A status of `provisional`, `evergreen`, or `disputed`
* At least one evidence record containing `source`, `kind`, and `excerpt`
* `captured` and `updated` dates

Use `evergreen` only when a claim is expected to remain true for a long time.
Use `provisional` for incomplete, time-bound, or interpretive evidence. Use
`disputed` when sources conflict or confidence has materially declined. Keep
evidence excerpts short and do not create claims for routine prose.