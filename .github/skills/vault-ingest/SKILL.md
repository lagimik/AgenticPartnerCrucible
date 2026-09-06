---
name: vault-ingest
description: "Ingests and connects new vault source material. Use for ingesting, importing, capturing, or processing sources. - Brought to you by lagimik/AgenticPartnerCrucible"
---

# Vault Ingest

## Overview

Preserve new source material and distill it into sourced, linked wiki pages
without altering the original input.

## Prerequisites

* Source material supplied by the user or already available in the workspace
* User direction to add or process material in the vault

## Quick Start

Identify or preserve the source under `raw/`, extract durable knowledge into
the appropriate wiki pages, update discovery links, and record the operation.

## Workflow

1. Identify the source, its provenance, and the date captured.
2. If the source is not under `raw/`, preserve it in a descriptive dated path.
   Never overwrite an existing raw file; choose a distinct path when needed.
3. Read the source and distinguish direct evidence from interpretation.
4. Create a concise source summary in the most relevant resource or wiki page.
5. Create or update entity pages for named people, organizations, products,
   places, platforms, and systems.
6. Create or update concept pages for reusable ideas, patterns, frameworks,
   definitions, and methods.
7. Update relevant resources, projects, areas, or maps of content. Prefer links
   to repeating the same material across pages.
8. Update `index.md` so the new material is discoverable.
9. Add one dated `ingest` entry to `log.md` using the workspace log contract.
10. Report the source preserved, pages changed, links added, and any uncertain
    or unsupported conclusions.

## Failure Handling

* If provenance is unknown, mark it as uncertain rather than inventing it.
* If a source conflicts with an existing page, preserve both positions and
  flag the contradiction for review.
* If the material may be private or internal, keep it out of `100-Crucible/`.
* If a suitable page location is unclear, use `00-Inbox/` and state why.

> Brought to you by lagimik/AgenticPartnerCrucible