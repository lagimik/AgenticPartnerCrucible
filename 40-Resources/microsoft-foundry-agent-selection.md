---
title: Choosing the Right Agent in Microsoft Foundry
type: resource
created: 2026-08-21
updated: 2026-08-21
tags:
  - microsoft-foundry
  - agents
  - architecture
  - decision-guide
sources:
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

## Decision Rule

Default to the least-custom option that satisfies the requirements. Move to hosted agents only when required behavior cannot be expressed reliably through instructions and managed tools.

## Related Pages

- [[azure-ai-foundry]]
- [[ai-agent-lifecycle]]
- [[ai-agents-for-it-ops-workshop]]
