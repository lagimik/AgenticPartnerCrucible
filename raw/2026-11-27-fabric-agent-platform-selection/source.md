---
title: "Source capture - Fabric and Microsoft AI agent platform selection"
source_url: https://techcommunity.microsoft.com/blog/analyticsonazure/unlocking-data-value-with-fabric-and-microsoft-ai-agents-choose-deploy-optimise/4574895
article_id: "4574895"
captured: 2026-11-27
published: 2026-11-26
author: limaoncloud
publisher: Microsoft Tech Community - Analytics on Azure Blog
version: "1.0"
capture_type: Public article metadata and paraphrased source review
---

# Provenance

The user supplied the public article URL. The complete article was reviewed in two page segments on November 27, 2026. The page identifies the author as `limaoncloud` with a Microsoft badge, publication date November 26, and version 1.0. The November 27 signal report links the legacy URL form for the same article ID; it is not a separate source.

This capture preserves metadata and paraphrased knowledge, not the full article, images, tables, or deployment code.

# Source summary

The article is **Part 1: Choose** of a planned Choose, Deploy, Optimise series. It argues for governed enterprise data and a well-defined semantic layer before conversational analytics. Deployment walkthroughs and production optimization comparisons are promised for later posts, not delivered or tested here.

The author positions OneLake as a shared data foundation with domains/workspaces, open table formats, shortcuts, mirroring, and business meaning through semantic models and Fabric IQ. Shortcuts and replication are different access patterns; the article's broad one-copy and security claims should not be treated as guarantees of universal engine compatibility, freshness, or identical authorization.

Reports and agents are complementary. Certified reports remain appropriate for stable KPIs and regulated reporting. Natural-language answers need representative user questions and comparison with certified results; explicit measures, descriptions, and terminology matter more than persuasive answers.

The platform selection rule is the least-complex architecture that satisfies the use case: Microsoft 365 Copilot for the work experience, Copilot Studio for low-code business workflows and channels, and Foundry for engineered orchestration/runtime requirements. A layered design can keep the conversational front door, specialist analytics, action tools, and custom orchestration distinct.

Fabric data agents are described as GA, read-only analytical specialists over selected sources. The article's **October 2026** integration matrix lists Microsoft 365 publication as preview, Copilot Studio's tool-based path as GA, and Foundry Fabric IQ integration as preview. These are capability-specific claims, not platform-wide availability.

# Documentation review and qualifications

Seven public Learn pages were reviewed in full:

- [Data agent concepts](https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent): core feature is GA and read-only; paid F2+ or Fabric-enabled P1+ capacity; up to five sources; no raw/unstructured file access; current English-only support; same-region source/agent capacities; chat output capped at 25 rows and 25 columns. Semantic model Read permission is sufficient, and question/query examples are not currently supported for semantic model sources. The internal model cannot be changed. Purview protection capabilities have their own preview boundaries.
- [Microsoft 365 publication](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-365-copilot): same tenant/account, individual licenses, agent plus underlying-source permissions, Agent Store publication and possible output rephrasing. Instructions can reduce variation but do not guarantee unchanged output. The guide does not itself announce GA for the publication integration.
- [Copilot Studio tool path](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool): published data agents, compatible Copilot harness agent type, Fabric IQ Data MCP, same tenant/account, source permissions, and licensing prerequisites. **User** authentication uses the chatting user's permissions; **Maker** authentication uses the maker's permissions, and consumers do not need their own Fabric/source access. This qualifies the article's general "security follows the user" framing.
- [Foundry Fabric IQ path](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq): explicitly preview, published catalog items, delegated user authentication, separate build/connection roles, and multiple specialist data agents. The Foundry orchestration model does not change the Fabric data agent's internal model. Background mode requires a compatible model; the Java SDK does not support Fabric IQ.
- [Tenant settings](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-tenant-settings): required feature settings and region-dependent processing/storage switches. Detailed guidance requires cross-geo processing/storage for capacities outside the EU data boundary and US, rather than unconditionally for every geography. External consumers may process/store returned answers outside Fabric's compliance boundary under their own terms.
- [Retired Foundry integration](https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry): the legacy Microsoft Fabric tool became unsupported starting November 6, 2026; the documentation points to Fabric IQ. This date has already passed at capture time.
- [Fabric IQ in Copilot Chat](https://learn.microsoft.com/en-us/fabric/iq/connectors/microsoft-365-copilot-overview): Power BI data answering is GA, distinct from publishing a Fabric data agent. App/web access requires Microsoft 365 Copilot Premium and licensed Power BI content access. Report grounding can be combined with other Microsoft 365 context; answers reflect the last successful semantic-model refresh. Data agents/ontologies require an explicitly published Microsoft 365 agent. Unsupported content and regional/tenant settings remain important.

# Evidence boundaries

No customer sources were connected, agent published, identity configured, capacity purchased, tenant switch changed, or query/deployment executed. Other OneLake and platform-choice references in the article were not independently reviewed. The article's generalized commercial row, claims of universal security/interoperability, and future comparisons are not binding licensing advice, performance measurements, or production acceptance evidence.
