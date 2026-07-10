---
title: Document Processing Tool Selection
type: concept
created: 2026-07-10
updated: 2026-07-10
tags:
  - document-processing
  - azure-ai-foundry
  - decision-model
sources:
  - raw/2026-07-10-ingestlinks/044-learn-microsoft-com-en-us-azure-ai-services-content-understanding-choosing-right/extracted_text.md
status: active
---

# Document Processing Tool Selection

Document processing tool selection is the decision pattern for choosing between managed extraction services and custom LLM-based builds.

## Decision Pattern

1. Use managed services first when you need built-in OCR, extraction, confidence/grounding, scaling, governance, and lower operational burden.
2. Use [[azure-document-intelligence]] for structured documents, common templates, low-latency extraction, and labeled custom models.
3. Use [[azure-content-understanding]] for unstructured or semi-structured documents, high variation, multimodal content, inferred fields, and zero-shot schema-based extraction.
4. Build your own with Azure-hosted LLMs only when you need full control over models, prompts, proprietary infrastructure, or unsupported workflow behavior.

## Evaluation Criteria

- Straight-through processing rate.
- Latency.
- Accuracy.
- Continuous improvement path.
- Build effort.
- Total cost of ownership.
- Security and governance requirements.

## Related

- [[azure-ai-foundry]]
- [[azure-content-understanding]]
- [[azure-document-intelligence]]
- [[044-choose-the-right-azure-ai-tool-for-document-processing-foundry-tools-microsoft-l]]
- [[moc-ingested-link-library]]
