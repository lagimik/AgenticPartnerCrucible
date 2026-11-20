---
title: Azure Agent Grid
type: entity
created: 2026-11-20
updated: 2026-11-20
tags: [agent-grid, network-security, workload-identity, zero-trust]
sources:
  - https://azure.microsoft.com/en-us/updates?id=580684
  - https://learn.microsoft.com/en-us/azure/agent-grid/overview
status: active
---

# Azure Agent Grid

Azure network security for enrolled ACI and AKS agent workloads, using workload
identity, mTLS, and centrally enforced traffic policies outside the agent sandbox.
The update says public preview; Learn specifies limited-preview access and
compute/region restrictions. Attaching compute is not enrollment, and its
workload identity is not Entra Agent ID in this preview.

## Related

- [Preview Access and Enrollment Boundaries](../../40-Resources/azure-agent-grid-preview.md)
- [Azure AI Gateway](azure-ai-gateway.md)
- [Microsoft Agent 365](microsoft-agent-365.md)
- [Runtime Governance Integration](../../40-Resources/agent-365-apim-runtime-governance.md)
