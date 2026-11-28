---
title: Azure API Management AI Gateway Capabilities
type: resource
created: 2026-09-05
updated: 2026-11-27
tags: [azure-api-management, ai-gateway, mcp, model-routing, governance]
sources:
  - https://learn.microsoft.com/en-us/azure/ai-gateway/overview
  - https://learn.microsoft.com/en-us/azure/api-management/genai-gateway-capabilities
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Azure API Management AI Gateway Capabilities

Microsoft Learn overview of APIM controls for language models, agents, MCP servers, A2A APIs, and self-hosted endpoints.

## Capability Map

- Import OpenAI-compatible, Anthropic Messages, Google Vertex AI, and passthrough model APIs.
- Expose multiple providers through a unified OpenAI-compatible model API.
- Govern remote MCP servers and A2A agent APIs.
- Authenticate backends with managed identity and authorize consumers centrally.
- Apply token limits and quotas per subscription, IP, or policy-defined key.
- Improve cost and latency through semantic caching.
- Balance traffic across endpoints and add observability, logging, and tracing.

This capability map covers AI gateway features within API Management service;
feature availability varies by APIM tier. The [November dedicated AI Gateway
overview](https://learn.microsoft.com/en-us/azure/ai-gateway/overview) describes
a distinct product sharing the `Microsoft.ApiManagement` provider but using
different resource types. Existing APIM AI workloads remain supported; do not
transfer this capability map's SKU assumptions to the dedicated product.

## Related Pages

- [Foundry Model Router and AI Gateway Selection](foundry-model-router-responses-capacity-gateway.md) - Separate selection preview, alias constraints, and gateway/backend billing.
- [[ai-gateway-pattern]]
- [[ai-governance]]
- [[model-context-protocol-mcp]]
