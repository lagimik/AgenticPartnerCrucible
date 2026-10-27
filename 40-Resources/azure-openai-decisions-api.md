---
title: Azure OpenAI Decisions API in Microsoft Foundry
type: resource
created: 2026-10-27
updated: 2026-10-27
tags: [microsoft-foundry, azure-openai, decision-making, agents]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/azure-openai-decisions-api-now-generally-available-in-microsoft-foundry/4567265
  - raw/2026-10-27-github-open-issues-125-134/issues.md
  - raw/2026-10-27-github-open-issues-125-134/sources.md
status: active
---

# Azure OpenAI Decisions API in Microsoft Foundry

## Source Summary

Microsoft's [October 23 announcement](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/azure-openai-decisions-api-now-generally-available-in-microsoft-foundry/4567265)
describes the generally available Decisions API as a focused way to evaluate
text, images, and structured input. Questions return a probability, a choice
from predefined options, or a score against a rubric rather than free-form
generated text requiring interpretation.

The announcement specifies `/openai/v1/decisions` on an Azure OpenAI resource,
a GPT-6 Luna deployment name in `model`, OpenAI SDK or REST access, and API-key
or Microsoft Entra ID authentication. Confirm current model, region, quota,
and pricing support before designing a deployment.

## Partner Application

**Interpretation:** Evaluate bounded decision points before, during, and after
agent execution: request routing, issue prioritization, output acceptance,
retry selection, and human escalation. Benchmark task quality, latency, and
cost against rules and existing models using customer-representative examples.

Structured output does not establish calibrated confidence, factual correctness,
or authorization. Enforce business constraints and side-effect permissions in
application code; retain review paths for uncertain or high-impact decisions.
The announcement is not an independent performance or savings benchmark.

## Related Pages

- [Structured AI Decisions](../10-Notes/concepts/structured-ai-decisions.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [SAFE Agent Controls](safe-agent-controls-foundry.md)
- [Token Economics](../10-Notes/concepts/token-economics.md)
