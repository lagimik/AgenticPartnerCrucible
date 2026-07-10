Platform AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start EXPLORE Why GitHub Documentation Blog Changelog Marketplace View all features

AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools

GitHub Copilot Write better code with AI

GitHub Copilot app Direct agents from issue to merge

MCP Registry New Integrate external tools

DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes

Actions Automate any workflow

Codespaces Instant dev environments

Issues Plan and track work

Code Review Manage code changes

APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start

GitHub Advanced Security Find and fix vulnerabilities

Code security Secure your code as you build

Secret protection Stop leaks before they start

EXPLORE Why GitHub Documentation Blog Changelog Marketplace

Solutions BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries View all solutions

BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits

Small and medium teams

BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases

BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries

Resources EXPLORE BY TOPIC AI Software Development DevOps Security View all topics EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners View all resources

EXPLORE BY TOPIC AI Software Development DevOps Security View all topics

Software Development

EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills

SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners

Open Source COMMUNITY GitHub Sponsors Fund open source developers PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program REPOSITORIES Topics Trending Collections

COMMUNITY GitHub Sponsors Fund open source developers

GitHub Sponsors Fund open source developers

PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program

Maintainer Community

REPOSITORIES Topics Trending Collections

Enterprise ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform

Enterprise platform AI-powered developer platform

AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

GitHub Advanced Security Enterprise-grade security features

Copilot for Business Enterprise-grade AI features

Premium Support Enterprise-grade 24/7 support

Search code, repositories, users, issues, pull requests...

We read every piece of feedback, and take your input very seriously.

Use saved searches to filter your results more quickly

To see all available qualifiers, see our documentation .

Notifications You must be signed in to change notification settings

Security and quality 0

Security and quality

andreaswasita/copilot-agents-dojo

Repository files navigation

Copilot Agents Dojo 🏯

A discipline framework for your GitHub Copilot agents.

End-to-end framework to take AI agents from improvised assistants to disciplined, measurable, repeatable engineering partners.

📖 Wiki · Start Here · 🥋 Belt Quest · Skills · Agents · Spec · Contributor Guide

Your AI agents are untrained. Time to put them through the dojo.

A skills & discipline framework for GitHub Copilot agents — for the engineers who build with Copilot every day to plan, code, test, review, ship, and learn alongside autonomous tooling.

Where the Copilot Cowork Dojo trains AI coworkers for knowledge work, this dojo trains AI builders : software engineers, architects, TPMs, security engineers, and test engineers running Copilot in their IDE, terminal, and CI.

Drop skills/ + optional-skills/ + .github/copilot-instructions.md into any repo → Copilot agents auto-discover the index and follow the workflow. Run bash scripts/verify.sh as the single gate in CI or pre-PR.

32 production skills across core / practical / optional tiers (28 always-discoverable + 4 optional) — see the auto-generated skills.md index for the canonical list

8 specialized agent personas — generalist architect , three TOGAF specialists (business / solution / platform), plus security-engineer , software-engineer , technical-program-manager , test-engineer

Mandatory BRAINSTORM → PLAN → TDD → REVIEW → FINISH pipeline

Self-improving curator — state machine, backups, idle-based trigger, per-run audit trail

Memory vault — persistent, linked knowledge graph (Obsidian-compatible)

MCP memory server — any MCP-capable agent can read/write the vault

Git worktree isolation + cache-aware skill amendments

Single enforcement gate: scripts/verify.sh (+ GitHub Actions)

The Mandatory Workflow

Every non-trivial task follows this pipeline — no skipping, no improvising:

One command runs the whole sprint. In Copilot Chat, /dojo-sprint <goal> walks every phase above in order; /dojo-swarm <goal> does the same but fans EXECUTE + TEST out to parallel sub-agents. Both are driven by scripts/sprint.sh , whose phase→skill map is the single source of truth in scripts/pipeline.tsv :

New to the Dojo? Train interactively. The Belt Quest is a gamified, self-contained onboarding that takes you from 白帯 white belt to 黒帯 black belt — install the framework, drill the core kata, walk the mandatory workflow, and reach mastery.

A winding stone path of 23 checkpoints , each with copy-ready commands and a "stuck?" hint. Progress is saved locally, belts unlock in sequence, and finishing the path earns a downloadable black-belt certificate . No build step, no dependencies — one static HTML file.

Play it: publish via GitHub Pages ( Settings → Pages → Deploy from branch → main / /docs ), then open …github.io/copilot-agents-dojo/quests/ . Or open docs/quests/index.html directly in a browser.

skills/ — Core + practical skill folders (always discoverable)

optional-skills/ — Heavy / niche skills (installed explicitly)

agents/ — Persona briefs + agents/registry.yaml

skills.md — Master index — generated, auto-discovered by Copilot

spec/ — The Copilot Skills specification (v1)

template/ — Starter template for creating new skills

Always loaded. Behavioral skills that govern how agents think. Style-agnostic.

Skills that orchestrate the mandatory pipeline.

Practical Kumite — 実践組手

Task-specific skills for the most common engineering work.

Optional Skills — 選択

Heavyweight or niche. Installed explicitly from optional-skills/ .

Specialized Agent Personas

Personas in agents/ , with a single source of truth in agents/registry.yaml . scripts/verify.sh blocks drift between the registry and the briefs.

Single Gate, Single Sources of Truth

scripts/verify.sh is the only enforcement entry point. Four modes: spec (default), plan , tests , all .

If any source of truth changes, the gate either auto-regenerates the artifact or fails loudly. No silent drift.

Everything in scripts/ honors ${DOJO_ROOT:-…} so it works from any cwd and supports multi-instance profiles.

Every skill and persona is also exposed as a discoverable GitHub Copilot slash command . scripts/regen-prompts.sh generates one prompt shim per skill and per agent under .github/prompts/ , so in Copilot Chat you can type:

The shims are auto-generated (never hand-edited) and kept in sync by the same gate as skills.md : verify.sh warns on drift and tests/test_prompts.py fails CI if they are stale. The two pipeline shims ( /dojo-sprint , /dojo-swarm ) are generated from scripts/pipeline.tsv . Regenerate after adding or renaming a skill or persona:

bash (Git for Windows works on Windows hosts) and standard POSIX tools.

jq — used by curator.sh and lesson-updater.sh . On Windows: winget install jqlang.jq .

Python 3.10+ (optional) for the cli/dojo_cli/ CLI and --profile multi-instance support.

scripts/curator.sh reads .dojo/skill-usage.json (gitignored), enforces an active → stale → archived lifecycle, and writes per-run reports + tarball backups. v1.1 ports the hermes-agent self-improvement pattern without adding a daemon.

Idle-based trigger (hermes-style — fires only when the agent is quiet):

Wire it into your shell init, a pre-commit hook, or a scheduled task. Knobs live in .dojo/curator.env ( DOJO_CURATOR_STALE_DAYS , DOJO_CURATOR_ARCHIVE_DAYS , DOJO_CURATOR_INTERVAL_HOURS , DOJO_CURATOR_MIN_IDLE_HOURS , DOJO_CURATOR_BACKUP_KEEP , DOJO_CURATOR_REPORT_KEEP ).

Three-layer provenance guard. Bundled skills can never be auto-archived. Three checks, any of which exempts a skill from every auto-transition:

created_by: human in the SKILL.md frontmatter.

Folder name in .dojo/bundled-manifest.txt (regenerated whenever you run regen-skills-index.sh ).

pinned: true in the usage sidecar ( bash scripts/curator.sh pin <name> ).

Only agent-authored, unpinned, un-bundled skills can ever reach archived — and even then, "archived" means moved to skills/.archive/ , never deleted, and restorable via curator.sh restore <name> or rollback <stamp> .

Cache-Aware Self-Improvement

Mutating skills.md or any SKILL.md mid-session invalidates Copilot's prompt cache. The dojo defends against this:

scripts/lesson-updater.sh (no flag) writes proposed amendments to .dojo/pending-amendments.md . Apply them at session boundaries.

scripts/lesson-updater.sh --now applies immediately but prints a loud warning that the cache is being blown.

Multi-Instance Profiles

Working on several projects concurrently? Each profile gets its own skills/ , tasks/ , .dojo/ under ~/.dojo/profiles/<name>/ :

DOJO_ROOT is exported automatically so every shell script and the verify.sh gate operate on the right root.

The memory/ directory is the agent's persistent knowledge graph — structured, linked, and queryable. It replaces flat-file memory with the capabilities that make tools like Obsidian powerful, implemented as plain markdown + scripts any agent can use.

Observe — After every correction, log a structured lesson in tasks/lessons.md with YAML tags (error type, root cause, fix, rule).

Store — Lessons are tagged and queryable. Metrics track total lessons, recurring patterns, and amendment rate.

Promote — When a pattern hits 3+ occurrences, scripts/obsidian-sync.sh promotes it to memory/patterns/ as a proven rule.

Decide — Architectural choices are recorded in memory/decisions/ with context, alternatives, and consequences.

Learn — User preferences accumulate in memory/preferences/ with confidence levels that grow over time.

Link — scripts/link-index.sh rebuilds the knowledge graph — backlinks, forward links, and memory/.link-graph.json .

Query — Agents search memory with scripts/memory-query.sh instead of re-reading every file.

Amend — Proven patterns feed amendments into skills.md via scripts/lesson-updater.sh .

Rollback — Failed fixes get rolled back immediately. Failed rules get revised or removed.

All files use relative markdown links (not wikilinks) and YAML frontmatter for metadata — standards any agent can parse. Zero dependencies on Obsidian or any external tool.

Obsidian compatibility

The memory/ directory is also a real Obsidian vault . Open the folder in Obsidian and the native graph view + backlinks pane just work — color groups match the Control Plane theme (decisions cyan, patterns indigo, preferences amber, sessions emerald). See memory/README.md for details.

Any MCP-capable agent (Claude Code, Copilot CLI, Cursor, VS Code) can read and write the vault via tool calls. The @dojo/mcp-memory package exposes:

10 tools — memory_list , memory_search , memory_get , memory_create , memory_link , memory_supersede , memory_history , memory_recent_sessions , memory_decisions_active , memory_patterns_for_context

2 resource types — memory://INDEX (the Map of Content) and memory://{type}/{slug} (one resource per entry)

Session auto-resume — installed copilot-instructions.md instructs agents to call memory_recent_sessions + memory_decisions_active on startup and memory_create({type:'session'}) on completion

Install the Control Plane's MCP wiring with the 🔌 Wire MCP memory server toggle on the Install page, or copy a sample config from control-plane/packages/mcp-memory/examples/ . Full reference: docs/memory-mcp.md .

The Control Plane exposes git history as a first-class UI. On any memory entry, click 🕰 Time Machine to scrub commits, preview a prior version, and restore it (auto-commits with audit trail). The Memory Browser also has a vault-wide 🕰 Time Slider that filters cards + graph to the vault state at any chosen commit.

Why Train Your Agents?

Rush in without a plan — all offense, no strategy

Never learn from their losses

Throw sloppy patches instead of finding the root cause

Declare victory without proof

Flood the context window like an undisciplined sparring partner

Trained agents operate like seasoned black belts — plan the approach, execute with precision, verify the outcome, learn from every round.

🥋 New here? Walk the Belt Quest first — the gamified onboarding ( see above ). Prefer to dive straight in? Install below.

One command (recommended)

Drop the whole framework into the current repo — no clone, no Python:

The installer is re-runnable and idempotent : it refreshes the bundled skills, agents, scripts, and spec while preserving your own additions — tasks/ , memory/ , custom skills, and an edited .github/copilot-instructions.md (a differing dojo version is written to .github/copilot-instructions.dojo.md for you to merge). It finishes by running scripts/verify.sh spec as a health gate.

Pin a release for reproducible installs, and pass options as needed:

Install as a Copilot CLI plugin

If you live in the GitHub Copilot CLI , the dojo ships as a plugin you can install from its built-in marketplace — the 28 core skills land in your Copilot CLI, no repo files required:

Verify and manage it like any other plugin:

The plugin scope is the core discipline skills ( skills/ ). The optional tiers ( optional-skills/ ) stay opt-in and are delivered through the installer or manual setup above — keeping the dojo's "core always, optional by choice" contract intact.

Prefer to wire it up by hand? The steps the installer automates are:

Copy skills/ and optional-skills/ into your repo — or pick the individual tiers you need.

Copy memory/ — the persistent knowledge graph.

Place skills.md at your repo root — Copilot agents auto-discover this index.

Place .github/copilot-instructions.md in your .github/ folder — customize for your stack.

Run bash scripts/init.sh — scaffolds tasks/todo.md and tasks/lessons.md .

Run bash scripts/regen-skills-index.sh — rebuilds skills.md and primes .dojo/bundled-manifest.txt .

Run bash scripts/link-index.sh — initializes the memory vault graph.

Run bash scripts/verify.sh spec — confirms the skill index, personas, and scripts are wired correctly.

Author your own skills from template/SKILL.md — guidance lives in optional-skills/writing-skills .

Upgrading from pre-v1? Run bash scripts/migrate-v1.sh for the idempotent migration helper.

Choose Your Fighting Style

The Code Standards in copilot-instructions.md ship with examples for multiple stacks. Pick your style. Delete the others. The disciplines are style-agnostic .

📘 TypeScript — strict mode, Vitest, Tailwind, Next.js App Router

🐍 Python — pytest, Black, type hints, FastAPI / Django

☕ Java — JUnit 5, Spring Boot, Maven / Gradle

🐹 Go — standard library, table-driven tests

🛡️ .NET — xUnit, clean architecture, nullable reference types

The Copilot Agents Dojo distills field-tested patterns from shipping production code with AI agents — watching them fail, and figuring out what actually makes them reliable:

Field experience — Real-world agent sessions exposing failure modes: rushing without plans, skipping verification, repeating the same mistakes, flooding the context window. Every core kata exists because an agent failed without it.

hermes-agent — The reference build for spec v1, the curator pattern (state machine, backups, idle trigger), durable boards, and the registry-driven CLI.

Copilot Cowork Dojo — The sibling project for AI coworkers ; this one trains AI builders .

obra/superpowers — The mandatory orchestration pipeline (BRAINSTORM → WORKTREE → … → LEARN) proving disciplined agents outperform freestyle ones.

Anthropic Claude — Structured prompting, progressive disclosure, explicit verification gates.

See AGENTS.md for the contributor guide and CONTRIBUTING.md for the high-level checklist. Keep contributions on-brand with the brand & style guide — palette, wordmark, voice/tone. Changelog: CHANGELOG.md .

A behavioral governance framework for GitHub Copilot agents — skills.md and instructions to make AI coding agents think like senior engineers.

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information