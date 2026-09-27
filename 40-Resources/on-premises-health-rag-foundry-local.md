---
title: On-Premises Health RAG with Foundry Local
type: resource
created: 2026-09-26
updated: 2026-09-26
tags: [healthcare, rag, foundry-local, data-residency, rust]
sources:
  - https://techcommunity.microsoft.com/blog/educatordeveloperblog/architecture-first-drawing-the-boundary-for-on-premises-health-rag/4557242
  - https://techcommunity.microsoft.com/blog/educatordeveloperblog/foundry-local-with-rust-from-catalog-discovery-to-in-process-streaming/4558179
  - https://techcommunity.microsoft.com/blog/educatordeveloperblog/documentdb-as-an-internal-hybrid-store-documents-vectors-state-and-safe-publicat/4558181
  - raw/2026-09-26-github-open-issues-101-113/issues.md
status: active
---

# On-Premises Health RAG with Foundry Local

This series begins with a strict invariant: health records, prompts, vectors,
retrieved evidence, conversations, model output, and operational telemetry
remain on premises. If local inference is unavailable, model-dependent work
must fail or degrade explicitly rather than silently use a cloud fallback.

## Architecture Pattern

- Begin with legal, residency, and trust boundaries before selecting products.
- Keep policy and orchestration in one server-side boundary; do not expose
  bearer credentials to browser clients.
- Separate operational clinical systems from the internal retrieval store.
- Treat ingestion as governed publication rather than bulk copying.
- Distinguish answer paths that use governed records from other information.
- Prove the local model lifecycle first: initialize the SDK, inspect the
  catalog, resolve a device-specific model, cache and load it, and stream tokens.
- Keep embedding and retrieval boundaries explicit rather than hiding them
  inside the inference integration.

## Partner Relevance

Partners can use the pattern for regulated local-AI discovery, residency
architecture, hardware-fit validation, explicit failure design, and controlled
RAG prototypes. The referenced implementation uses synthetic data and is not a
clinical or compliance-ready system.

The third article redirected to authentication during this capture, so this
summary does not rely on unverified details from it.
