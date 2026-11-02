---
title: Copilot Studio Harness Selection
type: resource
created: 2026-09-05
updated: 2026-11-02
tags: [copilot-studio, github-copilot, agent-architecture, decision-guide]
sources:
  - https://www.microsoft.com/en-us/copilot/blog/copilot-studio/the-github-copilot-harness-in-copilot-studio-is-now-the-microsoft-copilot-harness/
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - https://techcommunity.microsoft.com/blog/copilot-studio-blog/white-paper-choosing-between-the-github-copilot-and-standard-harnesses-in-copilo/4552385
  - https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/overview
  - https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/build-new-agent
  - https://learn.microsoft.com/en-us/training/modules/explore-copilot-studio-agent-harnesses/
  - https://learn.microsoft.com/en-us/microsoft-copilot-studio/create-automation-natural-language
  - https://microsoft.github.io/agent-academy/recruit-nextgen/
  - https://learn.microsoft.com/en-us/credentials/certifications/github-copilot/
  - raw/2026-09-05-github-open-issues-72-85/issues.md
  - raw/2026-09-18-copilot-studio-github-copilot-harness/source.md
status: active
---

# Copilot Studio Harness Selection

Decision guide for choosing the execution harness that mediates context, tools, planning, and task completion in Copilot Studio.

## Current Naming and Evidence

The [October rename announcement](https://www.microsoft.com/en-us/copilot/blog/copilot-studio/the-github-copilot-harness-in-copilot-studio-is-now-the-microsoft-copilot-harness/)
renames the **GitHub Copilot harness** to the **Microsoft Copilot harness** in
Copilot Studio. Existing agents continue operating with no capability or billing
change from the rename. Older linked training and guidance may retain the
GitHub Copilot name; this is not a request to migrate existing agents.

Microsoft's reported harness comparisons use internal evaluations and telemetry
with scenario, model, and configuration limits. They are evidence for evaluation
planning, not a guarantee of task success, resilience, or customer savings.
The [Foundry public preview](foundry-copilot-harness-managed-execution.md) is a
separate implementation with its own status, limits, and billing.

## Selection Guidance

- **Standard harness:** best for bounded, predictable workflows with explicit topics and flows, inspectable control logic, and lower operating cost.
- **Microsoft Copilot harness (formerly GitHub Copilot):** best for reasoning-heavy, adaptive, multi-step work that benefits from dynamic planning, skills, memory, files, tools, connected agents, and sandboxed execution.

Select from workload needs, not novelty. Start with the simplest harness that reliably completes the task, then use the Microsoft Copilot harness when dynamic decomposition and recovery justify its greater runtime complexity and cost.

The previously reviewed guidance states that agents cannot be transferred between
the Standard and GitHub Copilot harnesses. The rename announcement does not
announce a transfer capability; verify current portability before promising
migration. Treat orchestration, supported capabilities, publishing channels,
billing, and migration constraints as architecture criteria.

## Microsoft Copilot Harness Delivery Model

- Describe the desired behavior with natural language.
- Configure instructions, knowledge, tools, reusable skills, model, memory, and connected agents.
- Use Build, Preview, Evaluate, and Monitor activities before publication.
- Establish connections, permissions, evaluation datasets, release criteria, monitoring, and Copilot Credit controls explicitly.
- Retain preview qualifiers for natural-language solution generation, memory, model availability, and billing details.

## Implementation and Skilling Path

- [Microsoft Learn harness overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/overview)
- [Create a new GitHub Copilot harness agent](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agents-experience/build-new-agent)
- [Explore Copilot Studio and agent harnesses](https://learn.microsoft.com/en-us/training/modules/explore-copilot-studio-agent-harnesses/)
- [Create an automated solution with natural language](https://learn.microsoft.com/en-us/microsoft-copilot-studio/create-automation-natural-language)
- [Agent Academy: GitHub Copilot harness](https://microsoft.github.io/agent-academy/recruit-nextgen/)
- [GitHub Copilot certification](https://learn.microsoft.com/en-us/credentials/certifications/github-copilot/)

## Related Pages

- [Managed Copilot harness in Foundry](foundry-copilot-harness-managed-execution.md)
- [[copilot-studio]]
- [[ai-agent-lifecycle]]
- [[token-economics]]
