---
title: Fabric Data Agents - Platform Selection and Governed Delivery
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [microsoft-fabric, data-agents, onelake, copilot-studio, microsoft-foundry, governance]
sources:
  - raw/2026-11-27-fabric-agent-platform-selection/source.md
  - https://techcommunity.microsoft.com/blog/analyticsonazure/unlocking-data-value-with-fabric-and-microsoft-ai-agents-choose-deploy-optimise/4574895
  - https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-365-copilot
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-tenant-settings
  - https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry
  - https://learn.microsoft.com/en-us/fabric/iq/connectors/microsoft-365-copilot-overview
status: active
---

# Fabric Data Agents - Platform Selection and Governed Delivery

## Source summary

The [November 26, 2026 Analytics on Azure article](https://techcommunity.microsoft.com/blog/analyticsonazure/unlocking-data-value-with-fabric-and-microsoft-ai-agents-choose-deploy-optimise/4574895) is **Part 1: Choose**. It connects governed OneLake data and business semantics to Microsoft 365 Copilot, Copilot Studio, and Microsoft Foundry. Deploy and Optimise are planned follow-ups, not completed walkthroughs or validated customer outcomes.

Start with the lightest architecture meeting user experience, data, actions, and governance requirements. Preserve certified reports for stable or regulated reporting; test conversational answers against representative questions and certified measures rather than treat fluent output as evidence of accuracy.

## Platform fit

| Platform | Article's selection rule | Analytics connection |
| --- | --- | --- |
| Microsoft 365 Copilot | Use an existing work experience or declarative agent when it meets the need. | GA Power BI data answering in Copilot Chat is distinct from publishing a specialist Fabric data agent to Agent Store. |
| Copilot Studio | Favor low-code business workflows, approvals, integrations, and channel reach. | The Fabric IQ Data MCP tool can call published data agents; compatible agent type and connection authentication matter. |
| Microsoft Foundry | Choose engineered model, runtime, networking, and orchestration control when required. | Fabric IQ (OneLake Catalog) exposes published data agents as tools using delegated user authentication. |

The article's integration matrix is dated **October 2026**: Microsoft 365 data-agent publication preview, Studio tool integration GA, and Foundry Fabric IQ preview. Reviewed Foundry guidance still labels that path preview; the Microsoft 365 publication guide does not independently establish a newer GA announcement. Do not inherit core data-agent GA for every source, protection feature, or integration.

## Identity and action boundaries

The [core data agent](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent) generates read-only analytical queries. An orchestrator can use its answer in a subsequent workflow, but that does not authorize writes, emails, transactions, or other tools.

**Security does not always follow the chatting user.** The [Studio tool guide](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool) supports two connection modes:

- **User:** each consumer needs access to the data agent and underlying sources.
- **Maker:** requests use the maker's permissions; consumers do not need their own Fabric/source access and see data through that identity.

This qualifies the article's general security framing. Review connection identity and audience explicitly before publication; read-only access can still expose data.

The [Foundry path](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq) uses delegated user authentication. Building/testing requires Foundry User; creating the Fabric IQ connection requires Foundry Project Manager. Published-item discovery and agent access are distinct from access to underlying data.

## Delivery checks

| Check | Current documented boundary |
| --- | --- |
| Capacity and licensing | Paid F2+ or Fabric-enabled Power BI Premium P1+ capacity; same tenant/account for the reviewed consuming paths. Capacity does not confer consuming-platform licenses. Verify each path's current builder/user licensing. |
| Region and data handling | Source and data-agent capacities must share a region. Review required tenant settings; detailed cross-geo guidance applies processing/storage switches to capacities outside EU/US boundaries. External answers can leave Fabric's compliance boundary under the consumer's terms. |
| Source scope | Up to five sources. Lakehouse access is through selected tables, not raw files; unstructured documents are unsupported. Validate specific source/protection feature status rather than infer universal support. |
| Semantic preparation | Curate measures, descriptions, and terminology. Semantic-model Read permission suffices for agent queries; sample question/query pairs are not currently supported for semantic-model sources. |
| Answer completeness | Current data-agent chat output is capped at 25 rows and 25 columns; it is not a complete-dataset export. Follow-ups can inherit truncated context. Current core data-agent language support is English only. |
| Output fidelity and freshness | Copilot orchestration can rephrase specialist output; publishing instructions cannot guarantee byte-for-byte preservation. GA Power BI answers can combine other Microsoft 365 context and reflect the semantic model's last successful refresh. |
| Foundry connector lifecycle | The legacy Microsoft Fabric tool has been unsupported since November 6, 2026. Use the documented Fabric IQ replacement, not the retired workflow. |
| Model/runtime assumptions | Changing the Foundry orchestration model does not change the internal Fabric data-agent model. Long questions may need supported background mode; the Fabric IQ code path does not support the Java SDK. |

These checks are supported by [core concepts](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent), [tenant settings](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-tenant-settings), [Microsoft 365 publication](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-365-copilot), [Power BI answers](https://learn.microsoft.com/en-us/fabric/iq/connectors/microsoft-365-copilot-overview), and the [retirement notice](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry).

## Partner application and limitations

**Interpretation:** Offer a bounded platform-choice and analytics-readiness workshop. Select one business question set, identify the certified semantic authority, agree caller identity and audience, review data movement, test authorized/unauthorized personas, and compare final answers across the intended channel. Separately govern every downstream action and billable deployment.

OneLake's shared-data model does not guarantee identical engine permissions, universal interoperability, instant freshness, or unchanged answers across channels. Generated analytics and source examples are not regulatory-report replacements or assurance guarantees. No customer data, agent publication, query, deployment, licensing transaction, or tenant setting was accessed or changed.

## Related pages

- [Fabric Data Agent](../10-Notes/entities/fabric-data-agent.md)
- [Read-Only Analytics and Action Separation](../10-Notes/concepts/read-only-analytics-and-action-separation.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Microsoft Foundry](../10-Notes/entities/microsoft-foundry.md)
- [Foundry Agent Selection](microsoft-foundry-agent-selection.md)
- [Microsoft IQ Solution Accelerator](microsoft-iq-solution-accelerator.md)
- [Shared Storage with Catalog-Mediated Access](../10-Notes/concepts/shared-storage-catalog-mediated-access.md)
- [Fabric Practice Building](../100-Crucible/DataAISolutionArea-Fabric.md)
