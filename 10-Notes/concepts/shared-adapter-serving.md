---
title: Shared Adapter Serving
type: concept
created: 2026-10-27
updated: 2026-10-27
tags: [lora, serving, finops, capacity-planning]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/foundry-fine-tuning-open-source-model-expansion-mai-code-and-shared-multi-lora-d/4565915
status: active
---

# Shared Adapter Serving

Multiple compatible fine-tuned adapters can share a base-model deployment
instead of duplicating its serving footprint. The reviewed
[Foundry Multi-LoRA preview](../../40-Resources/foundry-fine-tuning-multi-lora.md)
requires matching base model/version and a compatible LoRA-enabled template.

**Interpretation:** Pooling is a capacity decision, not an automatic saving.
Measure aggregate concurrency, context lengths, latency, and idle hours; compare
hourly hardware with eligible serverless alternatives. Evaluate each adapter
in its full application workflow, not solely on training metrics.

## Related Pages

- [Token Economics](token-economics.md)
- [Economics of Agent Optimization](../../40-Resources/economics-of-agent-optimization.md)
- [Microsoft Foundry](../entities/microsoft-foundry.md)
