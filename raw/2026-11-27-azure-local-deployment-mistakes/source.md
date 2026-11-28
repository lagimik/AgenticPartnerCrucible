---
title: "Source capture - Azure Local deployment mistakes"
source_url: https://techcommunity.microsoft.com/blog/AzureInfrastructureBlog/azure-local-10-mistakes-that-can-derail-your-deployment-before-it-starts/4569922
captured: 2026-11-27
published: 2026-11-03
source_updated: 2026-11-10
source_version: "11.0"
author: Azure-Hacker
publisher: Microsoft Community Hub - Azure Infrastructure Blog
capture_type: Public article metadata and paraphrased source summary
---

# Provenance

The user supplied the public article URL. The complete article was reviewed in three successive page segments on November 27, 2026. The page identifies the author as Azure-Hacker with a Microsoft badge, publication on November 3, and an update on November 10, version 11.0. This capture preserves metadata and a paraphrased summary, not the full article, diagrams, commands, or anonymized customer stories.

# Source summary

The author frames Azure Local as a validated hybrid platform with Azure governance and a coordinated solution lifecycle, not a drop-in hypervisor substitution. The ten field lessons concern platform fit; buying hardware before architecture; Azure landing-zone placement; DNS and outbound connectivity; conflicting or undersized IP ranges; late AD, firewall, and proxy preparation; insufficient storage/network headroom; testing platform changes in production; updates without readiness checks; and missing Day-2 monitoring and recovery plans.

The proposed delivery sequence is to agree the workload and VM management model before procurement, validate the exact hardware and NIC roles, settle Azure placement and permissions, and bring network, identity, security, and operations owners into design. The post treats infrastructure DNS and many address/placement decisions as effectively permanent under the documented support model at capture time.

The article separates infrastructure DNS from workload logical-network and guest DNS changes. It describes post-deployment proxy changes, Arc gateway enablement, and public-to-private connectivity transitions as release-2610 previews, not unrestricted configuration edits. Existing AKS clusters need separate attention after proxy changes; the post distinguishes Azure Local recreation guidance from an AKS in-place refresh preview.

Storage sizing must fund resiliency copies, unallocated repair reserve, and growth. The author's purchasing trigger around 70% usable capacity is not the same measure as the second article's default thin-provisioning alert at 70% physical pool utilization. Hardware, OEM firmware, Network ATC intents, and future SDN requirements must be validated together.

Before and after servicing, the author recommends health/readiness evidence and workload checks. Monitoring needs actionable alerts, owners, and cost planning. Recovery requires reconciled backup scope, tested RTO/RPO, accessible BitLocker and Trusted Launch guest-state keys, and VM-type-specific protection support.

# Evidence boundaries

- Field engagement counts, customer outcomes, list-price arithmetic, and cost anecdotes are the author's reported experience, not independently verified estimates for a customer.
- Do not reuse the post's historical prices, Azure Hybrid Benefit assumptions, support window, or release-specific networking limits without checking current documentation and the customer's agreement.
- No customer environment was assessed; no deployment, policy, network, update, key export, backup, or recovery command was executed.

# Supporting documentation reviewed

- [Proxy updates](https://learn.microsoft.com/en-us/azure/azure-local/manage/update-proxy-settings?view=azloc-2611): preview, Azure Local 2610 or later, coordinated machine/resource-bridge changes, complete replacement bypass lists, and separate handling for existing AKS clusters.
- [Supported VM operations](https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610): Azure-owned lifecycle actions, explicitly permitted local operations, and no cross-cluster live migration for Azure Local VMs enabled by Arc.
- [Update best practices](https://learn.microsoft.com/en-us/azure/azure-local/update/update-best-practices?view=azloc-2611): representative test clusters, readiness, approved coordinated updates, and staged production batches.
- [Trusted Launch recovery](https://learn.microsoft.com/en-us/azure/azure-local/manage/trusted-launch-vm-overview?view=azloc-2610): all VM files and guest-state key required; ASR unsupported for this VM type; a restore to another instance is locally managed; automatic key backup remains preview.

The article's broader reference list was inspected for discovery, not exhaustively revalidated. Linked documentation can change independently of this source capture.
