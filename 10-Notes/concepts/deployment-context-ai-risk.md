---
title: Deployment-Context AI Risk
type: concept
created: 2026-10-16
updated: 2026-10-16
tags: [ai-risk, deployment, shared-responsibility, evaluation, governance]
sources:
  - https://www.microsoft.com/en-us/security/blog/2026/10/16/managing-open-weight-model-risk-in-enterprise-deployments/
status: active
---

# Deployment-Context AI Risk

An AI system's risk depends on its model, use case, users, deployment, and
surrounding safeguards, not simply whether its weights are open or closed.
The same model used for document drafting or connected to customer-facing tools
can have different consequences and control needs.

## Separate Three Decisions

- **Model access:** What can the organization inspect, modify, and evaluate?
- **Deployment:** Which service and configuration host the model, and who
  operates the safeguards?
- **System authority:** What data, tools, permissions, and actions surround it?

These decisions interact but are not interchangeable. Managed services can host
open-weight models, and a favorable model evaluation does not establish the
safety of an application or agent.

## Risk-to-Control Mapping

The [Microsoft-NVIDIA guidance announcement](../../40-Resources/open-weight-model-risk-enterprise.md)
recommends connecting relevant risks to evaluation evidence, effective controls,
and accountable owners. Controls may belong in the model, inference environment,
application, or operating process. Revisit the mapping when models or deployments
change.

**Interpretation:** A useful assurance record should state its deployment scope
and evidence limits, rather than treating a model label or benchmark as a
universal deployment approval.

## Related Pages

- [AI Governance](./ai-governance.md)
- [AI Red-Teaming Tool Selection](./ai-red-teaming-tool-selection.md)
- [Open-Weight Model Risk in Enterprise Deployments](../../40-Resources/open-weight-model-risk-enterprise.md)
