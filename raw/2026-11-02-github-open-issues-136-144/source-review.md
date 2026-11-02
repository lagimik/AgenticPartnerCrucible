# Public-source review - 2026-11-02

This is a capture-time summary of reviewed public evidence, not copied article
text, customer validation, or a record of changes to any live Microsoft service.
The [issue capture](issues.md) preserves the original submissions.

| Issue | Reviewed evidence | Supported summary and boundaries |
| --- | --- | --- |
| #136 | [Fabric Assessment Tool README](https://github.com/microsoft/fabric-toolbox/blob/main/tools/fabric-assessment-tool/README.md), read through GitHub and its public raw-content endpoint | Inventory and JSON export for Synapse and Databricks migration assessment, plus offline HTML visualization; permissions affect inventory completeness, and optional SQL statistics collection can create a view. No tool installation or customer assessment was performed. |
| #137 | [Finance announcement](https://www.microsoft.com/en-us/copilot/blog/2026/10/29/microsoft-copilot-for-finance-purpose-built-for-the-way-finance-teams-work/) | Accounting capabilities in Excel and Cowork are Frontier; Excel finance skills and Cowork Capital Markets and Finance plugins are GA; ERP and partner plugins are beginning rollout; third-party prerequisites and professional review still apply. This is not proof that the older Copilot for Finance preview product has the same lifecycle. |
| #138 | [Surge protection](https://learn.microsoft.com/en-us/fabric/enterprise/surge-protection?tabs=onelake-catalog), [capacity overage](https://learn.microsoft.com/en-us/fabric/enterprise/capacity-overage-overview), [overview events](https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-overview-events), [operation events](https://learn.microsoft.com/en-us/fabric/real-time-hub/create-streams-fabric-capacity-operation-events), and [operation event schema](https://learn.microsoft.com/en-us/fabric/real-time-hub/explore-fabric-capacity-operation-events) | Separate admission control, paid throttling relief, and telemetry; workspace-level surge protection is preview; overage thresholds are not hard spending caps; operation event consumers must be in the source region. The issue's GA/preview event labels were not explicitly restated by the retrieved setup pages. |
| #139 | [Direct Lake overview](https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-overview), including guardrails and limitations | Direct Lake uses VertiPaq and Delta tables with metadata framing; OneLake and SQL variants have different fallback and security behavior; capacity and table layout still matter. |
| #140 | [Foundry harness announcement](https://devblogs.microsoft.com/foundry/microsoft-copilot-harness-in-foundry/) | Managed Copilot harness is public preview; hosted-agent long-running resilience is separately GA; restart-safe progress and side effects remain application responsibilities; runtime billing is scheduled to begin December 1, 2026. |
| #141 | [Copilot Studio rename announcement](https://www.microsoft.com/en-us/copilot/blog/copilot-studio/the-github-copilot-harness-in-copilot-studio-is-now-the-microsoft-copilot-harness/) | GitHub Copilot harness is now named Microsoft Copilot harness in Copilot Studio; existing agents, capabilities, and billing are unchanged by the rename; internal evaluation figures are scenario-specific, not customer guarantees. |
| #142 | [Submitted announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/govern-your-microsoft-fabric-data-estate-from-one-place-with-the-onelake-catalog/5377369), read through [official Fabric RSS](https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs), item 5377369 | OneLake catalog Govern is GA; Govern Skills support Health, Protect, and Trust with audit/explain/recommend/remediate procedures and confirmation gates; Policies Center remains preview. |
| #143 | [Submitted announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/introducing-the-data-engineering-agent-for-fabric-project-osmos/5377944), read through the same official Fabric RSS, item 5377944; [overview](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview) and [quickstart](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started) | Project Osmos is preview, not production/SLA-backed; persistent Fabric tasks execute and validate Spark work; eligible nontrial capacity, Contributor access, tenant settings, permissions, and consumption review are required. |
| #144 | [Azure update 577260](https://azure.microsoft.com/en-us/updates?id=577260), verified with live `get_azure_update_by_id` on [Microsoft Release Communications MCP](https://www.microsoft.com/releasecommunications/mcp) | Published October 27, 2026; status Launched; Claude spend is attributed to the Foundry resource with deployment/resource tags and model/usage_type cost dimensions for allocation. |

## Access and uncertainty

- The two submitted Fabric article pages returned HTTP 403. Their full
  announcement content was available in Microsoft's public RSS, with matching
  stable article IDs; Project Osmos status and prerequisites were independently
  checked in public Microsoft Learn documentation.
- The surge-protection page contradicts itself on whether mission-critical
  workspaces are exempt from capacity-level surge protection: its state table
  says exempt, while its limitations say mission-critical status does not
  override capacity-level surge protection. Do not promise that exemption.
- The capacity-overage page calls the feature opt-in but also says it is enabled
  by default for newly created capacities. Inspect the actual capacity setting
  rather than assuming either default.
- The submitted operation-events link is labeled Public Preview in the issue;
  neither retrieved setup nor schema page explicitly confirms that lifecycle
  label. Retain the issue provenance and verify current release status before
  customer commitments.
- No inaccessible customer information, internal evaluation datasets, credentials,
  or third-party licensed data was retrieved or published.
