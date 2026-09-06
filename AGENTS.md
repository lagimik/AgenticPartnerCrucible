# Vault Guidelines

This repository is an LLM-maintained second brain. Preserve source material,
distill durable knowledge, connect related pages, cite evidence, and keep the
vault navigable for people.

## Repository Model

| Layer | Locations | Ownership and purpose |
| --- | --- | --- |
| Raw | `raw/` | User-owned, immutable source material. Agents may read and reference it but must never delete or overwrite it. |
| Wiki | `00-Inbox/`, `10-Notes/`, `20-Projects/`, `30-Areas/`, `40-Resources/`, `50-Archive/` | Agent-maintained knowledge pages, changed with user direction. |
| Schema | `AGENTS.md`, `.github/instructions/`, `.github/skills/`, `index.md`, `log.md` | User-governed rules, workflows, indexes, and change history. |
| Web | `100-Crucible/` | Public-facing solution area, industry, and special-topic content, maintained with user direction. |

The web layer publishes through the `gh-pages` branch. Never publish the
`raw/` layer or expose private, protected, or internal-only source content.

## Hard Requirements

* Never delete or overwrite files in `raw/`.
* Summarize source material before filing derived knowledge into the wiki.
* Preserve the distinction between source material, interpretation, and
  decisions.
* Cite sources for factual claims and decisions. Mark uncertainty instead of
  overstating confidence.
* Keep one durable idea, entity, project, area, or resource per page. Split
  pages that grow beyond one subject and connect the resulting pages.
* Prefer links over duplicated content and use relative links between wiki
  pages.
* Keep pages readable for people, not only optimized for retrieval.
* Follow the scoped wiki-page instructions for frontmatter, page types, and
  optional claim records.
* Update a page's `updated` date after a meaningful change.
* Keep `index.md` useful as the starting point for vault discovery.
* Add a `log.md` entry for every meaningful operation that changes the vault.

## Folder And Naming Conventions

| Location | Content |
| --- | --- |
| `00-Inbox/` | Unprocessed notes and captures |
| `10-Notes/entities/` | People, organizations, products, places, systems, partners, and named things |
| `10-Notes/concepts/` | Ideas, patterns, frameworks, definitions, methods, and reusable insights |
| `20-Projects/` | Time-bound efforts with outcomes, milestones, decisions, and tasks |
| `30-Areas/` | Ongoing responsibilities without a fixed end date |
| `40-Resources/` | Reference material organized for reuse |
| `50-Archive/` | Completed, inactive, superseded, or retired wiki pages |
| `100-Crucible/` | Public web content for solution areas, industries, and special topics |

Use clear, descriptive filenames. Prefer lowercase kebab-case for new files,
except when a proper name improves entity-page readability. Avoid vague names
such as `notes.md`, `misc.md`, `thoughts.md`, and `new.md`.

## Workflow Routing

Load the matching workspace skill for task-specific procedures:

* Use `vault-ingest` to preserve and process new source material.
* Use `vault-query` to answer questions from indexed vault knowledge.
* Use `vault-curate-web` to update public content in `100-Crucible/`.
* Use `partner-crucible-newsletter` to generate or refresh the weekly
  Generative Partner Crucible post.
* Use `vault-lint` to audit vault structure, metadata, links, sources, and
  claims.

Vault queries are read-only by default. Change wiki pages only when the user
requests or approves filing the result.

## Log Contract

Keep each `log.md` entry on one line when possible and use this format:

```text
YYYY-MM-DD | operation | target | summary | sources
```
