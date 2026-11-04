---
title: Fabric Capacity Observability and Protection
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-fabric, capacity, observability, finops, surge-protection]
sources:
  - https://learn.microsoft.com/en-us/fabric/enterprise/surge-protection?tabs=onelake-catalog
  - https://learn.microsoft.com/en-us/fabric/enterprise/capacity-overage-overview
  - https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-overview-events
  - https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-operation-events
  - https://learn.microsoft.com/en-us/fabric/real-time-hub/explore-fabric-capacity-operation-events
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Fabric Capacity Observability and Protection

The four distinct resources submitted in issue #138 describe a coordinated
operating model: observe demand, control admission, and decide whether to pay for
temporary throttling relief. None substitutes for capacity sizing.

## Source Summary

| Surface | Behavior and boundary |
| --- | --- |
| [Capacity-level surge protection](https://learn.microsoft.com/en-us/fabric/enterprise/surge-protection?tabs=onelake-catalog) | Rejects new background operations at configured thresholds; does not cancel in-flight jobs or guarantee uninterrupted interactive requests. |
| Workspace-level surge protection | Preview control over rolling 24-hour workspace consumption; blocked workspaces reject supported new interactive and background operations; limits are soft and exceptions apply. |
| [Capacity overage](https://learn.microsoft.com/en-us/fabric/enterprise/capacity-overage-overview) | Pays off eligible excess usage when throttling would occur; documented at three times PAYG rates without increasing the SKU's compute or memory. |
| [Overview events](https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-overview-events) | Capacity summaries every 30 seconds and state-change events. |
| [Operation events](https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-operation-events) | Per-operation CU consumption, duration, throttling delay, and status; consumers must be in the source region. |

Both event setup pages require capacity-admin access and Contributor-or-higher
workspace access. Private networking and outbound access protection can restrict
cross-workspace consumption.

## Cost and Evidence Boundaries

Overage has a rolling 24-hour threshold, not a hard spending cap: five-minute
evaluation and in-flight work can overshoot it. It does not override surge
protection or remove memory and concurrency limits. Inspect actual enablement:
the documentation calls it opt-in but also says new capacities default to on.

The surge documentation is internally inconsistent about mission-critical
workspace exemption from capacity-level surge protection. Do not promise
exemption or an availability guarantee; verify actual service behavior before
setting a critical-workload policy.

The issue labels overview events GA and operation events Public Preview, but
the retrieved setup/schema pages do not explicitly reaffirm those statuses.
Verify lifecycle status before commitments; workspace-level surge protection
is explicitly marked preview in its documentation.

**Partner interpretation:** baseline the Capacity Metrics app, correlate summary
and operation signals, agree rejection/recovery and cost thresholds, and test
notifications and recovery with a capacity owner.

## Related

- [Capacity admission and cost governance](../10-Notes/concepts/capacity-admission-and-cost-governance.md)
- [Real-Time Hub event architecture](fabric-real-time-hub-event-architecture.md)
- [Direct Lake design](fabric-direct-lake-design.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
