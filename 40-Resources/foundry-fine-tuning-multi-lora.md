---
title: Foundry Fine-Tuning and Shared Multi-LoRA Deployments
type: resource
created: 2026-10-27
updated: 2026-10-27
tags: [microsoft-foundry, fine-tuning, lora, finops, preview]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/foundry-fine-tuning-open-source-model-expansion-mai-code-and-shared-multi-lora-d/4565915
  - raw/2026-10-27-github-open-issues-125-134/issues.md
  - raw/2026-10-27-github-open-issues-125-134/sources.md
status: active
---

# Foundry Fine-Tuning and Shared Multi-LoRA Deployments

## Source Summary

The [October 22 Microsoft announcement](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/foundry-fine-tuning-open-source-model-expansion-mai-code-and-shared-multi-lora-d/4565915)
introduces public-preview managed fine-tuning for Muse-Glimmer-30B,
qwen3.8-27b, qwen3.6-35b-a3b, and gpt-oss-120b with supervised and
reinforcement fine-tuning. MAI-Code-1.1-Flash supports **RFT only** in this
preview; do not assume the same training methods apply to every model.

Multi-LoRA Managed Compute is also public preview. Compatible adapters can
share a LoRA-enabled base deployment and GPU capacity while remaining separately
addressable. The described managed-compute path supports the four OSS models;
do not infer MAI-Code support for that path.

## Serving Economics and Constraints

The article contrasts hourly hardware billing with per-token serverless
inference and per-deployment hosting charges. Shared hardware may improve
utilization across variants, but idle hardware remains billable and aggregate
concurrency and context lengths determine capacity needs.

Adapters must match the same base model and version, use a compatible
LoRA-enabled deployment template, and have accelerator quota. Confirm current
regional support and eligible deployment paths before quoting.

## Partner Application

**Interpretation:** Offer an evaluation-led customization engagement: establish
a baseline, curate examples or verifiable rewards, train a bounded variant,
and evaluate the resulting agent with its real instructions, tools, and
workflow. Compare pooled hardware and eligible serverless alternatives using
observed utilization rather than promising savings from adapter count alone.

## Related Pages

- [Shared Adapter Serving](../10-Notes/concepts/shared-adapter-serving.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Open-Weight Model Risk](open-weight-model-risk-enterprise.md)
- [Economics of Agent Optimization](economics-of-agent-optimization.md)
