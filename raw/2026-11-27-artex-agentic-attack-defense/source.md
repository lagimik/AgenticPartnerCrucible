---
title: "Source capture - ARTEX agentic attack defense"
source_url: https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/
captured: 2026-11-27
published: 2026-11-25
author: Microsoft Threat Intelligence
publisher: Microsoft Security Blog
capture_type: Public article metadata and paraphrased defensive summary
---

# Provenance

The user supplied the public Microsoft Security Blog URL. The complete article was reviewed in four successive page segments on November 27, 2026. The page identifies Microsoft Threat Intelligence as author, November 25 as publication date, and the article as research. This capture preserves metadata and a paraphrased defensive summary, not the full article, diagrams, offensive procedures, or hunting-query code.

# Source summary

Microsoft reports that ARTEX, an AI-powered penetration-testing framework, has been abused by state-sponsored and financially motivated actors to accelerate existing reconnaissance, credential attacks, web exploitation, and post-compromise workflows. The report names Storm-0940, Storm-3358, Onyx Sleet, Pearl Sleet, Crystal Typhoon, and Salt Typhoon as observed users. These are Microsoft-attributed observations, not independently verified investigations by the vault.

At a high level, ARTEX coordinates goal setting, planning, workers, and reporting around a shared knowledge graph. Agents can use different models and providers, so provider-specific model safety controls and telemetry do not encompass all deployments. The report emphasizes existing attack techniques executed with adaptive retries and short transitions between attack stages, rather than new techniques.

For defenders, the more durable signal is a correlated sequence: bursts of diverse web requests or failed sign-ins, suspicious web-server child processes or script writes, rapid access to sensitive files, and application credential/role changes followed by cloud API or data access. The reported default user-agent prefixes `artex-enrich/*` and `norma/*` can support investigation but are mutable. Ordinary automation and other offensive frameworks can produce similar evidence; common utilities, alerts, or a user-agent match alone do not prove ARTEX attribution.

The mitigation guidance emphasizes exposure inventory and remediation, tuned WAF prevention and rate limits, API authentication/authorization, endpoint coverage on internet-facing Windows and Linux servers, constrained egress, strong user authentication, service-principal protection, leaked-secret invalidation, least privilege, application consent/credential governance, and supported automated containment.

The source makes log coverage an investigation prerequisite: include Entra audit and service-principal sign-ins, Graph activity, web requests, and WAF logs. Empty hunts are not proof of no compromise when relevant data was never collected. Endpoint hunting examples require Defender for Endpoint coverage; the service-principal example uses `EntraIdSpnSignInEvents` and requires Entra ID P2. Sample query thresholds and automation exclusions need environment-specific tuning.

Some Defender for Cloud Apps policies are transitioning from alerts to behaviors. The report identifies `MultipleFailedLoginAttempts` in `BehaviorInfo`/`BehaviorEntities`; applicable policies may be disabled by default and may not emit alerts. Current behavior collection and custom-detection configuration must be checked separately.

The article positions Perception Recon Agent as read-only attack-path analysis, not active exploitation validation. Authorized testing requires an agreed scope, resource-owner consent, traffic constraints, and compliance with Microsoft testing rules; third-party leaked credentials are not authorized test inputs.

# Supporting documentation and qualification

- [Conditional Access for workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/workload-identity), reviewed in full: covers directly assigned, tenant-owned single-tenant service principals; managed identities and Microsoft/third-party multitenant SaaS applications are excluded; group assignment does not enforce a policy for a member service principal; Workload Identities Premium is required to create or modify these policies; workload identities cannot perform MFA. This narrows the blog's broad recommendation to apply Conditional Access to every workload identity.
- [Automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption), reviewed in full: incident-level correlation and supported response actions, with security teams retaining investigation, recovery, and exclusion control; no guarantee of universal containment coverage.
- [Configure attack disruption](https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption), prerequisite sections reviewed: coverage depends on deployed products, onboarding, permissions, sensors, device discovery, action accounts, and connectors; automatic device isolation is described as preview and scoped to onboarded, managed end-user workstations, not every internet-facing server.

# Evidence boundaries

- No customer logs were queried, threat attributed, hunting query executed, policy deployed, credential handled, or response action taken.
- Source incident timings, traffic counts, and deception results are Microsoft-reported examples, not general thresholds or performance guarantees.
- Sample queries and alert names are investigation starting points, not validated tenant detections or proof of compromise.
- Other linked incident reports, product prerequisites, and third-party references were not exhaustively reviewed; verify current licensing, schema, scope, and platform support before implementation.
