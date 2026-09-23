---
title: Fabric Real-Time Hub Event Architecture
type: resource
created: 2026-09-18
updated: 2026-09-18
tags: [microsoft-fabric, real-time-hub, business-events, eventhouse, activator, event-driven-architecture]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/from-business-events-fabric-events-and-azure-events-to-real-time-hub/5365864
  - raw/2026-09-18-fabric-real-time-hub-events/source.md
status: active
---

# Fabric Real-Time Hub Event Architecture

Eight-part Microsoft Fabric series for designing publisher-to-Real-Time-Hub-to-consumer event flows.

## Event Pillar Decision

| Publisher owns | Use |
| --- | --- |
| A meaningful business condition | Business Events |
| Fabric platform activity | Fabric Events |
| Azure Storage activity | Azure Events |

## Design Guidance

- Begin with a factual, versioned schema contract.
- Publish near the workload that detects the condition.
- Keep the event independent from any single consumer action.
- Use Activator for immediate rules and actions.
- Use Eventhouse for durable KQL history, investigation, trends, and dashboards.
- Use Eventstream when streaming transformation is required.
- Make consumers idempotent and include event and correlation identifiers.
- Keep event chains short; use explicit orchestration when strict ordering, shared state, or compensation is required.

## Partner Motion

- Event-opportunity discovery workshop
- Event-pillar and consumer architecture assessment
- Schema registry, ownership, and compatibility governance
- Polling-to-event modernization
- Small lighthouse implementation followed by fanout
- Managed monitoring, retry, and failure operations

## Related Pages

- [[microsoft-fabric]]
- [[fabric-authoring-consumption-operations]]
- [[fabric-cicd-resources]]

