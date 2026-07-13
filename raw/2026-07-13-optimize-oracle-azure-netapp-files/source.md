# Optimize Oracle Workloads on Azure with Azure NetApp Files

**Source:** https://techcommunity.microsoft.com/blog/azurestorageblog/optimize-oracle-workloads-on-azure-with-azure-netapp-files/4532644
**Captured:** 2026-07-13
**Issue:** lagimik/AgenticPartnerCrucible#6

---

This article shows how Azure NetApp Files optimizes Oracle on Azure with high-performance storage, simplified deployment, and integrated data protection.

## Key Advancements

1. **Flexible service level capacity pools** — Capacity and throughput tuned independently. Start with 128 MiB/s baseline, scale up to 5x Ultra per 1 TiB. Reduces costs 10–40%.

2. **Oracle Direct NFS (dNFS)** — Database-optimized NFS client built into Oracle Database. Predictable performance, simpler operations, modernized Oracle environments without changing proven NFS-based operating models.

3. **Application volume group for Oracle** — Automated deployment of Oracle data, redo, archive, and backup volumes in one workflow. Applies Oracle-aware layout and placement guidance.

4. **Availability-zone-aware volume placement** — Oracle VMs and ANF volumes aligned in same AZ to reduce latency.

5. **Enhanced data protection** — Snapshots, backup, cross-zone replication, cross-region replication. RPO as low as 10 minutes with built-in replication.

6. **Migration assistant** — ONTAP-based volumes migrated to ANF using block-level replication, preserving file structure, permissions, and snapshots.

7. **Short-term clones** — Snapshots turned into writable, space-efficient clones for test/dev/reporting.

8. **Storage with cool access** — Inactive data tiered automatically to optimize cost.

9. **Oracle Database@Azure integration** — ANF as backup target and source for rapid test/dev refreshes.

## Application Volume Group Enhancements

- AZ volume placement for latency minimization
- Data protection volume group creation for DR
- Standard network features for best performance
- Data and log volumes on separate storage endpoints

## VM IO Advantage

Network IO is not throttled by Azure VMs like managed disk is. Larger storage bandwidth with network-connected storage. Same or better performance with smaller VM SKU — positive consequences for licensing.

## Summary

Shifts conversation from "Can Oracle run well on ANF?" to "How can Oracle environments on Azure become easier to operate, protect, and scale?"
