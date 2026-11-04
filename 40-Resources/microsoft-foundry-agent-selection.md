---
title: Choosing the Right Agent in Microsoft Foundry
type: resource
created: 2026-08-21
updated: 2026-11-02
tags:
  - microsoft-foundry
  - agents
  - architecture
  - decision-guide
sources:
  - https://devblogs.microsoft.com/foundry/microsoft-copilot-harness-in-foundry/
  - https://techcommunity.microsoft.com/blog/azurearchitectureblog/choosing-the-right-agent-in-microsoft-foundry/4547827
  - raw/2026-08-21-github-open-issues-55-63/issues.md
status: active
---

# Choosing the Right Agent in Microsoft Foundry

This architecture guide distinguishes Microsoft Foundry prompt agents from hosted agents by locating ownership of orchestration, state, and operational complexity.

## Prompt Agents

Use a prompt agent when instructions and built-in tools can express the workflow. Foundry manages orchestration, sessions, scaling, identity, and observability, making this the fastest path to a governed agent.

## Hosted Agents

Use a hosted agent when the solution requires custom orchestration code, libraries, middleware, state handling, multi-agent coordination, or integrations beyond declarative tools. The developer owns more application logic while Foundry supplies managed hosting.

## Managed Harness Option - November 2026 Update

The [October 28 announcement](https://devblogs.microsoft.com/foundry/microsoft-copilot-harness-in-foundry/)
adds a **public-preview Microsoft Copilot harness for prompt agents** with
managed skills, files, execution, and bounded delegation. Multi-step work or
subagents alone no longer imply that the application must own a hosted runtime.
Use hosted agents when custom execution behavior or dependencies are required,
not simply because the workflow is complex.

Hosted-agent long-running resilience is separately GA. Progress checkpoints,
restart behavior, and duplicate-action prevention remain application concerns.
See the [managed harness resource](foundry-copilot-harness-managed-execution.md)
for preview, creation-time selection, and billing boundaries.

## Decision Rule

Default to the least-custom option that satisfies the requirements. Move to hosted agents only when required behavior cannot be expressed reliably through instructions and managed tools.

## Related Pages

- [Managed Copilot harness](foundry-copilot-harness-managed-execution.md)
- [[azure-ai-foundry]]
- [[ai-agent-lifecycle]]
- [[ai-agents-for-it-ops-workshop]]
- [[deploying-hosted-agents-foundry-terraform]]
