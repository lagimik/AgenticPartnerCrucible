# AGENTS.md

This vault is an LLM-maintained Second Brain: a personal wiki where raw material is preserved, useful knowledge is distilled into durable pages, and structure is maintained over time.

The assistant should act as a careful wiki gardener: ingest new material, summarize it, connect it, cite it, and keep the vault navigable.

## 1. Three Layers

The vault has three knowledge layers.

### Raw Layer

**Location:** `raw/`

**Owner:** User owns the source material. The assistant may read, summarize, reference, and organize pointers to it, but must not delete or overwrite raw files.

**Purpose:** Preserve original inputs exactly as received: transcripts, pasted notes, exported documents, meeting notes, chat logs, articles, drafts, screenshots, and other source material.

### Wiki Layer

**Locations:**

- `00-Inbox/`
- `10-Notes/entities/`
- `10-Notes/concepts/`
- `20-Projects/`
- `30-Areas/`
- `40-Resources/`
- `50-Archive/`
- `_meta/MOCs/`

**Owner:** Assistant maintains the wiki layer with user direction.

**Purpose:** Turn raw material into useful, linked, readable knowledge pages. This is the working Second Brain.

### Schema Layer

**Locations:**

- `AGENTS.md`
- `_meta/conventions.md`
- `_meta/templates/`
- `index.md`
- `log.md`

**Owner:** User defines intent and rules. Assistant follows and proposes changes when patterns need to evolve.

**Purpose:** Define how the vault works: folder rules, page types, frontmatter, naming conventions, logs, indexes, and maintenance operations.

## 2. Folder Conventions and Naming Rules

Use folders consistently.

| Folder | Purpose |
| --- | --- |
| `raw/` | Immutable source material. Never delete from here. |
| `00-Inbox/` | Temporary holding area for unprocessed notes and captures. |
| `10-Notes/entities/` | People, organizations, products, places, systems, partners, and named things. |
| `10-Notes/concepts/` | Ideas, patterns, frameworks, definitions, methods, and reusable insights. |
| `20-Projects/` | Active efforts with outcomes, milestones, decisions, and tasks. |
| `30-Areas/` | Ongoing responsibilities with no fixed end date. |
| `40-Resources/` | Reference material organized for reuse. |
| `50-Archive/` | Completed, inactive, superseded, or retired wiki pages. |
| `_meta/` | Vault operating rules, templates, maps of content, and maintenance notes. |

Naming rules:

- Use clear, descriptive filenames.
- Prefer lowercase kebab-case for new files: `partner-channel-strategy.md`.
- Entity pages may use proper names when readability matters: `Microsoft.md`, `Contoso.md`, `Jane-Doe.md`.
- Avoid vague filenames such as `notes.md`, `misc.md`, `thoughts.md`, or `new.md`.
- One page should represent one durable idea, entity, project, area, or resource.
- If a page grows into multiple ideas, split it and link the pieces.
- Use relative links between wiki pages.

## 3. Page Types and Required YAML Frontmatter

Every wiki page should start with YAML frontmatter.

Required fields:

```yaml
---
title: Page Title
type: entity | concept | project | area | resource | moc | inbox | archive | log | meta
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []
sources: []
status: draft | active | stale | archived
---
```

Field meanings:

| Field | Meaning |
| --- | --- |
| `title` | Human-readable page title. |
| `type` | Page category. Must match the purpose of the page. |
| `created` | Date the page was first created. |
| `updated` | Date the page was last meaningfully changed. |
| `tags` | Short topical tags for discovery. |
| `sources` | Raw files, URLs, emails, meetings, or other references used to support the page. |
| `status` | Lifecycle state of the page. |

Common page types:

| Type | Location | Use |
| --- | --- | --- |
| `entity` | `10-Notes/entities/` | A person, company, product, team, partner, platform, system, or named thing. |
| `concept` | `10-Notes/concepts/` | A reusable idea, framework, term, mental model, or pattern. |
| `project` | `20-Projects/` | A time-bound effort with outcomes. |
| `area` | `30-Areas/` | An ongoing responsibility or domain. |
| `resource` | `40-Resources/` | Reference material worth keeping. |
| `moc` | `_meta/MOCs/` | Map of Content that links related pages. |
| `inbox` | `00-Inbox/` | Unprocessed capture. |
| `archive` | `50-Archive/` | Retired or completed material. |
| `meta` | `_meta/` | Operating documentation for the vault. |

## 4. Operations

### Ingest

Use this flow when new source material is added.

1. Store or identify the source in `raw/`.
2. Create a concise summary of the source.
3. Extract entities and update or create pages in `10-Notes/entities/`.
4. Extract concepts and update or create pages in `10-Notes/concepts/`.
5. Update relevant project, area, resource, or MOC pages.
6. Update `index.md` so the material is findable.
7. Add a dated entry to `log.md`.

Ingest pattern:

```text
raw -> summary + entity updates + concept updates + index update + log entry
```

### Query

Use this flow when answering a question from the vault.

1. Read `index.md` first.
2. Drill into the most relevant linked pages.
3. Check cited sources when precision matters.
4. Synthesize an answer with clear uncertainty markers.
5. If the answer is durable and useful, file it into the appropriate wiki page.
6. Add or update links so the answer can be found again.

Query pattern:

```text
read index -> drill -> synthesize -> file good answers
```

### Lint

Use this flow to maintain vault quality.

Check for:

- Contradictions between pages.
- Orphan pages with no inbound or outbound links.
- Stale pages whose `updated` date or status needs review.
- Missing frontmatter.
- Missing required fields.
- Missing or weak sources.
- Duplicate pages or overlapping concepts.
- Pages that violate one-idea-per-page.

Lint pattern:

```text
contradictions / orphans / stale / missing
```

## 5. Log Format

`log.md` should use greppable, dated entries.

Each entry should be one line when possible.

Format:

```text
YYYY-MM-DD | operation | target | summary | sources
```

Examples:

```text
2026-07-10 | ingest | 10-Notes/concepts/llm-maintained-wiki.md | Created concept page from Karpathy wiki pattern notes | raw/2026-07-10-karpathy-wiki-notes.md
2026-07-10 | update | index.md | Added links for entities, concepts, projects, and MOCs | AGENTS.md
2026-07-10 | lint | vault | Found 3 orphan concept pages and 1 stale project page | n/a
```

Use operation names such as:

- `ingest`
- `create`
- `update`
- `query`
- `lint`
- `archive`
- `rename`
- `merge`
- `split`

## 6. House Rules

- Keep one idea per page.
- Cite sources for claims, facts, and decisions.
- Flag uncertainty clearly instead of overstating confidence.
- Never delete from `raw/`.
- Summarize source material before filing it into the wiki.
- Preserve the difference between source material, interpretation, and decisions.
- Prefer links over duplication.
- Keep pages readable for a human, not just optimized for an LLM.
- Update `updated` dates when pages materially change.
- Keep `index.md` useful as the first place to look.
- Add a `log.md` entry for every meaningful ingest, update, lint, archive, merge, split, or query result that changes the vault.

## Optional Claims Block

Wiki pages may include an optional `claims` block in YAML frontmatter when a page contains important assertions that should be tracked over time.

Use claims for statements that are factual, decision-relevant, likely to be reused, or likely to become stale.

Example:

```yaml
claims:
  - id: claim-001
    text: "Microsoft Skills for Fabric separates work into authoring, consumption, and operations bundles."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-10-github-microsoft-skills-for-fabric/README.md
        kind: documentation
        excerpt: "Or install a focused bundle..."
    captured: 2026-07-10
    updated: 2026-07-10
```

Claim fields:

| Field | Required | Meaning |
| --- | --- | --- |
| `id` | Yes | Stable claim identifier, unique within the page. Use `claim-001`, `claim-002`, etc. |
| `text` | Yes | The assertion being tracked. |
| `confidence` | Yes | Numeric confidence from `0.0` to `1.0`. |
| `status` | Yes | `provisional`, `evergreen`, or `disputed`. |
| `evidence` | Yes | One or more supporting evidence entries. |
| `captured` | Yes | Date the claim was first recorded. |
| `updated` | Yes | Date the claim was last reviewed or changed. |

Evidence fields:

| Field | Required | Meaning |
| --- | --- | --- |
| `source` | Yes | Source path, usually `raw/<file>` or another durable source reference. |
| `kind` | Yes | `documentation`, `quote`, or `observation`. |
| `excerpt` | Yes | Short quote or note supporting the claim. |

Claim rules:

- Use `evergreen` only for claims expected to remain true for a long time.
- Use `provisional` when evidence is incomplete, current only as of a point in time, or based on interpretation.
- Use `disputed` when sources conflict or confidence has materially dropped.
- Every claim must have evidence.
- Keep excerpts short.
- Do not use claims for every sentence; track only assertions worth maintaining.

## Claims Linting

The lint operation should check claim blocks in addition to normal vault health.

Flag:

- **Disputed claims:** any claim with `status: disputed`.
- **Claims with no evidence:** missing `evidence`, empty `evidence`, or evidence entries without `source`, `kind`, or `excerpt`.
- **Contradictions across pages:** claims whose `text` conflicts with another claim, especially when both are marked `evergreen` or have high confidence.
- **Stale evergreen claims:** claims with `status: evergreen` whose `updated` date is more than 90 days old.
- **Invalid confidence:** confidence outside `0.0` to `1.0`.
- **Invalid status:** status other than `provisional`, `evergreen`, or `disputed`.
