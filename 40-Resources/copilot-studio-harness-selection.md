---
title: Copilot Studio Harness Selection
type: resource
created: 2026-09-05
updated: 2026-09-18
tags: [copilot-studio, github-copilot, agent-architecture, decision-guide]
sources:
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

- **Standard harness:** best for bounded, predictable workflows with explicit topics and flows, inspectable control logic, and lower operating cost.
- **GitHub Copilot harness:** best for reasoning-heavy, adaptive, multi-step work that benefits from dynamic planning, skills, memory, files, tools, connected agents, and sandboxed execution.

Select from workload needs, not novelty. Start with the simplest harness that reliably completes the task, then use the GitHub Copilot harness when dynamic decomposition and recovery justify its greater runtime complexity and cost.

Harness choice is not portable: Microsoft states that agents cannot be transferred between the standard and GitHub Copilot harnesses. Treat orchestration, supported capabilities, publishing channels, billing, and migration constraints as architecture criteria.

## GitHub Copilot Harness Delivery Model

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

- [[copilot-studio]]
- [[ai-agent-lifecycle]]
- [[token-economics]]
