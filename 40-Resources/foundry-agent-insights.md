---
title: Foundry Agent Insights
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [microsoft-foundry, agents, observability, traces, evaluation, optimization]
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - raw/2026-11-27-foundry-routing-and-agent-insights/source.md
  - https://azure.microsoft.com/en-us/updates?id=581363
  - https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/agent-insights
  - https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights
status: active
---

# Foundry Agent Insights

## Source summary

The [November 23, 2026 Azure update](https://azure.microsoft.com/en-us/updates?id=581363) announces Agent insights in Microsoft Foundry as **GA**. Insights analyze agent traces to identify recurring patterns, group related issues, and support evidence-led prioritization. The availability field specifies November 2026; it is not a guarantee of every regional or agent configuration.

[Reviewed Learn guidance](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/agent-insights) describes representative traces, affected versions, likely causes, and proposed actions. Categories include reliability, hallucinations, token/cost spikes, latency, tool failures, and custom priorities. Findings are AI-generated decision support, not authoritative diagnoses or guaranteed real-time monitoring.

## Telemetry and access prerequisites

- Use a supported Foundry project/region, a connected Application Insights resource, and a supported GPT-5-or-newer GPT judge deployment.
- Verify recent, representative healthy and failing traces, stable agent/version identities, the analysis window, and useful model/tool/workflow spans. Missing evidence cannot be reconstructed by analysis.
- Interactive users need the agent-type-specific role: Foundry User for prompt agents or Foundry Project Manager for hosted agents. Telemetry query access is separate.
- Protected `AppGenAIContent` requires Privileged Monitoring Data Reader or equivalent protected-content access at the queried resource/workspace scope. Authorize collection and analysis under customer data policies.
- For application-only runs, separately grant the caller's Foundry API access and the project's managed identity's model/telemetry access; caller permission does not confer analysis permission.

These requirements come from the [insights setup guide](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/agent-insights). Model availability, quota, roles, and retention remain deployment-specific.

## Review before remediation

Compare highlighted failing traces with healthy controls. Confirm version, grouping, business impact, ownership, and the proposed cause. Convert confirmed behavior into an evaluation target or route dependency/platform defects to their owner rather than patch the agent's prompt.

Retrieving existing findings through documented Foundry tools is read-only; it does not start analysis, apply fixes, or change status. An empty result is not a health verdict. Scans and recurring analysis are separate, potentially billable operations. A persistent schedule can incur model charges after the initiating client closes. [Review and operation boundaries](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/agent-insights)

## Optimizer Release Scope and Execution Safety

The [fix-insights optimizer workflow](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/optimize-agents-from-insights) was labeled **preview** in the November 27 review, for prompt agents without the Microsoft Copilot harness. Hosted agents use separate Toolkit/CLI workflows. The current baseline is unchanged until a candidate is reviewed and promoted.

The [Ignite Book of News](https://news.microsoft.com/events/ignite/2026/book-of-news/)
separately announces Agent Optimizer GA. Scope/version equivalence with this
workflow is unconfirmed; retain both sources and verify the exact delivery path.
See the [event reconciliation note](ignite-2026/microsoft-foundry.md#release-status-reconciliation).

However, evaluations can invoke live tools and cause irreversible changes **before promotion**. Use read-only tools or isolated test resources and permissions, not merely an isolated compute environment. Evaluation calls can incur charges and throttling.

Review **Insights improved** separately from the general-quality regression check: the documented check can pass with up to **2% regression** if at least one selected insight improves. This is a service acceptance rule, not automatic customer approval. Candidates in this workflow change instructions/function-tool descriptions, not the model or skills.

## Partner application and limits

**Interpretation:** Offer a bounded agent-operations review: verify trace readiness and authorized content access, inspect recurring issues, assign owners, create regression coverage, and separately approve any billable scan, candidate execution, or deployment.

Generated insights can omit real issues, merge unrelated behavior, or infer the wrong cause. They complement evaluations and Azure Monitor; they do not replace security, safety, compliance, or infrastructure monitoring. No customer traces, scans, schedules, optimizer runs, role assignments, or deployments were accessed or changed.

## Related pages

- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Microsoft Foundry Agent Optimizer](microsoft-foundry-agent-optimizer.md)
- [Agent Configuration Optimization](../10-Notes/concepts/agent-configuration-optimization.md)
- [AI Agent Lifecycle](../10-Notes/concepts/ai-agent-lifecycle.md)
- [Foundry Model Router](foundry-model-router-responses-capacity-gateway.md)
- [Data and AI Workloads](../100-Crucible/DataAISolutionArea.md)
