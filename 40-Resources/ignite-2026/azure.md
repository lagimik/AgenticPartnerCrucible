---
title: Ignite 2026 - Azure
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [ignite-2026, azure, infrastructure, databases, microsoft-fabric]
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - raw/2026-11-27-ignite-2026-book-of-news/source.md
status: active
---

# Ignite 2026 - Azure

Paraphrased announcement inventory under the source's Azure categories.
Release labels below describe what the [Book of News](https://news.microsoft.com/events/ignite/2026/book-of-news/)
announces, not independent deployment verification. Product links are source
follow-up pointers; regional availability, access, billing and support need
workload-specific checks.

## Brand, infra & silicon

### Chaos Studio Workspaces and AKS extension

Both are announced GA. Workspaces organize repeatable failure scenarios; the
AKS extension supports controlled pod disruptions with narrower permissions.
**Partner interpretation:** validate actual recovery against business objectives
rather than treating an architecture diagram as resilience evidence.
[Source follow-up](https://aka.ms/chaosstudio/workspaces-ga).

### Confidential computing expansion

VR72 multi-GPU confidential computing, confidential enclaves/Kata CoCo containers,
and confidential clean rooms are preview. They address different trusted
execution and collaboration boundaries, not a general compliance guarantee.
[Source follow-up](https://aka.ms/acc-ignite2026).

### Cobalt 200 virtual machines

Cobalt 200 is announced GA. Expansion to 24 regions by year-end is a plan,
not a statement that all 24 are available now. Consistent-speed/boost options
and Mpsv4/Lpsv5 variants support different CPU, memory and storage profiles.
The reported improvement over Cobalt 100 is workload-dependent.
[Source follow-up](https://aka.ms/Cobalt200VMs-GA).

## Core

### Agentic Azure operations

Azure Monitor natural-language capabilities and health models are GA.
Copilot spaces/custom skills, Workload Center and the described SRE Agent
extensions are preview. Customer-managed keys, agent identity integration,
cross-agent work, Teams and multicloud investigations require capability-level
checks. [Source follow-up](https://aka.ms/ignite2026/agenticops).

### Production AI infrastructure and Foundry-to-AKS

Foundry deployment to customer AKS, Agent Grid, Agent Sandbox extension and
Flex nodes are preview; Cobalt 200 is the explicit GA exception.
**Partner interpretation:** separate model serving, generated-code isolation,
network policy and operational ownership.
[Source follow-up](https://aka.ms/ai-infra-ignite26).

### Azure Catalyst modernization

Catalyst and the renamed Catalyst agent are announced GA. Deeper discovery,
execution, integrated application/database modernization and BizTalk migration
additions include previews. GA of the umbrella experience does not make every
execution path GA. [Source follow-up](https://aka.ms/modernization-ignite26).

### Windows Server 2028

Server security, performance and management additions are Insider preview;
hybrid intelligence has separate limited early access and hardware requirements.
The item names local inference, execution containers and Agent 365 integration.
Do not equate preview platform support with supported production combinations.
[Source follow-up](https://aka.ms/WindowsServer2028Announcement).

## Data

### Cosmos DB development, retrieval and backup

Shell, Rust SDK, semantic reranking, FuzzyBM25 score projection and Azure Backup
are announced GA. AI-assisted VS Code data modeling is preview.
The source calls this seven updates but lists six named capabilities; no
additional feature is inferred. [Source follow-up](https://aka.ms/ignite26/cosmosdb).

### DocumentDB development and hybrid deployment

VS Code tooling and near-instant M10-M30 provisioning are GA. Arc deployment,
Azure Local deployment and database/collection-level custom RBAC are preview.
MongoDB compatibility does not establish compatibility for every application
or topology. [Source follow-up](https://aka.ms/ignite26/documentdb).

### Azure HorizonDB

The Azure PostgreSQL-compatible service is announced GA. Built-in model
management, AI Functions/Pipelines and Fabric mirroring are preview; the
PostgreSQL VS Code extension is GA. Keep service GA separate from AI and
analytics integration previews. [Source follow-up](https://aka.ms/ignite26/horizondb).

### Managed Redis 8 and agent kit

Both additions are preview. Redis 8 combines multiple data/search types;
the agent kit recommends connection and configuration improvements for human
evaluation. It is not proof that an application's caching is correct.
[Source follow-up](https://aka.ms/ignite26/AMR).

### Azure SQL resiliency, migration and local development

Managed Instance zone redundancy, applicable independent memory sizing and
multi-database availability-group link support are GA. The Azure SQL Database
local container is preview. Free local development does not imply free cloud
database or model usage. [Source follow-up](https://aka.ms/ignite26/mssql).

### Database Hub and SQL/PostgreSQL agents

Database Hub in Fabric is GA; database agents are preview. Estate-wide
discovery/monitoring and permissioned, approved remediation are distinct
activities. Preview agents do not replace DBA judgment or authorization.
[Source follow-up](https://aka.ms/ignite26/databases).

### Fabric HorizonDB

Fabric's serverless PostgreSQL offering is preview, distinct from GA Azure
HorizonDB. The item describes app backends, translytical queries, mirroring and
reverse ETL. Automatic provisioning, pausing and resuming are source-described
behaviors, not measured latency or availability commitments.
[Source follow-up](https://aka.ms/AAncdv4).

### PostgreSQL migration and protection

Oracle/PostgreSQL migration additions, Burstable v2 and expanded Azure Backup
are preview. Cobalt 200 compute, AMD v6 confidential compute, restore
immutability and same-zone-to-zone-redundant conversion are announced GA.
Verify exact service, region and migration-mode support.
[Source follow-up](https://aka.ms/Ignite26/Postgres_on_Azure).

### Power BI data app creation

Power BI Pro app creation in Desktop is preview. The source describes apps
grounded in semantic models with transactional/write-back behavior and Fabric
database access. A governed analytical model does not independently authorize
every write action.
[Source follow-up](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/microsoft-fabric-is-fueling-frontier-transformation/5422989).

### Rayfin and Fabric apps

Rayfin/Fabric apps are announced GA, with backend, authentication, app governance
and Copilot/Power BI integration. Preserve the separate previews for Fabric
HorizonDB and Pro/Desktop creation instead of inheriting blanket GA.
[Source follow-up](https://aka.ms/FabricApps-Ignite26).

## Connected Knowledge

- [Azure](../../10-Notes/entities/azure.md)
- [Microsoft Fabric](../../10-Notes/entities/microsoft-fabric.md)
- [Azure Local](../../10-Notes/entities/azure-local.md)
- [CAF AI architecture](../caf-ai-architecture-governance.md)
- [SRE Agent enterprise adoption](../azure-sre-agent-enterprise-adoption.md)
- [Continuous resilience validation](../continuous-azure-resilience-validation.md)
- [Caching correctness](../../10-Notes/concepts/caching-correctness-and-failure-budgets.md)
- [Ignite map](../moc-ignite-2026-book-of-news.md)
