---
title: Structured AI Decisions
type: concept
created: 2026-10-27
updated: 2026-10-27
tags: [decision-making, agents, evaluation, governance]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/azure-openai-decisions-api-now-generally-available-in-microsoft-foundry/4567265
status: active
---

# Structured AI Decisions

A model can return a bounded choice, probability, or rubric score at an
application decision point instead of generating an unconstrained answer.
The [Decisions API](../../40-Resources/azure-openai-decisions-api.md) illustrates
this separation of routing and evaluation from content generation.

**Interpretation:** Define the allowed outcomes, test representative and
adversarial cases, and keep authorization and mandatory business rules outside
the model. A well-formed score is not proof of calibration, correctness, or
permission to act; uncertain and high-impact cases need an explicit fallback.

## Related Pages

- [SAFE Agent Controls](../../40-Resources/safe-agent-controls-foundry.md)
- [Agent Recovery Engineering](agent-recovery-engineering.md)
- [Microsoft Foundry](../entities/microsoft-foundry.md)
