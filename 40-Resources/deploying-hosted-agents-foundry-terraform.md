---
title: Deploying Hosted Agents in Foundry Agent Service via Terraform
type: resource
created: 2026-10-03
updated: 2026-10-03
tags:
  - microsoft-foundry
  - terraform
  - iac
  - agents
  - azure
status: active
sources:
  - raw/2026-10-03-foundry-hosted-agents-terraform/source.md
---

# Deploying Hosted Agents in Foundry Agent Service via Terraform

Microsoft Foundry Blog walkthrough (2026-10-01) for folding Foundry
**hosted agent** deployment into an existing Terraform/IaC pipeline using
the AzAPI provider's `azapi_data_plane_resource`, instead of manual SDK
calls or REST API scripts. Explains the control-plane/data-plane split
behind Foundry (project and connections are ARM control-plane resources;
the logical agent itself is created through the project's data-plane API),
a Day‑1/Day‑n deployment workflow for organizations that separate
platform-team-owned Foundry infrastructure from application-team-owned
agent code, and a working Terraform resource sketch plus a linked sample
repository (`JFolberth/simple-hosted-agent-deploy-azapi`).

## Why It Matters for Partners

- Gives partners delivering Foundry agent platforms a concrete pattern for
  bringing hosted-agent deployment under the same IaC discipline
  (versioning, code review, remote state, CI/CD) customers already require
  for the rest of their Azure estate — a common gap when agent platforms
  bypass IaC via ad hoc SDK/REST scripts.
- Names the operating model many enterprise engagements need: a
  centralized platform team owns the Foundry account/project/model/
  connections lifecycle while application teams independently build,
  publish, and deploy their own agent container versions — a reusable
  responsibility-split story for platform-engineering proposals.
- Documents the control-plane vs. data-plane distinction behind Foundry
  agents (ARM resources vs. `azapi_data_plane_resource`) that partners
  need to get right when designing Terraform module boundaries, RBAC, and
  approval gates for agent deployments.
- Flags concrete production gaps the sample does not solve out of the box
  — remote state, access controls, image-version promotion/validation,
  cleanup — giving partners a checklist for hardening the linked sample
  into a production-ready delivery accelerator rather than presenting it
  as one.
- Cross-references the author's companion post on deploying Foundry hosted
  agents directly from source (non-registry path), useful when a customer's
  container-registry strategy differs from this example's assumptions.

## Source

[Deploying hosted agents in Foundry Agent Service via Terraform](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/deploying-hosted-agents-in-foundry-agent-service-via-terraform/4560435) — Microsoft Foundry Blog, 2026-10-01. Sample repository: https://github.com/JFolberth/simple-hosted-agent-deploy-azapi.

## Related Pages

- [[azure-ai-foundry]]
- [[microsoft-foundry-agent-selection]]
