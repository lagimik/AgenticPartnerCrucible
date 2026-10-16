---
title: Azure SRE Agent
type: entity
created: 2026-10-16
updated: 2026-10-16
tags: [azure, sre, operations, reliability, agentic-ai]
sources:
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-1-deploying-your-first-azure-/4564306
  - https://techcommunity.microsoft.com/blog/appsonazureblog/enterprise-adoption-guide-for-azure-sre-agent-part-2-from-one-team-to-enterprise/4564311
status: active
---

# Azure SRE Agent

Microsoft's Azure operations agent combines operational context and tools to
investigate issues and support bounded workflows. The October 2026 adoption
series recommends a measured, read-only first use case before reviewed
automation and broader enterprise adoption.

## Important Boundary

An agent's users share its context, memory, knowledge, and configuration.
User RBAC roles do not partition that context. Sharing and topology decisions
must account for what every user may see and what the agent may change.

## Related Pages

- [Microsoft](./microsoft.md)
- [First Deployment and Workflow Adoption](../../40-Resources/azure-sre-agent-first-deployment.md)
- [Enterprise Adoption and Governance](../../40-Resources/azure-sre-agent-enterprise-adoption.md)
- [Configuration Guide](../../40-Resources/azure-sre-agent-configuration-guide.md)
- [Incident Response Playbook](../../40-Resources/azure-sre-agent-incident-response-playbook.md)
- [Agentic Cloud Operations](../concepts/agentic-cloud-operations.md)
