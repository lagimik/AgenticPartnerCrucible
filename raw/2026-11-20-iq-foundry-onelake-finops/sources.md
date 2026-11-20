---
title: November 20 Microsoft IQ, Foundry, Oracle, OneLake, Fabric Apps, and AI FinOps source capture
captured: 2026-11-20
source_type: public-announcements-and-documentation
---

# Source Capture

User-directed ingestion of six links from
[the November 20 signal report](../partner-crucible-signal-history/rss-partner-signal-2026-11-20.md).
This capture preserves provenance and paraphrased evidence, not full copyrighted
articles, video transcripts, or customer data. No deployment, billing change,
permission grant, training job, or website publication was performed.

## 1. Microsoft IQ

- Source: https://azure.microsoft.com/en-us/blog/introducing-the-new-microsoft-iq-putting-your-organizations-intelligence-to-work-in-every-agent/
- Publisher: Microsoft Azure Blog; displayed November 17; retrieved November 20, 2026.
- Access: article read successfully.

Microsoft announces an enterprise-context platform combining Work IQ
collaboration context, Fabric IQ business data and meaning, Foundry IQ
institutional knowledge, and Web IQ external context. Business plugins package
governed sources, skills, and tools for reuse across agents and supported
Microsoft and third-party experiences.

The article labels several Work IQ capabilities GA, including granular MCP
policies and real-time meeting context. The November 20 signal report instead
records roadmap items 570671 and 572674 as in development with January 2027 GA
estimates. Do not resolve this scope or timing difference by assumption.
Fabric data agents in Copilot are described as coming soon; several Fabric IQ
integrations and knowledge graphs are preview. Foundry IQ Serverless GA is
announced for December 2026, not established as available on capture day.
The article's Fabric apps preview wording differs from the dedicated GA article.

Supporting documentation reviewed:
https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/
describes user-scoped requests, policy evaluation, connector participation,
auditability, and usage-based API billing independent of Copilot user licensing.
It does not settle every roadmap discrepancy.

## 2. Microsoft Foundry Continuous Improvement

- Source: https://azure.microsoft.com/en-us/blog/continuous-improvement-comes-to-microsoft-foundry/
- Publisher: Microsoft Azure Blog; displayed November 17; retrieved November 20, 2026.
- Access: article read successfully.

The operating loop is Establish, Identify, Optimize, Validate and repeat.
Experts annotate traces and define representative evaluations; recurring
issues become candidate changes to instructions, skills, model selection, or
training. Teams compare quality, latency, and cost, and choose what reaches
production. Configuration improvement is separate from model-weight training.

Insights and visibility for LangGraph, LangChain, and CrewAI are described as
GA. Trace annotations, evaluation datasets, golden datasets, safety rubric
extensions, insight-to-optimizer handoff, skill and cost optimization, and
Programmed Training are preview. Hosted-agent concurrency is GA, faster startup
and the managed Copilot harness are preview, and AKS deployment is coming soon
in preview. Customer savings and benchmark examples are vendor-reported,
workload-specific evidence, not guarantees. Runtime control for agents outside
Foundry is framed as future work.

## 3. Microsoft and Oracle

- Source: https://azure.microsoft.com/en-us/blog/microsoft-and-oracle-bring-agentic-ai-into-flow-of-enterprise-work/
- Publisher: Microsoft Azure Blog, co-authored with Oracle; displayed November 17; retrieved November 20, 2026.
- Access: article read successfully.

The announcement connects Oracle business data with Work IQ context in Excel,
Teams, Copilot, and Foundry agent scenarios. Azure Workload Center for Oracle
and the Run Oracle operational experience use Workload Virtual Instances to
join infrastructure, database, and application evidence; Workload Center is
limited preview. An Oracle AI Database Excel plug-in is described as available
today. Managed MCP access supports approved SQL, PL/SQL, tools, and reports,
with Entra authentication, Oracle Deep Data Security, application roles, and
auditability governing access. MCP access can target OCI or Database@Azure.

Example workflows illustrate reviewed actions, not universal autonomous
write authorization. FedRAMP Class D certification is described as coming soon,
not a certification verified during ingestion. The cited latency comparison
is vendor-reported and placement-specific. Plug-in licensing, connector
prerequisites, certification, and workload performance were not independently
validated.

## 4. OneLake

- Requested source: https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/onelake-the-unified-foundation-for-data-context-governance-and-ai/5423035
- Publisher RSS: https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
- RSS item: https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/OneLake-The-unified-foundation-for-data-context-governance-and/ba-p/5423035
- RSS publication: 2026-11-17 18:20:51 GMT; retrieved November 20, 2026.
- Access: requested article HTTP 403; complete publisher RSS description reviewed.

The publisher positions OneLake catalog as the lake-first governance foundation
for native and connected data, explicitly not a feature-for-feature replacement
for Purview Data Governance. Purview security and compliance continue.
Atlan is announced as a complementary partner for governance beyond OneLake and
transition tooling; that tooling was not independently tested.

Catalog federation and Iceberg read/write credential vending are labeled GA.
IQ Sharing with ontologies, OneLake knowledge-source/security integration with
Foundry IQ, semantic views, and Salesforce Data 360 shortcuts are preview.
Additional data quality, glossary, lineage, and policy work is forward-looking.
The summary labels Databricks native storage GA but does not independently
establish that the previously reviewed Databricks-side preview restrictions
have ended.

Reviewed implementation evidence:
- https://learn.microsoft.com/en-us/fabric/onelake/table-apis/iceberg-table-apis-overview
  distinguishes native Iceberg writes from read-only virtual Iceberg metadata
  over Delta; commits through shortcuts are unsupported.
- https://learn.microsoft.com/en-us/fabric/onelake/table-apis/table-apis-overview
  separates metadata operations from preview secured row reads and requires
  operation-specific permissions.

## 5. Fabric Apps

- Requested source: https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/build-governed-data-apps-with-microsoft-fabric-apps-generally-available/5423011
- Publisher RSS: https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
- RSS item: https://community.fabric.microsoft.com/t5/Fabric-Updates-Blog/Build-governed-data-apps-with-Microsoft-Fabric-Apps-Generally/ba-p/5423011
- RSS publication: 2026-11-17 18:30:00 GMT; retrieved November 20, 2026.
- Access: requested article HTTP 403; complete publisher RSS description reviewed.

Rayfin SDK/CLI and Fabric Apps are announced GA. TypeScript defines data,
permissions, APIs, functions, and frontend delivery; deployed apps become
governed Fabric items. Fabric HorizonDB is separately preview. The summary
describes administrator app inventory/blocking, CSP, secure embedding, and
item identity, with build entry points through Copilot and Power BI.

Supporting Learn pages reviewed:
- https://learn.microsoft.com/en-us/fabric/apps/overview
- https://learn.microsoft.com/en-us/fabric/apps/data-permissions
- https://learn.microsoft.com/en-us/fabric/apps/connectors
- https://learn.microsoft.com/en-us/fabric/apps/pricing

Documentation distinguishes app access, entity row/field policies, and source
authorization. SQL connectors default to application authentication in the
documented CLI release, with the app identity currently the item owner;
delegated mode uses caller permissions, and semantic models are delegated only.
This qualifies the announcement's independent item-identity wording.
Local schema discovery does not prove runtime access. Lakehouse SQL access is
read-only; warehouse/SQL writes require selected operations and permissions.
Capacity and Power BI Pro licensing paths differ. Local file storage still uses
Fabric storage, so local development is not fully offline. Anonymous static
hosting and anonymous data roles exist; sign-in is not a blanket protection for
every asset. Application exposure, secrets, and compliance remain customer
responsibilities.

## 6. Copilot and Agent 365 AI Cost and Value

- Source: https://techcommunity.microsoft.com/blog/microsoftmechanicsblog/manage-ai-cost--roi-with-copilot-and-agent-365/4574647
- Publisher: Microsoft Mechanics; published November 19, 2026; retrieved November 20.
- Access: article read successfully; linked video not independently watched.

The article demonstrates individual task-level credit visibility, AI spending
breakdowns, use-case value estimates, forecasts, and delegated budget controls.
Usage-based billing uses an Azure subscription with PAYG or prepaid billing.
Policies can cover identities or shared resources, cumulative and per-user
limits, alerts, model controls, and Delegator/Writer/Reader roles.
Reaching a demonstrated hard limit interrupts covered services.

The article states a current US-dollar conversion of one Copilot Credit to one
cent; this is dated publisher guidance, not a binding customer quote. Its
AI-value metric estimates comparable human work using labor references, not
realized cash savings. Example spend shares are demonstration data.
Roadmap item 577548 in the signal report still lists Business Analytics in
development with November preview and December 2026 GA estimates.

Reviewed supporting guidance:
https://learn.microsoft.com/en-us/plugins/cost-considerations
states that spending policies limit consumption but do not reserve credits;
Work IQ, Cowork, and Studio can share a prepaid pool, allocations reduce shared
availability, and no single control spans both administration planes.
Studio per-agent enforcement is not instantaneous and does not stop called
agent flows. Copilot user licenses do not replenish API credit balances.

## Interpretation and Decisions

The six sources support bounded partner motions for enterprise-context
curation, evaluated agent operations, Oracle integration, lake-first governance,
governed data apps, and AI FinOps. Capability-specific licensing, permissions,
status, and customer outcome evidence must be checked before proposals.
No source disagreement was silently reconciled and no customer outcome was
inferred from vendor demonstrations.
