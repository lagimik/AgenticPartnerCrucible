---
name: vault-curate-web
description: "Curates public Partner Crucible web content. Use for updating solution area, industry, or special-topic pages in 100-Crucible. - Brought to you by lagimik/AgenticPartnerCrucible"
---

# Vault Web Curation

## Overview

Curate sourced wiki knowledge into the public `100-Crucible/` web layer while
preserving each page's established structure and publication boundaries.

## Prerequisites

* User direction to curate or update public web content
* Relevant public sources or already distilled wiki pages

## Quick Start

Choose the narrowest relevant web page, verify that the material is suitable
for publication, preserve the page's format, and record the curation.

## Workflow

1. Identify the applicable solution area, industry vertical, or special topic.
2. Locate the existing page in `100-Crucible/`. Create a new page only when no
   current page owns the topic.
3. Verify that every proposed source is public and appropriate for external
   publication. Exclude private, protected, confidential, and internal-only
   material.
4. Read the target page and nearby examples to preserve its frontmatter,
   structure, table conventions, and editorial style.
5. Add or refresh concise content, wiki links, public learning resources, and
   access requirements where relevant.
6. Use paths relative to `100-Crucible/` for links back to wiki pages.
7. Update the page's date metadata when the existing format provides it.
8. Check links and confirm that no content from `raw/` is exposed directly.
9. Add one dated `curate` entry to `log.md` naming the web page and sources.
10. Report the pages changed, sources published, and any material withheld from
    publication.

## Failure Handling

* If publication rights or source visibility are unclear, do not publish the
  material and ask for direction.
* If multiple pages could own the content, prefer the most specific existing
  page and link from broader pages only when useful.
* If a target page uses a legacy format, preserve it unless the user requested
  a migration.

> Brought to you by lagimik/AgenticPartnerCrucible