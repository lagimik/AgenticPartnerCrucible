---
title: Azure Local
type: entity
created: 2026-11-27
updated: 2026-11-27
tags: [azure-local, azure-arc, hybrid-cloud, infrastructure]
sources:
  - https://techcommunity.microsoft.com/blog/AzureInfrastructureBlog/azure-local-10-mistakes-that-can-derail-your-deployment-before-it-starts/4569922
  - https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143
  - https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610
  - raw/2026-11-27-azure-local-deployment-mistakes/source.md
  - raw/2026-11-27-azure-local-running-cluster-antipatterns/source.md
status: active
---

# Azure Local

Azure Local is Microsoft's validated hybrid infrastructure platform, described in the [deployment field guide](https://techcommunity.microsoft.com/blog/AzureInfrastructureBlog/azure-local-10-mistakes-that-can-derail-your-deployment-before-it-starts/4569922) as integrating hardware, the operating system, Azure services, governance, and a coordinated solution lifecycle. Cloud-connected deployment and the separately offered disconnected model require different operating assumptions.

## Design distinctions

- Choose hardware, storage, Azure placement, addressing, connectivity, and Day-2 responsibilities before procurement; this is a platform decision, not only a hypervisor replacement. [Deployment guide](../../40-Resources/azure-local-deployment-readiness.md)
- An Azure Local VM enabled by Arc and a locally managed Hyper-V VM with an Arc-enabled guest have different lifecycle ownership. Use the [supported operations matrix](https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610), not the assumption that every local tool is valid for both.
- Connected multi-node, switched S2D, switchless, and SAN-backed designs need different failure-domain and storage-path evidence. Cluster health is not proof of workload recovery. [Operating review](../../40-Resources/azure-local-running-cluster-review.md)

## Related pages

- [Microsoft](microsoft.md)
- [Deployment Readiness](../../40-Resources/azure-local-deployment-readiness.md)
- [Running-Cluster Review](../../40-Resources/azure-local-running-cluster-review.md)
- [Workload Recovery Evidence](../concepts/workload-recovery-evidence.md)
- [Distributed Hybrid Infrastructure](../../40-Resources/distributed-hybrid-infrastructure-2026.md)
- [Adaptive Cloud Hosting Modernization](../concepts/adaptive-cloud-hosting-modernization.md)
