---
title: Choose the right Azure AI tool for document processing - Foundry Tools | Microsoft Learn
type: resource
created: 2026-07-10
updated: 2026-07-10
tags:
  - azure-ai-foundry
  - azure
  - security
  - document-processing
  - content-understanding
sources:
  - raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right/source.url
  - raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right/metadata.json
  - raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right/extracted_text.md
status: active
---

# Choose the right Azure AI tool for document processing - Foundry Tools | Microsoft Learn

Source: https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/choosing-right-ai-tool

Final URL: https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/choosing-right-ai-tool

Raw capture: `raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right`

## Summary

This Microsoft Learn guide explains how to choose among [[azure-content-understanding]], [[azure-document-intelligence]], and build-your-own solutions with Azure-hosted LLMs for document and multimodal content processing.

Key takeaways:

1. Use managed Azure Content Understanding or Document Intelligence when you want built-in OCR, extraction, confidence/grounding, scaling, post-processing, governance, and lower engineering overhead.
2. Use [[azure-document-intelligence]] for structured or highly templated documents where low latency, consistency, labeled training, and proven extraction accuracy matter.
3. Use [[azure-content-understanding]] for unstructured, semi-structured, high-variation, multimodal, inferred-field, or zero-shot schema-based extraction scenarios.
4. Build your own with Azure-hosted LLMs only when you need complete control over models, prompts, proprietary infrastructure, or unsupported workflow requirements.
5. Preview API versions `2024-12-01-preview` and `2025-05-01-preview` retire July 15, 2026; new work should target `2025-11-01 (GA)`.

## Decision Model

The article frames tool selection around a two-step decision:

1. Choose managed service vs. custom build.
2. If managed, choose Content Understanding analyzers vs. Document Intelligence models.

Use [[document-processing-tool-selection]] as the durable concept page for the decision pattern.

## Notable Headings

- Choose the right Foundry Tool for document processing
- In this article
- Foundry Tools for Document Processing
- Azure Content Understanding vs. build your own
- Choosing the right tool within Azure Content Understanding
- Quick-reference decision guide
- Scenario walkthroughs
- Scenario 1: Standardized, single-format forms
- Scenario 2: Documents with a small number of known variants
- Scenario 3: High-variation semi-structured documents

## Ingest Notes

- Capture status: `captured`.
- Content type: `text/html`.
- This page was generated from the provided ingest link list and should be refined when the source becomes important.

## Related

- [[moc-ingested-link-library]]
- [[azure-ai-foundry]]
- [[azure-content-understanding]]
- [[azure-document-intelligence]]
- [[document-processing-tool-selection]]
