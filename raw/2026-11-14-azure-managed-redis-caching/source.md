---
title: Build faster apps - database caching patterns with Azure Managed Redis
source_url: https://techcommunity.microsoft.com/blog/azure-managed-redis/build-faster-apps-database-caching-patterns-with-azure-managed-redis/4572989
publisher: Microsoft Community Hub
author: rakhithejraj
published: 2026-11-13
captured: 2026-11-14
capture_type: source-summary
---

# Source Capture

This capture preserves provenance and a paraphrased summary of the retrieved
public article, not a full-text reproduction.

## Source Summary

Azure Managed Redis provides an application-level cache outside the database.
The article pairs it with Azure Database for PostgreSQL, Azure SQL Database,
and Azure Cosmos DB using a shared retail example. It recommends choosing
patterns per data flow rather than one pattern for an entire application.

Eight patterns are discussed: cache-aside, reference-data prefetching,
write-through, event-driven updates, write-behind, sorted-set ranking,
session/state offload, and multi-region caching.

The article's write-through flow commits to the database before updating the
cache. Event-driven updates refresh or invalidate cached values when another
system writes data. Write-behind is presented for counters where losing some
increments is acceptable.

## Sample Coverage

All three samples cover cache-aside, prefetching, write-through, and event-driven
updates. PostgreSQL uses a Redis Streams worker, SQL uses an Azure Functions
SQL trigger, and Cosmos DB uses its change feed with Azure Functions.
Only the SQL sample covers write-behind; only Cosmos DB covers ranking and
session/state offload. Together they demonstrate seven patterns, not eight:
all deploy in one region and do not demonstrate multi-region caching.

## Operational Guidance

- Choose frequently read, reusable data rather than write-heavy data with
  little reuse.
- Set TTLs from acceptable staleness and add jitter to spread expirations.
- Preserve database fallback when the cache is unavailable and account for
  retries on both services.
- Co-locate app, cache, and database.
- Use Entra authentication and managed identity; the samples use
  `DefaultAzureCredential` rather than embedded access keys.
- Monitor hit ratio, evictions, cache latency, and database resource usage.

## Boundaries

Retail traffic numbers are illustrative, not measured customer results.
Sub-millisecond hot reads and avoided scaling are source-stated benefits,
not universal end-to-end performance or cost guarantees.
The linked repository, architectures, and how-to documentation were not
independently reviewed. The article warns that sample Azure resources incur
charges and recommends separate deployment environment names and cleanup.

## Source-Linked References

- https://github.com/AzureManagedRedis/amr-caching-pattern-samples
- https://learn.microsoft.com/azure/architecture/databases/architecture/cache-aside-azure-managed-redis-postgresql
- https://learn.microsoft.com/azure/architecture/databases/architecture/write-through-caching-azure-sql-managed-redis
- https://learn.microsoft.com/azure/architecture/databases/architecture/event-driven-cache-updates-azure-managed-redis-cosmos-db
- https://learn.microsoft.com/azure/redis/how-to-active-geo-replication
- https://learn.microsoft.com/azure/redis/entra-for-authentication
