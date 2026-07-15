# From AI Adoption to AI Governance - Using APIM as the Gateway for Azure AI Foundry

**Source:** https://techcommunity.microsoft.com/blog/appsonazureblog/from-ai-adoption-to-ai-governance---using-apim-as-the-gateway-for-azure-ai-found/4536247
**Captured:** 2026-07-13
**Issue:** lagimik/AgenticPartnerCrucible#3

---

Enterprises move through three phases of AI adoption: evaluating models, building apps and agents, and operationalizing them in production. The third is where governance becomes critical. Once multiple teams share an AI endpoint, leaders need clear answers: which model consumed tokens, which team used them, and who is authorized to call it.

This post shows how to place Azure API Management (APIM) in front of Azure AI Foundry as an AI Gateway, turning a shared endpoint into a governed control point for per-model token visibility, chargeback, and budget alerts — with no changes to client code. It also shows where Azure Front Door and Web Application Firewall (WAF) fit in a secure AI Landing Zone.

## The Problem

Azure gives rich resource-level telemetry out of the box (Azure Monitor Metrics, Diagnostic settings). But a governance view needs model identity and token counts correlated in a single record for per-model, month-to-date chargeback and alerting.

## The Pattern: APIM as AI Gateway

APIM becomes the governed front door for Azure AI Foundry. Clients continue calling an OpenAI-compatible endpoint; APIM authenticates to Foundry with a system-assigned managed identity, forwards the request, and emits per-model token telemetry to Azure Monitor and Application Insights.

### Key Policy Steps

1. **set-backend-service** — select Azure AI Foundry backend
2. **authentication-managed-identity** — obtain Entra ID token for cognitiveservices.azure.com
3. **set-variable deployment-id** — resolve model name from URL path or request body
4. **azure-openai-emit-token-metric** — emit prompt/completion/total token counts dimensioned by model

### Dual-Shape Model Resolution

Different API surfaces place model name in different locations:
- Foundry Model Inference / Anthropic-style: model in request body
- Azure OpenAI-compatible: model in URL path `/deployments/{name}/`

The policy handles both shapes for consistent governance.

## Observability

Metrics land in Azure Monitor / Application Insights under namespace `genai-tokens`. Per-model consumption queries and per-subscription chargeback views are built in.

## Cost Guardrail: 24-Hour Token Alert

A rolling 24-hour token-budget check via Azure Monitor log search alert rule. Fires when any model crosses its daily token budget.

## Completing the Picture: Front Door + WAF

- OWASP protection (Microsoft_DefaultRuleSet_2.1)
- Bot protection (Microsoft_BotManagerRuleSet_1.0)
- IP restriction and rate limiting
- DDoS protection at the edge

Architecture: Client → Front Door + WAF → APIM (AI Gateway) → Azure AI Foundry
