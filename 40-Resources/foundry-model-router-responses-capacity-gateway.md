---
title: Foundry Model Router - Responses, Capacity, and AI Gateway
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [microsoft-foundry, model-router, responses-api, ai-gateway, capacity, finops]
sources:
  - raw/2026-11-27-foundry-routing-and-agent-insights/source.md
  - https://azure.microsoft.com/en-us/updates?id=581398
  - https://azure.microsoft.com/en-us/updates?id=581393
  - https://azure.microsoft.com/en-us/updates?id=581388
  - https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/model-router-reference
  - https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-configure
  - https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-ai-gateway
  - https://learn.microsoft.com/en-us/azure/ai-gateway/overview
status: active
---

# Foundry Model Router - Responses, Capacity, and AI Gateway

## Source summary and availability

Three Azure updates published November 23, 2026 distinguish the API protocol, capacity used after model selection, and gateway-controlled backend selection. Their availability metadata specifies November, not an exact separate rollout day.

| Update | Announced status | Delivery boundary |
| --- | --- | --- |
| [Responses API support - 581393](https://azure.microsoft.com/en-us/updates?id=581393) | GA | Call a model router deployment by name on resource or project endpoints. Deployment-free `model=auto` remains public preview. |
| [Use existing deployments - 581388](https://azure.microsoft.com/en-us/updates?id=581388) | Public preview | Reuse eligible same-resource PTU/pay-as-you-go deployments after a model is selected; eligibility and additional routing fees apply. |
| [AI Gateway model selection - 581398](https://azure.microsoft.com/en-us/updates?id=581398) | Public preview | Rank supported models behind a gateway alias while retaining gateway policy, priorities, weights, and telemetry. Gateway GA does not make selection GA. |

## Responses compatibility is not universal parameter parity

The [Responses update](https://azure.microsoft.com/en-us/updates?id=581393) lists streaming, function tools, structured outputs, image input, multi-turn continuation, stored/background responses, and built-in tools. Each response identifies the answering model. Keep tool, parameter, conversation, and model support checks in the application contract.

The [API reference](https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/model-router-reference) marks per-request controls, affinity, and routing metadata as preview, requiring `Foundry-Features: ModelRouterControls=V1Preview`. Without that header, `routing_config` is ignored. Direct routing can drop optional unsupported parameters; the preview `require_parameters` control instead restricts eligibility and fails if no model preserves the requested parameters. Do not infer this stricter behavior from protocol GA alone.

## Direct routing: model choice, then capacity

Under the [existing-deployment preview](https://azure.microsoft.com/en-us/updates?id=581388), the selected model is served in this order:

1. Eligible customer-owned PTU deployment for an OpenAI model.
2. Eligible customer-owned pay-as-you-go deployment for a pool model.
3. Router-managed capacity.

Eligibility requires the same Foundry resource and the exact supported model name/version. A Data Zone Standard router accepts only eligible Data Zone deployments; Auto processes as Global Standard. Retryable capacity errors advance through this order for the same model before failover to another ranked model. Both router limits and the selected deployment's applicable limits matter. [Configuration guidance](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-configure)

The routing fee remains additional to committed PTU charges or pay-as-you-go usage. The response's model name does **not** reveal whether customer-owned or router-managed capacity handled the request; do not treat it as sufficient evidence of PTU utilization or chargeback.

## Gateway routing: ranking within an explicit policy

[Dedicated AI Gateway](https://learn.microsoft.com/en-us/azure/ai-gateway/overview) is distinct from API Management service's AI gateway capabilities: they share the resource provider but use different resource types. Do not transfer APIM SKU assumptions to this feature.

In the [gateway selection preview](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-ai-gateway), Balanced, Quality, or Cost sets the ranking objective. **Model first** considers all priority groups, using the highest-priority placement of the chosen model. **Priorities first** restricts model choice to the highest-priority group. Weights split traffic among backends of that model at that priority. Model router ranks; the gateway backend serves.

| Boundary | Consequence |
| --- | --- |
| Supported model pool | Compatible hosting does not make every model eligible for automatic selection. |
| Shared API format | The alias exposes only formats common to all backends; a Chat Completions-only member removes Responses for the alias. Claude and OpenAI cannot currently share an automatically selected alias. |
| Parameter handling | A parameter unsupported by the selected gateway backend errors; it is not adapted as on direct routing. |
| Responses continuation | `previous_response_id` pins a follow-up to the prior backend without reranking; direct model router ranks each turn. |
| Pricing | Gateway selection has no model router fee during preview, unlike direct routing. Gateway charges and backend usage remain; current docs state router charges will apply when selection becomes GA. |
| Preview scope | Verify region, backend credentials/network access, shared protocol, and API version `2026-11-01`; preview terms do not provide a production SLA for selection. |

## Partner application

**Interpretation:** Assess routing as a versioned workload policy, not an automatic savings promise. Benchmark representative tasks and failure cases; verify authorized model sets, residency, conversation/tool behavior, real capacity consumption, latency, and total gateway/router/backend cost. Decide explicitly whether preferred capacity or per-prompt model ranking takes precedence.

No routing calls, deployments, policy changes, or cost measurements were performed. Availability is capability-specific and current as of November 27, 2026.

## Related pages

- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [AI Gateway Pattern](../10-Notes/concepts/ai-gateway-pattern.md)
- [APIM AI Gateway Capabilities](azure-api-management-ai-gateway-capabilities.md)
- [Agent Configuration Optimization](../10-Notes/concepts/agent-configuration-optimization.md)
- [Foundry Agent Insights](foundry-agent-insights.md)
- [Azure OpenAI Workloads](../100-Crucible/DataAISolutionArea-AzureOpenAI.md)
