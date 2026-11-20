---
title: Azure API Management AI Gateway Capabilities
type: resource
created: 2026-09-05
updated: 2026-11-20
tags: [azure-api-management, ai-gateway, mcp, model-routing, governance]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580080
  - https://learn.microsoft.com/en-us/azure/ai-gateway/ai-gateway-resource
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

The earlier overview describes the AI gateway capabilities as an APIM extension,
not a separate Azure offering. Feature availability varies by APIM tier.

## November 2026 Dedicated Gateway

[Update 580080](https://azure.microsoft.com/en-us/updates?id=580080) now announces
Azure AI Gateway as a GA fully managed service. Its dedicated resource replaces
the earlier APIM `AIGateway` SKU representation, not other APIM SKUs. The older
overview's scope does not establish parity for the new resource: migration
guidance has separate private-endpoint and content-safety limitations.
See [GA and resource migration](azure-ai-gateway-ga.md) for the January 15, 2027
retirement deadline, identity/client cutover, and source differences.

## Related Pages

- [Azure AI Gateway](../10-Notes/entities/azure-ai-gateway.md)
- [Agent 365 Runtime Governance Integration](agent-365-apim-runtime-governance.md)
- [[ai-gateway-pattern]]
- [[ai-governance]]
- [[model-context-protocol-mcp]]
