---
title: Azure Local Running-Cluster Review
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [azure-local, operations, resiliency, storage, security, change-management]
sources:
  - raw/2026-11-27-azure-local-running-cluster-antipatterns/source.md
  - https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143
  - https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610
  - https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-secure-baseline?view=azloc-2611
  - https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-thin-provisioning-23h2?view=azloc-2611
  - https://learn.microsoft.com/en-us/azure/azure-local/update/update-best-practices?view=azloc-2611
  - https://learn.microsoft.com/en-us/azure/azure-local/manage/trusted-launch-vm-overview?view=azloc-2610
status: active
---

# Azure Local Running-Cluster Review

## Source summary

[Azure-Hacker's November 26, 2026 companion post](https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143) examines choices that can look healthy until maintenance, repair, backup, or failure creates competing demands. Its scope is connected, multi-node Azure Local, adapted to topology, release, VM type, and workload. The examples are operating risks, not a universal defect list or a declaration that every described configuration is unsupported.

## Ten operating checks

This paraphrased review checklist is derived from the source; none of these drills was performed by this ingestion.

| Risk | Evidence that addresses it |
| --- | --- |
| Cluster redundancy mistaken for service recovery | Agreed workload RTO/RPO, independent failure-domain map, surviving-node capacity, and a timed end-to-end user-flow drill. |
| Recovery depends on the failed cluster | Repository, catalog, recovery tooling, credentials, and keys reachable with the source instance unavailable; isolated restore and current backup coverage. |
| Generic SMB policy overrides the baseline | Resultant policy and active connection measurements; an approved, version-specific exception with security/platform owners, compensating controls, and expiry. |
| Deduplication assumed to be free capacity | One representative volume benchmarked during deduplication, backup, repair, and workload peaks; staggered schedules and measured physical growth. |
| CSV free space mistaken for repair reserve | Actual pool allocation, thin commitments, unallocated drive-repair reserve, routed capacity alerts, and a separate procurement lead-time trigger. |
| Host intent succeeds but switch QoS is incomplete | Correlated host, switch-queue, CSV, and application measurements on both switched S2D paths under representative contention and controlled path loss. |
| A second lifecycle manager added for one move | Explicit VM type and sole lifecycle owner; a supported mobility/recovery path and destination checks for management, backup, monitoring, user access, and data loss. |
| Rehearsal does not represent the change | Lab reproduces relevant adapters, firmware, storage path, policies, workload, and failure mode; test VMs on production hosts are not a platform lab. |
| Update completion mistaken for workload health | Readiness, capacity, and job-coordination checks; timestamped workload measurements during servicing; stop criteria before expanding production batches. |
| Telemetry collected without operational ownership | Actionable thresholds, tested on-call delivery, missing-signal monitoring, ingestion/retention ownership, and a common incident timeline. |

## Technical boundaries

**Storage topology matters.** For switched S2D, validate applicable DCB/QoS, priorities, PFC/ETS, VLANs, MTU, and independent paths using the actual transport and supported switch guidance. Successful Network ATC intent is not switch validation. SAN-only storage needs its own iSCSI/FC, zoning, persistent multipath, and array checks; do not apply an S2D repair/fabric recipe to SAN volumes. The source explicitly distinguishes PFC pause frames, CSV pauses, and event 5120: none alone proves the other or establishes root cause. [Companion post](https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143)

**Capacity measures are not interchangeable.** Thin logical volume capacity does not reserve physical pool capacity. Reviewed documentation recommends the default 70% pool-utilization alert; this is not the first article's approximate usable-capacity purchasing trigger. The source's reserve of one capacity drive per server, capped at four drives, addresses drive repair, not guaranteed whole-node recovery. Deduplication savings and deleted-space reclamation are not immediate capacity guarantees. [Thin provisioning](https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-thin-provisioning-23h2?view=azloc-2611), [companion post](https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143)

**Security ownership is not a performance toggle.** External SMB signing and in-cluster encryption are separate baseline controls, not two signatures per packet. Reviewed documentation permits individual-setting customization with drift control from 2610 after baselines are properly applied; use the supported intent/cmdlet path, not generic GPO or registry overrides. Do not disable signing or encryption as a blanket optimization. [Security defaults](https://learn.microsoft.com/en-us/azure/azure-local/manage/manage-secure-baseline?view=azloc-2611)

**Mobility, replication, and HA differ.** The reviewed operations matrix allows intra-cluster live migration but not cross-cluster live migration for Azure Local VMs enabled by Arc. The source distinguishes eligible VMM-managed VMs from Azure-managed VMs and rejects dual management. Hyper-V Replica is asynchronous recovery, not automatic application HA; destination management and VM-specific support must be rechecked. Trusted Launch requires its guest-state key, lacks ASR support, and becomes locally managed after a restore to another instance. [Operations matrix](https://learn.microsoft.com/en-us/azure/azure-local/manage/virtual-machine-operations?view=azloc-2610), [Trusted Launch](https://learn.microsoft.com/en-us/azure/azure-local/manage/trusted-launch-vm-overview?view=azloc-2610), [companion post](https://techcommunity.microsoft.com/blog/azureinfrastructureblog/azure-local-10-anti-patterns-that-quietly-break-a-running-cluster/4577143)

**A green update is not user-flow evidence.** Reviewed guidance calls for representative test clusters, coordinated Azure Local updates, healthy readiness, and small maintenance batches; investigate partial failures instead of blind retries. The source adds measurement during overlapping drains, repair, backup, and workload activity. [Update best practices](https://learn.microsoft.com/en-us/azure/azure-local/update/update-best-practices?view=azloc-2611)

## Partner application and limits

Start a Day-2 assessment with one critical workload and one upcoming change. Record the setting owner, supported change path, acceptance metric, baseline, and last recovery result; give gaps an owner and follow-up date. This is an interpretive partner service pattern, not proof of customer compliance, availability, or savings.

The post's separate Ignite/release examples concerning confidential VMs, migration tooling, MPIO fixes, and Azure Monitor health models were not independently revalidated. Vendor validation listings and source anecdotes do not replace a customer restore or benchmark. No infrastructure, backups, switches, policies, keys, or update jobs were changed.

## Related pages

- [Azure Local](../10-Notes/entities/azure-local.md)
- [Deployment Readiness](azure-local-deployment-readiness.md) - Companion pre-procurement and go-live checks.
- [Workload Recovery Evidence](../10-Notes/concepts/workload-recovery-evidence.md)
- [Distributed Hybrid Infrastructure](distributed-hybrid-infrastructure-2026.md)
