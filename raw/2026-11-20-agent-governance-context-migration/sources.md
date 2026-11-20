# November 20 Agent Governance, Context, and Migration Sources

Captured: 2026-11-20. User-selected sources from the November 20 signal report,
including the leading Azure AI Gateway link. This capture preserves URLs,
publisher metadata, and paraphrased evidence, not full copyrighted articles.
Interpretations and proposed delivery actions are maintained separately in wiki
resources. No tenant configuration, enrollment, migration, or deployment occurred.

## Acquisition and Provenance

The five Azure Updates pages returned generic application shells, not usable
item content. Their evidence was read through the public Microsoft Release
Communications MCP endpoint, `https://www.microsoft.com/releasecommunications/mcp`,
using live-discovered `get_azure_update_by_id` and the exact IDs below.
Initialization negotiated protocol `2025-03-26`; JSON-RPC/tool errors were checked.
Release rings and release months are distinct from post creation/modification.

| Azure ID | Structured title | Status / availability | Created / modified UTC |
| --- | --- | --- | --- |
| 580080 | Generally Available: Azure AI Gateway | Launched; GA November 2026 | 2026-11-17T20:00:32.9099044Z / same |
| 563661 | Generally Available: Semantic chunking and AI-generated image descriptions with Azure Content Understanding in Azure AI Search | Launched; preview June 2026, GA November 2026 | 2026-06-04T19:00:34.7881254Z / 2026-11-17T21:17:15.9306275Z |
| 579231 | Public Preview: AI Assisted Oracle-to-PostgreSQL Application Code Migration | In preview; November 2026 | 2026-11-17T20:00:32.9099044Z / same |
| 580055 | Generally Available: Microsoft Agent 365 integration with Azure API Management and Azure AI Gateway | Launched; GA November 2026 | 2026-11-17T20:00:32.9099044Z / same |
| 580684 | Public Preview: Agent Grid helping secure AI agent communications | In preview; November 2026 | 2026-11-17T20:47:31.8431798Z / same |

The Fabric IQ HTML article returned HTTP 403. Its complete publisher RSS
description was read from
https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
by exact article ID 5423049; publication metadata was November 18, 2026,
17:59:46 GMT. Canonical identity and supporting Learn URLs are preserved below.
The other four requested articles/documentation pages were directly accessible.

## 1. Azure AI Gateway

Requested source: https://azure.microsoft.com/en-us/updates?id=580080

The update announces a fully managed service for connecting users, applications,
and agents to models and MCP tools across providers. It describes centralized
authentication/authorization, stable model aliases, intelligent model selection,
priority/weighted routing, session affinity, failover, usage attribution,
estimated costs, quotas, rate limits, budgets, and integration with Foundry,
Agent 365, Entra ID, and Application Insights. The dated offer includes 10,000
free gateway requests per subscription per month; this is not free model usage.

Supporting migration guidance:
https://learn.microsoft.com/en-us/azure/ai-gateway/ai-gateway-resource
(updated November 18, 2026). It changes only the former `AIGateway` SKU
representation, from `Microsoft.ApiManagement/service` to
`Microsoft.ApiManagement/aigateways`, with ARM API `2026-11-01`. Other APIM SKUs
are not affected. Old AIGateway resources are documented to cease working and be
removed January 15, 2027; migration must complete before that date.

The new resource ID, hostname, key header, identities, role assignments, and
contracts require reviewed cutover; resource-scoped roles do not transfer.
Read the runtime hostname from `properties.frontend.defaultHostname`; key
authentication uses `Authorization: Bearer`. Keep rollback until traffic is
verified. Private endpoints are approval-gated public preview. The migration
guide says the content safety policy is unsupported, while the update advertises
content safety guardrails. Do not infer identical policy coverage.

Earlier APIM guidance at
https://learn.microsoft.com/en-us/azure/api-management/genai-gateway-capabilities
(updated June 25, 2026) calls AI gateway an APIM extension, not a separate
offering. That narrower historical description must not negate the new service
announcement or be treated as a parity guarantee for the new resource.

## 2. Fabric IQ Trusted Context

Requested source:
https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/bringing-trusted-fabric-iq-context-to-wherever-people-and-agents-work/5423049

The article describes OneLake unified data, Power BI semantic models, and
ontologies as three layers of reusable business context. Data and operations
agents put that context to work. Availability is per capability:

- Power BI semantic models in Copilot and Fabric IQ MCP: GA.
- Fabric data agents in Copilot: GA coming soon, not currently GA by this article.
- ChatGPT/Claude plugins: preview coming soon. Excel: Insiders Beta.
- Fabric Apps: GA; Copilot app creation and ontology access in GitHub Copilot:
  preview. Embedded data-agent experiences are coming soon.
- Semantic views, ontology enhancements, IQ sharing, and data-agent
  setup/monitoring/governance enhancements: preview or preview coming soon.
- Faster data-agent answers, larger result sets, and timezone-aware questions:
  described as GA; do not transfer that status to every agent enhancement.

The Foundry IQ section's heading says GA, but its detailed text explicitly puts
Power BI semantic models, OneLake shortcuts, and mirrored items as knowledge
sources in preview. Preserve the item-specific distinction.

Supporting overview: https://learn.microsoft.com/en-us/fabric/iq/overview
(updated November 20, 2026). The IQ workload and ontology remain preview.
Semantic views complement semantic models; creating ontologies from models
generated by semantic views is unsupported in this preview. The ontology
agent proposes changes for review.

Copilot documentation:
https://learn.microsoft.com/en-us/fabric/iq/connectors/microsoft-365-copilot-overview
(updated September 23, 2026). Copilot Premium and licensed Power BI access are
required; existing permissions including RLS/OLS, labels, and DLP apply. Tenant
settings govern exposure and metadata sharing; US/EU processing requirements
can require cross-geography consent. A report attachment does not restrict an
answer exclusively to that report.

## 3. Content Understanding in Search

Requested source: https://azure.microsoft.com/en-us/updates?id=563661

The GA skill creates semantically coherent Markdown chunks, location metadata,
and searchable descriptions of images for Foundry IQ and Azure AI Search.
Supporting skill reference:
https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-content-understanding
(updated November 17, 2026). The base skill is GA in Search API `2026-04-01`;
semantic chunking and image descriptions are GA in `2026-10-01`, independently
of the downstream Content Understanding API `2025-11-01`.

Semantic chunking is not semantic ranking. Image extraction, descriptions,
embeddings, and client-side image serving are separate. Descriptions require
paired supported `modelName` and `modelDeployment`; embeddings need their own
skill. Search's analysis polling window is eight minutes, not a file-size
threshold or end-to-end SLA. Timeout produces an enrichment error and no
analysis output; inspect other indexing behavior and failure thresholds.
Stopping polling does not prove downstream cancellation. Preserve citations
and permissions when splitting content. Extraction and optional model usage
are billed separately; retries may incur fresh charges.

## 4. Oracle-to-PostgreSQL Application Code Migration

Requested source: https://azure.microsoft.com/en-us/updates?id=579231

The public-preview plugin supplies AI-assisted skills consumed through GitHub
Copilot CLI or Visual Studio Code, including existing Modernize CLI workflows.
It identifies Oracle-specific application dependencies and proposes code changes
for Azure Database for PostgreSQL compatibility. Developers review and validate
before accepting. The item does not establish automatic database/schema/data
migration, complete language coverage, correctness, or production readiness.
Separate this migration motion from Oracle AI Database/Work IQ integration.

## 5. Agent 365 and APIM Runtime Governance

Requested source: https://azure.microsoft.com/en-us/updates?id=580055

The GA integration combines Agent 365 inventory/governance with runtime
enforcement in APIM and Azure AI Gateway. It discovers supported registered
gateways and MCP servers, supports server- and tool-level blocking, records
agent-to-tool interactions, and uses supported Defender/Purview capabilities
for threats and sensitive-information risks in requests/responses. Supported
registration, routing, policy scope, and backend permissions matter; inventory
is not universal discovery and GA is not a blanket protection claim.

## 6. Agent Grid

Requested source: https://azure.microsoft.com/en-us/updates?id=580684

The public-preview update describes identity-based network controls outside
the agent trust boundary: mTLS, TLS inspection, FQDN/URL filtering, granular MCP
tool controls, and Content Safety Prompt Shields. It names onboarded ACI groups,
AKS Kata sandboxes, and native AKS workloads, without customer sidecars.

Supporting overview: https://learn.microsoft.com/en-us/azure/agent-grid/overview
(updated November 18, 2026). This explicitly calls access **limited preview**
and requires an access request. Regions: Central US, West US 2, Sweden Central,
Australia East, Indonesia Central. Attaching compute alone does not change
traffic; only enrolled members are governed. Same subscription/region is
required. ACI sandbox groups need public IPs; VNet-integrated groups and private
AKS clusters are unsupported. Foundry hosted agents, Container Apps, and Copilot
Studio are unsupported. TCP/IPv4 only; identities are not integrated with
Entra Agent ID. Prompt Shields requires customer-owned Content Safety. These
access/scope limits qualify, rather than silently replace, the update's label.

## 7. Sovereign Control Panel

Requested source:
https://learn.microsoft.com/en-ca/azure/azure-sovereign-clouds/public/sovereign-control-panel
Canonical:
https://learn.microsoft.com/en-us/azure/azure-sovereign-clouds/public/sovereign-control-panel
(updated November 18, 2026; ms.date November 17).

SCP public preview assesses selected subscriptions/management groups for
residency, encryption at rest/in transit, network exposure, and continuity
compatibility. The global service stores view data and metadata in Sweden;
preview assessment is geared to European regions, but the tenant need not be
European. Selected policies are non-enforcing. Eligible primary-resource
residency can be remediated; linked copies are assessment-only. Coverage gaps,
RBAC, provider registration, and report status limit findings. Reports are not
real-time; existing scope/controls cannot be edited, so create replacement views.
Continuity compatibility is not recovery configuration or workload continuity
proof; RTO/RPO and operating duration are unavailable.

## 8. Perception Third-Party Security Data

Requested source:
https://techcommunity.microsoft.com/blog/perception-blog/more-signals-stronger-defense-microsoft-perception-expands-to-third-party-data/4573037
(published/updated November 19, 2026, version 2).

Defender connectors supply third-party signals. Triage Agent GA is limited to
specific Okta/Salesforce alerts generated by Microsoft security products.
Investigation has specialized AWS/Okta expertise; Detection Authoring has
specialized AWS/Okta/Salesforce expertise and tunes/validates proposed detections
for analyst review. Broader reasoning depends on data actually reaching Defender.
Do not assign Triage GA to all agents/sources.

The reconstructed real incident occurred without Perception deployed.
Demonstrations use a research tenant and simulated/replayed telemetry, not
observed incident prevention. The cited 20-40 minute investigation duration is
publisher guidance, not an SLA. Additional tailored source/alert support is
planned.

## 9. Azure Catalyst Webapp Assessment

Requested source:
https://techcommunity.microsoft.com/blog/azuremigrationblog/azure-catalyst-expands-webapp-target-coverage/4574689
(published/updated November 19, 2026, version 1).

New targets are Container Apps and Managed Instance on App Service, alongside
App Service Code/Containers and AKS. Discover apps, servers, databases, and
dependencies; select region, sizing, and pricing; compare target-specific
readiness, remediation warnings, recommended plan, and monthly cost estimates.
Optional Copilot Modernization code assessment adds proposed changes/effort.
CAF/WAF design, reviewed waves, approved changes, builds, and deployment remain
separate work. Assessment is not migration and cost/effort estimates are not
quotes or guarantees. Managed Instance targets Windows/.NET Framework OS
dependencies; Container Apps scale-to-zero is configuration-specific.

Supporting workflow:
https://learn.microsoft.com/en-us/azure/migrate/create-application-assessment?view=migrate
(updated September 24, 2026). Discover inventory and resolve flagged collection
issues before assessment; scope relationships and preferences explicitly.

## 10. Dynamics 365 Activate

Requested source:
https://www.microsoft.com/en-us/dynamics-365/blog/it-professional/2026/11/19/dynamics-365-activate-erp-crm-migration/
(published November 19, 2026).

ERP implementation/migration, including SAP ECC discovery, is **private
preview**; Salesforce CRM migration is **GA**. Guided discovery, requirements,
configuration, and migration retain team review/sign-off. ERP inventories
customizations/dependencies/roles and maps processes to the Business Process
Catalog; approved configuration is versioned and auditable. Salesforce
discovery inventories objects/fields/flows/Apex/integrations, maps to Dataverse
with reviewed roles/business units and schema approval, then trial loads,
incremental deltas, resumable record/file/attachment transfers, monitoring, and
record-count reconciliation. Counts are not proof of process/financial/security
correctness. Publisher scale/history and partner quotes are not guarantees.

Supporting overview:
https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/dynamics-365-activate-overview
and setup:
https://learn.microsoft.com/en-us/dynamics365/dynamics-365-activate/migrate-salesforce-to-dynamics-365-access-setup
(both updated November 18, 2026). Public setup covers Salesforce to Sales or
Customer Service, English only, US workspaces, Entra work accounts, workspace
membership plus project sharing. Self-service workspace signup needs no
Microsoft approval, but does not establish access to ERP private preview.
