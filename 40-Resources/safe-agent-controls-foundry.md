---
title: SAFE Agent Controls on Microsoft Foundry
type: resource
created: 2026-08-21
updated: 2026-08-21
tags:
  - microsoft-foundry
  - agent-security
  - policy-as-code
  - runtime-controls
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/build-a-safe-agent-on-microsoft-foundry/4547570
  - https://github.com/placerda/safe-agent-on-foundry
  - raw/2026-08-21-github-open-issues-55-63/issues.md
status: active
---

# SAFE Agent Controls on Microsoft Foundry

The SAFE pattern places deterministic runtime policy around a Foundry-hosted help-desk agent so changing or weakening the prompt cannot expand the agent's authority.

## SAFE Principles

1. **Scope** limits supported cases, tools, and action parameters.
2. **Anchored Decisions** requires host-verified evidence before consequential actions.
3. **Flow Integrity** proves required diagnostic steps occurred in the expected order.
4. **Escalation** enforces the correct human handoff and blocks completion when a required ticket does not exist.

## Enforcement Architecture

The host signs evidence envelopes, exposes only opaque evidence references to the model, verifies stage and audience, and evaluates Rego policy through Agent Control Specification middleware. Output-time controls catch missing escalations, and any bounded host repair must pass through the same protected tool path.

## Key Insight

Prompts guide behavior; deterministic controls authorize actions. Production agents need both.

## Related Pages

- [[ai-governance]]
- [[ai-agent-lifecycle]]
- [[reliable-agent-recovery-foundry]]
