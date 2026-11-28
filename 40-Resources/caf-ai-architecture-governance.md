---
title: CAF Architecture and Governance for AI
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [cloud-adoption-framework, azure-landing-zones, ai-governance, architecture, reliability]
sources:
  - raw/2026-11-27-caf-ai-architecture-governance/source.md
  - https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/ready?tabs=conceptual
  - https://learn.microsoft.com/en-us/azure/foundry/how-to/model-deployment-policy?tabs=cli
  - https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview
status: active
---

# CAF Architecture and Governance for AI

## Source summary

[Architecture and governance for AI](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/ready?tabs=conceptual) places AI in the existing Azure landing-zone architecture. Start with the established governance and connectivity baseline, extending it for approved services and models instead of creating a parallel AI governance model. AI-specific management groups are generally unnecessary; this is not a prohibition on requirement-driven tailoring.

The stated outcome is an **updated governance baseline** supporting the AI technologies the organization plans to use. This is architecture guidance, not an implementation, compliance certification, or product release announcement. Reviewed page metadata dates the document October 14, 2026 and its update October 15; capture occurred November 27.

## Responsibility and design boundaries

| Area | CAF guidance and ownership |
| --- | --- |
| Platform structure | Platform teams retain shared management groups, identity, management, security, and connectivity. Extend the existing controls where AI introduces a genuine gap. |
| Policies | Start with the platform baseline and add applicable policies for approved Foundry models/tools, AI Search, and infrastructure. Assign through the existing hierarchy. |
| Workload structure | Workload teams own their landing zones and environments; use one or more subscriptions for the required isolation, governance, cost, and service-specific quota boundaries. |
| Workload placement | Internet-facing workloads generally use Online; internal workloads generally use Internal/Corp. Follow the organization's established boundaries rather than an AI-only hierarchy. |
| Networking | Reuse shared protection and connectivity. Choose ExpressRoute or VPN by performance and availability needs; validate the actual exposed and hybrid paths. |
| Regional design | Check approved model/service availability, capacity, data residency, and retrieval-data proximity before selecting primary and secondary regions. |
| Reliability | Apply existing business-continuity standards. Multiregion adds cost and complexity; secondary regions need the models and retrieval data required for recovery. |
| Enterprise data | Use governed data and approved integration patterns, potentially including Fabric, rather than separate integration designs for every AI workload. |

These are paraphrased from the [CAF Ready guidance](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/ready). Conceptual integrations with Foundry, Copilot Studio, Fabric, Microsoft 365, Agent 365, Entra, Defender, and Purview do not prove identical permissions, universal feature coverage, or licensing.

## Control effectiveness is a separate question

The [Foundry policy guide](https://learn.microsoft.com/en-us/azure/foundry/how-to/model-deployment-policy?tabs=cli) marks approved-model and eligibility definitions as GA, but evaluates them **at deployment time**. They do not filter every model router request. Constrain routing sets and design runtime authorization separately.

Policy assignment alone is not enforcement evidence: Audit is not Deny; eligibility toggles default to false; asset IDs use prefix matching that can unintentionally broaden approval. Verify current definitions, parameters, effect, scope, publisher/asset IDs, and both permitted and rejected deployment cases. Allow for propagation and later compliance evaluation.

The [DDoS overview](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview) describes enhanced L3/L4 protection for supported virtual-network/public-IP architectures. Layer-7 web protection needs a WAF. Do not translate the CAF network recommendation into a promise that one plan protects every managed AI endpoint or stops application-level abuse.

## Partner application

**Interpretation:** Build an AI readiness engagement around the baseline delta, not a greenfield hierarchy. Produce a service/model approval list, platform/workload responsibility map, inherited-control and exception record, connectivity/residency design, region/capacity check, and recovery validation plan.

Test control effects and workload recovery against customer-defined acceptance criteria. A model deployment or conceptual secondary region is not proof that identity, retrieval data, network access, quota, and the full business flow recover together. Accelerator naming or reference diagrams do not establish customer production readiness.

No Azure resources, policies, networking, deployment, or recovery tests were accessed or changed. Other linked implementations and architecture downloads were not tested.

## Related pages

- [Cloud Adoption Framework](../10-Notes/entities/cloud-adoption-framework.md)
- [AI Governance](../10-Notes/concepts/ai-governance.md)
- [Policy to Proof](policy-to-proof-ai-governance.md)
- [Digital Sovereignty Adoption](digital-sovereignty-adoption-caf.md)
- [Foundry Model Router](foundry-model-router-responses-capacity-gateway.md)
- [Fabric Agent Platform Selection](fabric-data-agents-platform-selection.md)
- [Workload Recovery Evidence](../10-Notes/concepts/workload-recovery-evidence.md)
- [Landing Zones Practice Building](../100-Crucible/AzureInfrastructureSolutionArea-LandingZones.md)
