---
name: vault-query
description: "Answers questions from indexed vault knowledge. Use for vault searches, synthesis, source checks, and Second Brain queries. - Brought to you by lagimik/AgenticPartnerCrucible"
---

# Vault Query

## Overview

Answer questions from the vault with traceable sources and explicit uncertainty.
Queries are read-only unless the user requests or approves an update.

## Prerequisites

* A question that can be answered from the vault
* Access to `index.md` and relevant linked pages

## Quick Start

Start at `index.md`, follow the most relevant links, inspect cited evidence when
precision matters, and return a sourced synthesis without changing files.

## Workflow

1. Read `index.md` to identify the most relevant maps, resources, entities,
   concepts, projects, or areas.
2. Follow the smallest useful set of links into the wiki.
3. Inspect cited raw material or external sources when the answer depends on
   precise wording, dates, disputed claims, or potentially stale facts.
4. Separate sourced facts, interpretation, and unresolved uncertainty.
5. Answer the question directly and cite the supporting workspace pages.
6. Do not edit the vault unless the user explicitly requests or approves
   filing the result.
7. When an update is authorized, edit the appropriate wiki page, add discovery
   links, update `index.md` when needed, and append a `query` or `update` entry
   to `log.md`.

## Failure Handling

* If the index contains a broken link, search for the intended page and report
  the broken reference if no target exists.
* If evidence is missing, say what is unsupported and avoid inferring a fact.
* If sources conflict, present the conflict and identify each source.
* If a claim is time-sensitive, include the source date or last review date.

> Brought to you by lagimik/AgenticPartnerCrucible