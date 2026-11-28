---
title: Ignite 2026 - Microsoft Foundry
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [ignite-2026, microsoft-foundry, evaluation, optimization, models]
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - raw/2026-11-27-ignite-2026-book-of-news/source.md
  - https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights
status: active
---

# Ignite 2026 - Microsoft Foundry

This page follows the source's Foundry headings and attributes release labels
to the [Book of News](https://news.microsoft.com/events/ignite/2026/book-of-news/).
Evaluation results and model benchmarks are publisher-reported, not guarantees
of customer quality, latency or savings.

## Continuous improvement in Foundry

### Evaluation, production insights, optimization and training

Multi-turn evaluation and recurring production insights are announced GA.
Human annotations and new safety-evaluator support are preview.
The source announces Agent Optimizer GA, while Managed Training and Programmed
Training additions are preview. Teams retain evaluation baselines, regression
checks and deployment decisions.
[Source follow-up](https://aka.ms/miq-ignitelaunchblog).

## New models

### Microsoft-Decision-1.1

The structured-decision model is announced GA, including image inputs and use
across supported hosting platforms. It selects among developer-permitted
choices and exposes confidence; those choices and confidence do not replace
application authorization. Reported benchmark gains need workload evaluation.
[Source follow-up](https://aka.ms/decision-model-ga).

### MAI, routing and partner model portfolio

MAI-Code-2/Code-2-Flash are GA in GitHub; Code-2-Flash is separately private
preview in Foundry. Image models and the MDASH-only cyber model additions have
preview restrictions. Video models and Baseten deployments are preview.
Microsoft-Decision-1.1 is the explicit GA decision-model announcement.

The model-router description mentions broader model and API coverage without
individually declaring all routing features GA. Retain the
[specific Responses, capacity and gateway status boundaries](../foundry-model-router-responses-capacity-gateway.md).
Large catalog counts are not proof that every model supports every region,
protocol or deployment mode.
[Source follow-up](https://aka.ms/foundrymodelsignite2026).

## Release-status reconciliation

The Book of News explicitly announces Agent Optimizer GA.
The [insights-driven optimization guide](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights)
reviewed on 2026-11-27 labels that workflow preview, with prompt-agent/harness
restrictions. These may describe different scopes or versions; equivalence
has not been established. Do not silently convert every optimizer workflow to
GA or discard the event announcement.

The IQ section's broad improvement/platform GA framing also does not override
the Foundry item's explicit training previews. Before delivery commitments,
verify the exact workflow, model, API version, region and published terms.
Candidate evaluation can still call live tools before deployment: isolate
actual permissions and resources, not only compute.

## Connected Knowledge

- [Microsoft Foundry](../../10-Notes/entities/microsoft-foundry.md)
- [Agent Optimizer](../microsoft-foundry-agent-optimizer.md)
- [Agent Insights](../foundry-agent-insights.md)
- [Decisions API](../azure-openai-decisions-api.md)
- [Fine-tuning and Multi-LoRA](../foundry-fine-tuning-multi-lora.md)
- [IQ continuous improvement](microsoft-iq.md#continuous-improvement)
- [Ignite map](../moc-ignite-2026-book-of-news.md)
