---
title: Azure Content Understanding
type: concept
created: 2026-07-10
updated: 2026-11-20
tags:
  - azure
  - azure-ai-foundry
  - document-processing
  - content-understanding
sources:
  - https://azure.microsoft.com/en-us/updates?id=563661
  - https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-content-understanding
  - raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right/extracted_text.md
  - raw/2026-08-14-github-open-issues-47-53/issues.md
status: active
---

# Azure Content Understanding

Azure Content Understanding is a Foundry Tool for document and content processing that uses generative AI and LLM-powered analyzers. It is positioned for unstructured documents, varying layouts, multimodal content, inferred fields, complex reasoning, and zero-shot schema-based extraction without requiring labeled training data to start.

## Best Fit

- Semi-structured and unstructured documents.
- High-variation templates.
- Multimodal inputs such as documents, images, audio, and video.
- RAG-ready preprocessing and grounded summaries.
- Custom extraction where fields can be described in plain language.
- Scenarios needing reasoning, validation, enrichment, confidence, and grounding.

## Model Selection

Model selection should balance quality on representative content against end-to-end cost, latency, throughput, availability, and compliance. Hold the analyzer, schema, inputs, and labeled examples constant while swapping model deployments.

For GPT-5-series starting points, Microsoft recommends GPT-5.1 or GPT-5.2 for balanced document and speech extraction, GPT-5 or GPT-5.1 for video, and GPT-5.1 for image classification. Smaller models can reduce cost but require workload-specific quality testing. Confidence-sensitive workflows should avoid assuming Mini or Nano confidence scores are interchangeable with full-size models.

Acceptance thresholds should be calibrated per field and recalibrated whenever the model changes.

## Related

- [Search Semantic Chunking and Image Descriptions](../../40-Resources/content-understanding-search-semantic-chunking.md) - GA in Search API 2026-10-01; extraction, descriptions, vectors, serving, polling, and billing remain separate concerns.
- [[azure-ai-foundry]]
- [[azure-document-intelligence]]
- [[document-processing-tool-selection]]
- [[044-choose-the-right-azure-ai-tool-for-document-processing-foundry-tools-microsoft-l]]
- [[moc-ingested-link-library]]
- [[content-understanding-gpt5-model-selection]]
