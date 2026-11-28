---
title: "Using APIM as the Gateway for Azure AI Foundry"
type: resource
created: 2026-07-13
updated: 2026-11-27
tags:
  - azure-api-management
  - azure-ai-foundry
  - ai-governance
  - token-management
  - finops
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/from-ai-adoption-to-ai-governance---using-apim-as-the-gateway-for-azure-ai-found/4536247
  - raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
  - https://learn.microsoft.com/en-us/azure/api-management/llm-emit-token-metric-policy
status: active
claims:
  - id: claim-001
    text: "APIM's llm-emit-token-metric policy can emit model/provider-dependent token metrics to Application Insights for supported LLM APIs, with up to five custom dimensions."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: https://learn.microsoft.com/en-us/azure/api-management/llm-emit-token-metric-policy
        kind: documentation
        excerpt: "Token count metrics are model- and provider-dependent and can include total, prompt, and completion tokens."
    captured: 2026-07-13
    updated: 2026-11-27
  - id: claim-002
    text: "The article's configured APIM gateway authenticates to its Foundry backend using a system-assigned managed identity for cognitiveservices.azure.com, avoiding backend API keys in that flow."
    confidence: 0.95
    status: evergreen
    evidence:
      - source: raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
        kind: documentation
        excerpt: "authentication-managed-identity — obtain Entra ID token for cognitiveservices.azure.com using APIM's system-assigned identity. No keys ever leave the gateway."
    captured: 2026-07-13
    updated: 2026-11-27
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

**2026-11-27 revalidation:** The July article uses
`azure-openai-emit-token-metric`; its documentation now redirects to
[`llm-emit-token-metric`](https://learn.microsoft.com/en-us/azure/api-management/llm-emit-token-metric-policy).
Use the current policy reference for supported API schemas, tier restrictions,
Application Insights prerequisites and the five-custom-dimension limit.
Streaming interruptions and missing usage fields can make metrics incomplete.
Managed identity in this sample covers backend authentication, not every
client's authorization or every Foundry API.

1. `set-backend-service` — select Foundry backend
2. `authentication-managed-identity` — Entra ID token via managed identity
3. `set-variable deployment-id` — resolve model from URL path or request body (dual-shape)
4. `llm-emit-token-metric` — token metrics to Application Insights with explicitly configured model dimensions and usage-field support

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
