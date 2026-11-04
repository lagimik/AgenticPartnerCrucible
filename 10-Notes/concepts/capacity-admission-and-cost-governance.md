---
title: Capacity Admission and Cost Governance
type: concept
created: 2026-11-02
updated: 2026-11-02
tags: [capacity, observability, finops, governance]
sources:
  - https://learn.microsoft.com/en-us/fabric/enterprise/surge-protection
  - https://learn.microsoft.com/en-us/fabric/enterprise/capacity-overage-overview
  - https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-operation-events
status: active
---

# Capacity Admission and Cost Governance

Shared capacity has three distinct operating decisions: **what to admit**,
**what excess usage to pay for**, and **what evidence to observe**. A setting
that addresses one decision does not automatically solve the others.

Fabric illustrates the distinction: surge protection can reject new background
work, capacity overage pays for eligible throttling relief without increasing
hardware resources, and event streams reveal aggregate and operation-level
consumption.

## Reusable Decision Pattern

1. Establish workload ownership, service objectives, and baseline demand.
2. Select admission and recovery thresholds with explicit business tradeoffs.
3. Decide whether occasional paid relief is preferable to delay or rejection.
4. Correlate utilization, rejection, and cost evidence; test recovery paths.
5. Resize, isolate, or optimize sustained demand rather than repeatedly paying
   for emergency relief.

**Interpretation:** evaluate limits by their enforcement interval and treatment
of in-flight work, not their UI label. Soft thresholds are not hard spending
caps, and preventing throttling is not the same as improving query performance.

## Related

- [Fabric implementation and source caveats](../../40-Resources/fabric-capacity-observability-and-protection.md)
- [Direct Lake design](../../40-Resources/fabric-direct-lake-design.md)
