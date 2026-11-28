---
title: "Source capture - CAF architecture and governance for AI"
source_url: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/ready?tabs=conceptual
canonical_url: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ai/ready
captured: 2026-11-27
document_date: 2026-10-14
updated_at: 2026-10-15T18:43:00Z
author: stephen-sumner
publisher: Microsoft Learn - Cloud Adoption Framework
revision: f9bfeff0abbeedcbe7be6fa0a205d6e23c4d7b30
capture_type: Public documentation metadata and paraphrased source review
---

# Provenance

The user supplied the conceptual-tab URL. The complete page was reviewed on November 27, 2026, including text and the returned descriptions of all five architecture/decision-tree tabs. Page metadata identifies October 14 as the document date and October 15 as the update timestamp; neither is a new November release announcement. The canonical URL omits the presentation-tab query.

This capture preserves provenance and paraphrased knowledge, not full documentation, diagrams, deployment code, or the linked PowerPoint. Diagram descriptions were available in the page response; no downloadable architecture artifact was opened or modified.

# Source summary

CAF places AI workloads within the same Azure landing-zone architecture and governance model as other workloads. Platform teams start with existing management groups, policy, identity, and connectivity, extending the baseline for approved AI services/models where existing controls are insufficient. AI-specific management groups are generally unnecessary, rather than categorically forbidden for every tailored design.

Platform landing zones own shared governance, identity, security, management, and connectivity. Workload teams own workload landing zones and their development, test, and production environments. Subscriptions support isolation, quota, cost, and governance boundaries. Internet-facing workloads generally follow the existing Online hierarchy; internal workloads generally follow Internal/Corp.

The platform baseline starts with landing-zone accelerator policies, then adds applicable definitions for Foundry models/tools, AI Search, and infrastructure. Existing shared networking can provide protection and approved hybrid connectivity. ExpressRoute and VPN Gateway are options selected by performance and availability requirements, not one mandatory choice for all AI workloads.

Reliability follows enterprise standards. Prepare the platform for multiple regions when justified by business continuity, but account for model/service availability and capacity, retrieval-data placement, residency, cost, and complexity. Secondary regions need the model deployments and retrieval data required to recover the workload.

Enterprise integration should expose governed organizational data through approved patterns rather than duplicate integration work in every workload. Fabric is a possible data foundation. The conceptual diagrams place Foundry capabilities within selected workloads and show enterprise integrations; they do not establish universal control coverage, licensing, automatic deployment, or product GA.

The decision tree distinguishes productivity assistants, Microsoft 365 extensibility, business-process agents, Foundry tools/apps, custom ML in Fabric or Azure Machine Learning, and infrastructure-hosted models. Hosting and serverless GPU choices still require current regional and feature-status verification.

# Supporting documentation reviewed in full

- [Foundry model-deployment policies](https://learn.microsoft.com/en-us/azure/foundry/how-to/model-deployment-policy?tabs=cli): approved-model and eligibility policies are GA and evaluated at deployment time. They do not filter model router choices on every request. Approved routing subsets and runtime controls require separate design. Asset-ID matching is prefix-based; effects, publisher/asset IDs, case, parameter names, and assignment scope must be checked against the live definition. Eligibility toggles default to false, so an unconfigured assignment does not add those restrictions. Audit differs from Deny. Propagation and compliance evaluation are not immediate.
- [DDoS Protection overview](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview): enhanced protection is designed for supported virtual-network/public-IP architectures at layers 3/4. Layer-7 web protection requires a WAF. Other services have infrastructure-level network protection; do not assume one customer DDoS plan covers every managed AI endpoint. Network and IP tiers differ in value-added features and charging.

# Interpretation and evidence boundaries

Use this source for a baseline-gap and responsibility review, not a new default AI platform hierarchy. Record approved services/models, inherited controls, remaining gaps, workload boundaries, connectivity, region/capacity/residency, and recovery evidence.

Other linked accelerator policies, policy definitions, networking services, unified-data guidance, and diagram downloads were not independently evaluated. No tenant, management group, policy assignment, deployment, network, region, or recovery exercise was accessed or changed. The source's architecture is guidance, not proof that a customer's controls enforce their intended behavior or meet compliance and availability objectives.
