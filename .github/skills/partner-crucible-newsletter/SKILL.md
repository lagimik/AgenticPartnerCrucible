---
name: partner-crucible-newsletter
description: "Generates the weekly Generative Partner Crucible post from log.md and sourced vault changes. Use whenever asked to create, build, or refresh a Partner Crucible newsletter. - Brought to you by lagimik/AgenticPartnerCrucible"
argument-hint: "[week_ending=YYYY-MM-DD] [date_range=...] [hero_image=...]"
---

# Partner Crucible Weekly Newsletter Generator

## Overview

Generate one weekly Generative Partner Crucible post in the current house
layout. Use `log.md` as the source-of-truth change list, verify details against
referenced material, and publish only externally appropriate content.

## Prerequisites

* An active Partner Crucible vault or a user-provided vault path
* A readable `log.md`
* Existing posts under `100-Crucible/_posts/` when generating a subsequent week
* An image-generation capability when a new hero image is requested

## Quick Start

Resolve the newsletter period, review `log.md`, inspect relevant sources, group
partner-relevant highlights, and write exactly one post to:

```text
100-Crucible/_posts/<week_ending>-generative-partner-crucible-newsletter.md
```

Do not write newsletter posts to a root `_posts/` or to `Newsletter/`.

## Inputs

Resolve these values before writing the post:

| Input | Requirement |
| --- | --- |
| `week_ending` | ISO date supplied by the user or inferred from the publishing cadence |
| `log_entries` | Relevant `log.md` entries for the newsletter period, including referenced paths and sources |
| `highlights` | Partner-relevant items grouped by section, with labels, links, descriptions, source labels, and topic page slugs |
| `thumbnail_source_file` | Source page filename used in the frontmatter thumbnail path |
| `section_images` | Optional map of section marker images |
| `hero_image` | Optional local image concept, alt text, and asset filename |

Explicit user values override inferred values. If `week_ending` is absent, use
the most recent Friday on or before the current date. Use the prior newsletter
date as the exclusive start of the review period and `week_ending` as its
inclusive end. Do not overwrite an existing post unless the user asks to
refresh it.

## Source Review Workflow

1. Locate the vault from the user-provided path or active workspace.
2. Read `log.md` before selecting newsletter content.
3. Find the most recent existing Generative Partner Crucible post and resolve
   the newsletter period using the input rules.
4. Select `log.md` entries after the prior newsletter date through
   `week_ending`. Treat them as the authoritative list of vault changes.
5. Exclude administrative changes, prior newsletter-generation entries, and
   changes without useful public partner relevance.
6. For each candidate, inspect the referenced resource, raw capture,
   concept or entity note, public URL metadata, or curated page as needed.
7. Verify factual titles, canonical URLs, descriptions, source labels, access
   requirements, and partner relevance. Do not publish private, protected,
   confidential, or internal-only material.
8. Deduplicate highlights that appear in multiple log entries or pages.
9. Group the results in the canonical section order. Do not use file modified
   timestamps as a substitute for `log.md` when the log is available.

## Canonical Section Order

Use this order unless the user explicitly overrides it:

1. Industry Insights
2. Cloud and AI Platform
3. AI Business Solutions
4. Security

Include sections that have relevant highlights. Do not invent material to fill
an empty category. Every included section must follow the exact structure below.

## Output Format

Keep frontmatter keys in this exact order:

```yaml
---
title: Generative Partner Crucible - for the week ending <week_ending>
date: <week_ending>
flag: GenerativePartnerCrucible
layout: generativepartnercrucible
thumbnail: /AgenticPartnerCrucible/assets/images/<week_ending>-<thumbnail_source_file>-image.png
---
```

If a hero image is present, place it immediately after the frontmatter and
before the first section:

```markdown
![<alt text>](/AgenticPartnerCrucible/assets/images/<week_ending>-<topic-or-section>-hero.png)
```

Render each included section exactly as follows:

```markdown
# <Section Name>

## What's new?

* <Relevant emoji> <Short highlight label>

## Deep links

* [<title>](<url>): <factual, partner-relevant description> (<source_label>)

Visit the extended Partner Crucible page on this [Topic Page](https://lagimik.github.io/AgenticPartnerCrucible/<topic_page_slug>) for more partner resources.
```

Use one blank line between blocks. Start every `What's new?` bullet with one
topic-relevant emoji followed by a space, then a concise, scannable label. Vary
emoji when practical and do not use emoji in deep-link bullets. Do not add
headings, introductions, conclusions, or commentary outside this structure. If
an included section has no deep links, retain the `## Deep links` heading with
no bullets and still add the Topic Page sentence.

## Images

Store generated images under `100-Crucible/assets/images/`. Use PNG, a 16:9
aspect ratio, and approximately `400x225` pixels unless the user requests
otherwise. Do not hotlink an external image.

Use this filename for a generated hero unless the user supplies one:

```text
<week_ending>-<topic-or-section>-hero.png
```

For AI platform topics, the default treatment is a photorealistic cityscape
expressing AI experiments, research threads, technical solutions, and paths to
production. Use accurate alt text that describes the resulting image.

Optional section markers use the configured site base path:

```markdown
![<SourceFile>.md](/AgenticPartnerCrucible/assets/images/<week_ending>-<SourceFile>.md-image.png)
```

Add an image reference only after confirming the local PNG exists. If image
generation is unavailable, omit the image and report the validation issue.

## Validation Checklist

Before completing the task, verify:

* `log.md` informed the selected highlights for the resolved period
* Referenced files or URLs support each factual title and description
* The post exists under `100-Crucible/_posts/`, not another newsletter folder
* The filename and frontmatter dates match `week_ending`
* Frontmatter contains the five required keys in the exact order
* Included sections follow the canonical order
* Every included section has `## What's new?` and `## Deep links`
* Every `What's new?` bullet starts with one topic-relevant emoji and a space
* Every included section ends with the exact Topic Page sentence
* Each deep link follows `[Title](URL): description (Source)`
* Every referenced thumbnail, marker, or hero asset exists locally
* Image references use the `/AgenticPartnerCrucible/assets/images/` site path
* No private, protected, confidential, or internal-only content is published
* One `create` or `update` entry records the newsletter in `log.md`

## Failure Handling

* If `log.md` is absent, stop and ask for a source-of-truth change list.
* If no prior post exists, use the user-provided range or ask for the first
  newsletter period.
* If the resolved post already exists, do not overwrite it without explicit
  refresh instructions.
* If a source cannot be verified, omit the item and report it.
* If no qualifying highlights exist, do not fabricate a newsletter. Report the
  empty period instead.
* If an asset path does not resolve, omit its Markdown reference or generate the
  requested local asset before writing the post.

## Response Format

Return only the created or updated post path followed by validation issues. Use
`Validation issues: none` when every check passes.

> Brought to you by lagimik/AgenticPartnerCrucible