---
title: "Using APIM as the Gateway for Azure AI Foundry"
type: resource
created: 2026-07-13
updated: 2026-07-13
tags:
  - azure-api-management
  - azure-ai-foundry
  - ai-governance
  - token-management
  - finops
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/from-ai-adoption-to-ai-governance---using-apim-as-the-gateway-for-azure-ai-found/4536247
  - raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
status: active
claims:
  - id: claim-001
    text: "APIM can emit per-model token metrics (prompt, completion, total) using the azure-openai-emit-token-metric policy with model dimensions."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
        kind: documentation
        excerpt: "azure-openai-emit-token-metric — emit prompt, completion, and total token counts dimensioned by model"
    captured: 2026-07-13
    updated: 2026-07-13
  - id: claim-002
    text: "APIM authenticates to Azure AI Foundry using system-assigned managed identity for cognitiveservices.azure.com — no keys leave the gateway."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
        kind: documentation
        excerpt: "authentication-managed-identity — obtain Entra ID token for cognitiveservices.azure.com using APIM's system-assigned identity. No keys ever leave the gateway."
    captured: 2026-07-13
    updated: 2026-07-13
---

# Using APIM as the Gateway for Azure AI Foundry

Tech Community article showing how Azure API Management serves as an AI Gateway in front of Azure AI Foundry for governance, chargeback, and budget control.

## Summary

Enterprises move through three phases of AI adoption: evaluating models → building apps/agents → operationalizing in production. The third phase requires governance: per-model token visibility, chargeback, and budget alerts.

APIM becomes the governed front door. Clients call an OpenAI-compatible endpoint unchanged; APIM handles authentication, model resolution, request forwarding, and per-model token telemetry emission.

## Architecture

```
Client → Azure Front Door + WAF → APIM (AI Gateway) → Azure AI Foundry
```

## Key Policy Steps

1. `set-backend-service` — select Foundry backend
2. `authentication-managed-identity` — Entra ID token via managed identity
3. `set-variable deployment-id` — resolve model from URL path or request body (dual-shape)
4. `azure-openai-emit-token-metric` — per-model token metrics to Azure Monitor

## Governance Capabilities

- Per-model token visibility in Azure Monitor / Application Insights
- Per-subscription chargeback queries (KQL)
- Rolling 24-hour token budget alerts
- Front Door + WAF for edge security (OWASP, bot protection, IP restriction)

## Related Pages

- [[azure-ai-foundry]]
- [[ai-governance]]
- [[token-economics]]
- [[ai-gateway-pattern]]
