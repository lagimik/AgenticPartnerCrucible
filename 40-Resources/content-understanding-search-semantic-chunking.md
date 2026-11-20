---
title: Content Understanding Semantic Chunking and Image Descriptions in Search
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [content-understanding, azure-ai-search, foundry-iq, rag, document-processing]
sources:
  - https://azure.microsoft.com/en-us/updates?id=563661
  - https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-content-understanding
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Content Understanding Semantic Chunking and Image Descriptions in Search

## Source Summary

[Update 563661](https://azure.microsoft.com/en-us/updates?id=563661) announces
GA semantic chunking and AI-generated image descriptions in Azure AI Search
enrichment for Search and Foundry IQ. Outputs include coherent Markdown chunks,
location metadata, and searchable figure descriptions.

The [skill reference](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-content-understanding)
distinguishes base-skill GA in Search REST API `2026-04-01` from the new capabilities
in `2026-10-01`. The downstream Content Understanding API is `2025-11-01`, not
the same version contract.

| Capability | Separate configuration or limit |
| --- | --- |
| Semantic chunking | Layout/heading-aware token chunks; not semantic ranking. |
| Image extraction | `extractionOptions` includes `images`; does not automatically describe figures. |
| Image descriptions | Pair supported `modelName` and `modelDeployment`; independent of chunking choice. |
| Vectors and image delivery | Configure embeddings and authorized client image serving separately. |
| Source grounding | Preserve page offsets, figure associations, source identifiers, and permissions. |

## Operational Boundaries

Search polls analysis for up to **eight minutes**, not a file-size threshold or
end-to-end SLA. A timeout reports an enrichment error and returns no analysis
output for the document. Other indexed metadata/run behavior depends on the
remaining pipeline and failure thresholds; missing chunks do not prove the
entire document was excluded. Stopping polling does not prove cancellation.

Search tier limits, Content Understanding quotas, supported regions/file types,
and model support all apply. Format differences can alter extracted images.
Optional image storage has restrictions for permission-ingesting pipelines.
Extraction and optional model usage are separately billed; retries may repeat
analysis and charges.

## Partner Application

**Interpretation:** Evaluate representative long, image-heavy, and cross-page
documents for extraction quality, citations, timeouts, permissions, and measured
processing cost. Split only on meaningful boundaries while carrying source
offsets and ACLs forward; verify enrichment errors instead of treating an
indexer completion as complete document coverage.

## Related

- [Azure Content Understanding](../10-Notes/concepts/azure-content-understanding.md)
- [Content Understanding Model Selection](content-understanding-gpt5-model-selection.md)
- [Foundry Continuous Improvement](foundry-continuous-improvement.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
