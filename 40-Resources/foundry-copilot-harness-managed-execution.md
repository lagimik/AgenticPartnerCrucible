---
title: Microsoft Copilot Harness in Foundry Agent Service
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-foundry, copilot-harness, agents, execution, preview]
sources:
  - https://devblogs.microsoft.com/foundry/microsoft-copilot-harness-in-foundry/
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Microsoft Copilot Harness in Foundry Agent Service

The [October 28 announcement](https://devblogs.microsoft.com/foundry/microsoft-copilot-harness-in-foundry/)
introduces the Microsoft Copilot harness for Foundry prompt agents in **public
preview**. Microsoft's managed loop and sandbox coordinate skills, supported
tools, files, execution, and bounded delegation.

## Source Summary

Teams supply instructions, knowledge, reusable skills, tool connections, and a
supported model while Foundry manages the harness. Definitions and supporting
resources can be source-controlled; portal, azd, and developer-tool experiences
provide different authoring paths.

Choose among ordinary prompt agents, prompt agents with the managed Copilot
harness, and hosted agents when custom runtime ownership is necessary.
Existing agents are unchanged; the preview requires harness selection at agent
creation and does not yet support switching it afterward. Supported models,
regions, tools, authentication, and approval settings must be checked.

## Separate Resilience and Billing Claims

Hosted-agent long-running resilience is separately announced as GA, not proof
that the Copilot harness is GA. Foundry can restart work with its original
input, but application code must checkpoint progress and prevent duplicate
external actions. Conversation history alone does not restore work in progress.

Harness runtime consumption billing is scheduled to begin **December 1, 2026**.
The announcement's pre-December runtime waiver excludes model inference and
separately billed tools or connected services; it is not a free-agent promise.
Check current pricing and contract terms rather than embedding a lasting price
assumption in a service offer.

**Partner interpretation:** pilot reusable evidence-backed workflows with
explicit tool permissions, evaluations, approval boundaries, and measured cost;
select hosted agents only when custom execution behavior is required.

## Related

- [Foundry agent selection](microsoft-foundry-agent-selection.md)
- [Copilot Studio harness selection](copilot-studio-harness-selection.md)
- [Agent recovery engineering](../10-Notes/concepts/agent-recovery-engineering.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
