---
title: Azure Content Understanding GPT-5 Model Selection
type: resource
created: 2026-08-14
updated: 2026-08-14
tags:
  - azure-content-understanding
  - gpt-5
  - model-selection
  - grounding
  - confidence
sources:
  - https://devblogs.microsoft.com/foundry/azure-content-understanding-gpt-5-series-guide-model-selection-grounding-improvements-and-confidence-enhancements/
  - raw/2026-08-14-github-open-issues-47-53/issues.md
status: active
---

# Azure Content Understanding GPT-5 Model Selection

Microsoft Foundry guidance for selecting GPT-5-series models in Azure Content Understanding across document, image, video, and speech workloads.

## Starting points

| Modality | Balanced | Higher quality | Lower cost |
| --- | --- | --- | --- |
| Document and speech | GPT-5.1 or GPT-5.2 | GPT-5.5 | GPT-5.4 Mini |
| Video | GPT-5 or GPT-5.1 | Same as balanced | GPT-5 Mini |
| Image classification | GPT-5.1 | GPT-5.5 when the premium is justified | GPT-5 Mini |

These are benchmark-derived starting points, not universal winners. Teams should hold the analyzer, schema, representative inputs, and labeled examples constant while changing only the model deployment.

## Grounding and confidence

Microsoft reports that the updated grounding approach used 20–30% fewer input tokens and 18–28% fewer total inference tokens per document in tested configurations, reducing the full-inference LLM cost by 11–25%. The refreshed confidence method improved ranking accuracy in the reported tests.

Mini and Nano models showed materially weaker confidence quality. Confidence-sensitive workflows should test carefully, use field-specific acceptance thresholds, and recalibrate thresholds whenever the model changes.

## Partner relevance

- Turns model choice into a measurable quality, cost, latency, throughput, availability, and compliance decision.
- Supports straight-through processing with grounding evidence and calibrated field confidence.
- Provides a repeatable assessment method using Studio or request-level deployment overrides.

## Related pages

- [Azure Content Understanding](../10-Notes/concepts/azure-content-understanding.md)
- [Data and AI](../100-Crucible/DataAISolutionArea.md)
