---
title: Caching Correctness and Failure Budgets
type: concept
created: 2026-11-14
updated: 2026-11-14
tags: [caching, consistency, reliability, performance, databases]
sources:
  - https://techcommunity.microsoft.com/blog/azure-managed-redis/build-faster-apps-database-caching-patterns-with-azure-managed-redis/4572989
  - raw/2026-11-14-azure-managed-redis-caching/source.md
status: active
---

# Caching Correctness and Failure Budgets

Choose a caching pattern from the data's read/write behavior and business
tolerance for stale or lost values, not just its expected speed.
The [Azure Managed Redis guide](../../40-Resources/azure-managed-redis-database-caching-patterns.md)
recommends TTLs based on acceptable staleness, database fallback, and write-behind
only where losing some increments is acceptable.

## Decision Contract

**Interpretation:** Document four budgets for each cached data class:

- Freshness: how stale a value may be and how updates invalidate or replace it.
- Loss: whether buffered writes or short-lived state may be discarded.
- Recovery: what happens on cache misses, outages, and failed updates.
- Load: whether the database can sustain fallback demand and cache rebuilds.

Use expiration jitter to reduce synchronized misses and monitor hit ratio,
evictions, latency, and database utilization. Evaluate external writers
separately from changes owned by the application.

## Consistency Boundary

The source's write-through example writes the database before the cache.
**Interpretation:** This ordering does not establish a distributed transaction;
failed cache updates and concurrency still need a recovery design.
Likewise, database fallback applies to rebuildable copies, not automatically
to session state or increments that have not yet reached durable storage.

## Related Pages

- [Database Caching Patterns](../../40-Resources/azure-managed-redis-database-caching-patterns.md)
- [Azure Managed Redis](../entities/azure-managed-redis.md)
