---
title: AI Gateway Pattern
type: concept
created: 2026-07-13
updated: 2026-11-27
tags:
  - azure-api-management
  - ai-governance
  - architecture-pattern
  - token-management
sources:
  - https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-ai-gateway
  - raw/2026-11-27-foundry-routing-and-agent-insights/source.md
  - raw/2026-07-13-apim-gateway-azure-ai-foundry/source.md
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# AI Gateway Pattern

An architecture pattern where an API gateway is placed in front of AI model endpoints to add governance, observability, and cost control without changing client code.

## Pattern

```
Client → [Edge Security] → API Gateway (AI Gateway) → AI Model Service
```

## Capabilities Added by the Gateway

- **Authentication** — Managed identity to backend, no keys in client code
- **Model resolution** — Identify which model is being called regardless of API shape
- **Token metering** — Per-model prompt/completion/total token metrics
- **Chargeback** — Per-subscription, per-model cost allocation
- **Budget alerts** — Rolling token budget guardrails with alerting
- **Rate limiting** — Throttle abusive callers
- **Security** — WAF, DDoS, bot protection at the edge
- **Resilience** — Backend pools, priority/weight routing, retries, and circuit breakers
- **Caching** — Semantic response reuse to reduce latency and token consumption
- **Protocol governance** — Central controls for model APIs, MCP servers, and A2A APIs

## Why It Matters

AI adoption outpaces AI governance. Once multiple teams share endpoints, the gateway becomes the control point where model identity and token usage are captured together by design.

## Azure Implementation

Azure API Management with:
- `azure-openai-emit-token-metric` policy
- `authentication-managed-identity` for keyless auth
- Dual-shape model resolution (URL path + request body)
- Azure Front Door + WAF for edge security
- AI backend pools with priority and weight
- Token limits and quotas keyed to consumer identity
- Semantic caching backed by a compatible vector cache

## Reliability Pattern

Use committed capacity as the preferred backend and alternate deployments or regions as fallback. A circuit breaker temporarily removes throttled or failing backends; retry logic then selects another healthy member of the pool. Clients retain one stable endpoint while the gateway owns failover.

## Related Pages

- [Foundry Model Router](../../40-Resources/foundry-model-router-responses-capacity-gateway.md) - Separate model ranking from capacity preference and backend distribution.
- [[apim-gateway-azure-ai-foundry]]
- [[token-economics]]
- [[ai-governance]]
- [[multitenant-ai-agent-governance-architecture]]
- [[azure-ai-foundry]]
- [[azure-api-management-ai-gateway-capabilities]]
- [[azure-ai-gateway-labs]]
- [[openai-at-scale-apim-reliability]]

## Model Selection Versus Backend Preference

The [November AI Gateway selection preview](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-ai-gateway)
separates two policy decisions: which supported model fits the request, and
which backend should serve that model. Model first can select across priority
groups; Priorities first limits model choice to the highest-priority group.
Weights then split traffic between that model's backends at the selected priority.

**Interpretation:** Make this precedence explicit when using committed capacity.
Preferred capacity, estimated cost, and model quality are different objectives;
none is guaranteed by the presence of a gateway. This selection preview has
different API, conversation, and pricing boundaries from direct Foundry routing
or the older APIM backend-pool reliability pattern.
