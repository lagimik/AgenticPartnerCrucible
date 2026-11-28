---
title: "Source capture - Foundry routing and agent insights updates"
captured: 2026-11-27
publisher: Microsoft Azure Updates and Microsoft Learn
capture_type: Public update metadata and paraphrased source review
sources:
  - https://azure.microsoft.com/en-us/updates?id=581398
  - https://azure.microsoft.com/en-us/updates?id=581393
  - https://azure.microsoft.com/en-us/updates?id=581388
  - https://azure.microsoft.com/en-us/updates?id=581363
---

# Provenance and identity

The user supplied four unique Azure Updates IDs; the repeated `581388` link was processed once. All four public pages returned the Azure Updates application shell without item text. After live schema discovery, the public Microsoft Release Communications MCP endpoint returned complete records through `get_azure_update_by_id`. This capture preserves their identities, metadata, and paraphrased findings, not full publisher descriptions or documentation code.

| ID and public item | Exact update title | Created and modified (UTC; identical per record) | Status | Availability metadata |
| --- | --- | --- | --- | --- |
| [581398](https://azure.microsoft.com/en-us/updates?id=581398) | Public Preview: Use model router with AI Gateway | 2026-11-23T20:15:53.5839928Z | In preview | Preview, November 2026 |
| [581393](https://azure.microsoft.com/en-us/updates?id=581393) | Generally Available: Model router now supports the Responses API protocol in Microsoft Foundry | 2026-11-23T20:28:24.2431546Z | Launched | General Availability, November 2026 |
| [581388](https://azure.microsoft.com/en-us/updates?id=581388) | Public Preview: Use your model deployments with model router in Microsoft Foundry | 2026-11-23T20:29:36.598698Z | In preview | Preview, November 2026 |
| [581363](https://azure.microsoft.com/en-us/updates?id=581363) | Generally Available: Agent insights in Microsoft Foundry | 2026-11-23T21:10:07.590009Z | Launched | General Availability, November 2026 |

Publication dates above are post dates. The availability fields provide month precision only; they do not establish a separate exact rollout day or universal regional coverage.

# Update summaries

## 581398 - Gateway-based model selection

Model router ranks the supported models behind an AI Gateway alias, while the gateway retains authorization, policies, telemetry, priorities, and weights. Balanced, Quality, and Cost set the ranking objective. Model first considers all priority groups; Priorities first restricts selection to the highest-priority group. Weights distribute traffic between backends of the selected model. Backends can be in Foundry, provider infrastructure, other clouds, or compatible self-hosted environments, but arbitrary unsupported models do not become eligible.

## 581393 - Responses protocol

Deployment-based model router supports Responses on resource and project endpoints in GA. The update lists streaming, function tools, structured output, images, stored/background responses, conversation continuation, and built-in tools. A response identifies the serving model. Deployment-free `model=auto` remains public preview, so Responses support does not confer GA on Auto or all routing controls.

## 581388 - Existing deployment capacity

After selecting a model, model router can first use an eligible OpenAI PTU deployment, then an eligible pay-as-you-go deployment, and finally router-managed capacity. Eligibility requires the same Foundry resource and exact supported model name/version; Data Zone Standard routing accepts only eligible Data Zone deployments. Retryable errors advance through the capacity order. The routing fee is additional to existing PTU charges or pay-as-you-go usage.

## 581363 - Agent insights

Insights analyze agent traces to identify recurring patterns and group related issues with supporting evidence. Teams can investigate common failures and prioritize improvement. The update points to agent optimizer for testing possible fixes; it does not state that optimizer or automatic remediation becomes GA.

# Supporting documentation reviewed in full

- [Model router API reference](https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/model-router-reference): Auto, per-request controls, affinity, and routing metadata are preview; preview controls require the feature header. Optional unsupported parameters may be dropped on direct routing. The response identifies the model, not whether customer-owned or router-managed capacity served it.
- [Deploy and configure model router](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-configure): exact deployment eligibility, model-specific quotas, capacity fallback before model failover, Global-only Auto processing, and model/version lifecycle. Updating Auto settings can reset omitted routing/content-filter values, so examples are not safe standalone production changes.
- [Use model router with AI Gateway](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-ai-gateway): gateway GA differs from selection preview; no router ranking fee during the gateway selection preview, but gateway and backend charges remain. Alias API formats are the intersection of backend formats; Claude and OpenAI cannot currently share an automatically selected alias. Unsupported parameters error instead of being adapted. Responses continuation with `previous_response_id` stays on the previous backend without reranking.
- [AI Gateway overview](https://learn.microsoft.com/en-us/azure/ai-gateway/overview): dedicated AI Gateway and API Management service's AI capabilities share the resource provider but use different Azure resource types; existing APIM AI workloads remain supported.
- [Agent insights](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/agent-insights): representative Application Insights traces, supported region and GPT-5-or-newer GPT judge, appropriate agent/user roles, and separately authorized analysis identity are required. Protected content needs protected-data query access. Generated findings can be wrong or incomplete; retrieval of existing findings is read-only and differs from scans/scheduling, which can incur model charges.
- [Fix insights with agent optimizer](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights): preview portal workflow is for prompt agents without the Copilot harness; hosted agents use separate workflows. Candidate evaluation can invoke side-effecting tools before promotion. Isolate actual resources and permissions. General-quality checks can pass with up to 2% regression when at least one selected insight improves; review the insight outcome and regression results separately. Candidates change instructions/function-tool descriptions, not the model or skills.

# Evidence and operation boundaries

No Azure tenant, deployment, routing request, insights scan, schedule, optimizer run, role assignment, or billing action was accessed or changed. No pricing amounts, workload savings, latency gains, or production readiness were independently measured. Current model pools, regions, quotas, pricing, protected-content handling, and preview terms must be checked before implementation. The November 27 signal report remains unchanged.
