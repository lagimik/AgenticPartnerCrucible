---
name: partner-crucible-linkedin
description: "Generates a LinkedIn post from a weekly Partner Crucible newsletter. Use for LinkedIn article or newsletter promotion copy. - Brought to you by lagimik/AgenticPartnerCrucible"
argument-hint: "[week_ending=YYYY-MM-DD] [generation_credit=...]"
---

# Partner Crucible LinkedIn Post Generator

## Overview

Generate concise, paste-ready LinkedIn copy from a completed Generative Partner
Crucible newsletter. Follow the structure and tone of the post for the week
ending September 11, 2026.

## Prerequisites

* An active Partner Crucible vault or a user-provided vault path
* A completed weekly newsletter under `100-Crucible/_posts/`

## Quick Start

Resolve the requested newsletter, extract its `What's new?` highlights, and
return one LinkedIn post in the canonical format. Do not create or update a
file unless the user explicitly asks to save the post.

## Parameters Reference

| Parameter           | Requirement                                                                      |
|---------------------|----------------------------------------------------------------------------------|
| `week_ending`       | Optional ISO date; defaults to the latest completed newsletter                   |
| `newsletter_path`   | Optional explicit newsletter path; overrides `week_ending`                       |
| `generation_credit` | Optional footer; defaults to `This edition generated with GitHub Copilot App / GPT-5.6 Medium` |

## Source Workflow

1. Use `newsletter_path` when supplied. Otherwise, find the newsletter matching
   `week_ending`, or the latest completed newsletter when no date is supplied.
2. Read only the selected newsletter. Do not rescan `log.md` or regenerate the
   newsletter unless the user requests that separate workflow.
3. Extract each included section and its `What's new?` bullets in source order.
4. Omit `Deep links`, topic-page links, frontmatter, images, and descriptions.
5. Preserve each highlight's emoji and concise wording. Make only light edits
   needed for a natural standalone LinkedIn post.
6. Render the post using the canonical format and return it without commentary,
   labels, or a fenced code block.

## Canonical Format

The post content must always begin with this exact opening. Do not place a
title, label, greeting, whitespace, or any other text before it:

```text
From the things that caught my attention, to the things you may have missed:
```

Map newsletter section headings as follows and omit empty sections:

| Newsletter section      | LinkedIn heading       |
|-------------------------|------------------------|
| Industry Insights       | Industry               |
| Cloud and AI Platform   | Cloud and AI Platform  |
| AI Business Solutions   | AI Business Solutions  |
| Security                | Security               |

Place each heading on its own line. Put each emoji highlight on its own line
beneath the heading. Separate the opening, headings, section bodies, and footer
with one blank line. Do not add bullets, Markdown headings, hyperlinks,
hashtags, a title, or a call to action.

Use `generation_credit` as the final line. When it is not supplied, use:

```text
This edition generated with GitHub Copilot App / GPT-5.6 Medium
```

## Canonical Example

For `2026-09-11`, produce:

```text
From the things that caught my attention, to the things you may have missed:

Industry

💸 FinOps for AI practices expanded

Cloud and AI Platform

🛠️ Azure Copilot Troubleshooting Agent (GA)
🔀 Project HydraFusion: GitHub Copilot research previews
🧮 The Economics of Agent Optimization
📈 AI Agent ROI Framework

AI Business Solutions

🧩 Copilot Cowork + Copilot Studio = Full-Stack Business-App

This edition generated with GitHub Copilot App / GPT-5.6 Medium
```

## Validation Checklist

Before returning the post, verify:

* The selected newsletter date matches the request
* Every included line comes from a `What's new?` highlight in that newsletter
* Sections retain newsletter order and empty sections are omitted
* `Industry Insights` is rendered as `Industry`
* Every highlight retains one topic-relevant emoji
* No deep links, Markdown syntax, title, hashtags, or extra commentary appear
* The first characters are `From the things that caught my attention, to the things you may have missed:`
* The opening and generation credit each appear exactly once

## Troubleshooting

* If no completed newsletter exists, ask the user to generate one first.
* If the requested date has no matching newsletter, report the missing path and
  list the nearest available newsletter dates.
* If a highlight lacks an emoji, add one topic-relevant emoji before rendering.
* If the model credit supplied by the user differs from the default, preserve
  the supplied text exactly.

## Response Format

Return only the paste-ready LinkedIn post.

> Brought to you by lagimik/AgenticPartnerCrucible
