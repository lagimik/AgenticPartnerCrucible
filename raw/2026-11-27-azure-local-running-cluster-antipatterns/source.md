---
title: "Source capture - Azure Local running-cluster anti-patterns"
source_url: https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143
captured: 2026-11-27
published: 2026-11-26
source_version: "1.0"
author: Azure-Hacker
publisher: Microsoft Community Hub - Azure Infrastructure Blog
capture_type: Public article metadata and paraphrased source summary
---

# Provenance

The user supplied the public article URL. The complete article was reviewed in three successive page segments on November 27, 2026. The page identifies Azure-Hacker with a Microsoft badge and publication on November 26, version 1.0. This is the companion to [the pre-deployment article](https://techcommunity.microsoft.com/blog/AzureInfrastructureBlog/azure-local-10-mistakes-that-can-derail-your-deployment-before-it-starts/4569922). This capture preserves metadata and a paraphrased summary rather than the full article, diagrams, or customer anecdotes.

# Source summary

The ten operating anti-patterns are equating cluster redundancy with workload resiliency; keeping the only backup and recovery dependencies in the source cluster's failure boundary; conflicting generic SMB policies; defaulting to ReFS deduplication; treating volume free space as repair reserve; incomplete switched S2D QoS; adding a competing VM management plane for mobility; unrepresentative change rehearsals; trusting update status without workload measurements; and collecting telemetry without ownership or a shared incident timeline.

The scope is connected, multi-node Azure Local, with checks adapted to release, topology, VM type, and workload. These are design/operating risks, not a blanket product-defect or unsupported-configuration list. Switched S2D requires validation of the host-to-switch storage fabric. SAN-only deployments instead require independent iSCSI or Fibre Channel paths, MPIO, and array-specific headroom; mixed deployments need both checks separately.

The author defines recovery success as a working user flow within agreed RTO/RPO. Independent power/network/storage paths, surviving-node capacity, workload dependencies, recovery catalogs, credentials, and keys must be tested together. A successful backup or vendor validation listing does not demonstrate recovery with the source cluster unavailable.

Generic SMB policy conflicts are not two signatures per packet. Baseline exceptions require supported, version-specific customization and joint security/platform ownership, not disabling signing or encryption to fix performance. Deduplication must be measured with the actual workload and job schedule; it does not guarantee purchasable capacity or immediate reversal.

Physical pool allocation and unallocated repair reserve differ from free space in a CSV. The article separates the 70% pool-utilization alert from an earlier expansion-planning trigger. The drive-repair reserve is not a guarantee of rebuilding after whole-node loss. PFC counters, CSV pauses, and event 5120 are different evidence and do not individually establish a network root cause.

Azure-managed VM lifecycle, locally managed Hyper-V with guest Arc enablement, and eligible VMM-managed VMs are distinct models. Hyper-V Replica is asynchronous recovery, not cross-cluster live migration or automatic application HA; a recovered VM's management state must be checked separately. Updates and recovery drills require representative load, user-flow measurements, documented stop criteria, and timestamped platform/network/application evidence.

# Evidence boundaries

- The source's release examples include confidential-VM restrictions, migration tooling, an MPIO servicing fix, and Azure Monitor health models; these examples were read but their separate release announcements were not independently revalidated.
- No performance savings, root cause, customer service target, vendor validation, or recovery outcome was verified by this ingestion.
- No customer settings, security controls, switches, backups, VMs, or update jobs were changed.

# Supporting documentation reviewed

- [VM operations](https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610): distinguishes allowed local actions from Azure lifecycle ownership; cross-cluster live migration is unsupported for Arc-enabled Azure Local VMs.
- [Security defaults](https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-secure-baseline?view=azloc-2611): distinguishes external SMB signing from in-cluster encryption; version 2610 adds individual-setting customization with drift control, subject to properly applied baselines.
- [Thin provisioning](https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-thin-provisioning-23h2?view=azloc-2611): logical volume size is not reserved pool capacity; default alert threshold is 70% pool utilization; deleted space is not necessarily returned immediately.
- [Update best practices](https://learn.microsoft.com/en-us/azure/azure-local/update/update-best-practices?view=azloc-2611): representative test clusters, healthy readiness, staged maintenance batches, and investigation rather than blind retries.
- [Trusted Launch](https://learn.microsoft.com/en-us/azure/azure-local/manage/trusted-launch-vm-overview?view=azloc-2610): requires guest-state-key recovery and disallows ASR for this VM type; restore to a different instance changes the management model.

The article's full reference list was not exhaustively revalidated. Current product documentation and approved customer-specific rehearsals remain necessary before implementation.
