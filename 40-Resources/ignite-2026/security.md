---
title: Ignite 2026 - Security
type: resource
created: 2026-11-27
updated: 2026-11-27
tags: [ignite-2026, security, agent-365, defender, entra, intune, purview, perception]
sources:
  - https://news.microsoft.com/events/ignite/2026/book-of-news/
  - raw/2026-11-27-ignite-2026-book-of-news/source.md
status: active
---

# Ignite 2026 - Security

The source organizes 14 announcement entries by security product/control area.
The [Book of News](https://news.microsoft.com/events/ignite/2026/book-of-news/)
is evidence for the announcement labels, not proof of protection in a tenant.
Licensing, supported agents, collected telemetry, mode and approvals remain
independent delivery prerequisites.

## Agent 365

### Dynamic Agent Risk

Preview risk assessment combines posture, runtime evidence and blast radius.
Partner signals can contribute evidence; Microsoft computes the unified risk
level. A risk score is not a finding that every contributing source is complete.
[Source follow-up](https://aka.ms/secureAIannounce).

### Default management insights

Basic Microsoft-agent usage/activity visibility is expanding as GA without
Agent 365 licensing. Full management/security/governance and third-party
insights still require applicable licenses. Viva Insights retains its stated
50-assigned-Copilot-license threshold.
[Source follow-up](https://techcommunity.microsoft.com/blog/agent-365-blog/whats-new-in-microsoft-agent-365-ignite-2026/4571753).

### Agent and tool governance

Plugin/skill governance is GA. Agent Map use-case classification, gateway/MCP
integration and local/shadow observation are preview. Action center private
preview is planned for December. Observing an agent/tool does not mean it is
blocked, authorized or fully covered.
[Source follow-up](https://techcommunity.microsoft.com/blog/agent-365-blog/whats-new-in-microsoft-agent-365-ignite-2026/4571753).

### Business value reporting

Business Analytics is Frontier preview, with expanded cost/outcome reporting.
Use measured success, satisfaction and assisted time separately from spend
and estimated ROI.
[Source follow-up](https://techcommunity.microsoft.com/blog/agent-365-blog/whats-new-in-microsoft-agent-365-ignite-2026/4571753).

## Codename MDASH

### Agentic code-security pipeline

MDASH is preview for eligible organizations. The source describes attack-surface
mapping, scanning, debate/validation, deduplication and reproduction where
possible, with repository sharding and progress visibility. Future model
adoption depends on completed evaluation; finding counts and model names are
not proof that every reported vulnerability is exploitable.
[Source follow-up](https://aka.ms/perceptionignite).

## Defender

### ISOC and vulnerability shielding

Core ISOC is GA; the full SIEM breadth and 90-day included Defender retention
are preview. Vulnerability shielding is preview temporary protection during
active attacks, not permanent patching or guaranteed exploit prevention.
[Source follow-up](https://techcommunity.microsoft.com/blog/microsoftthreatprotectionblog/ignite-2026-whats-new-in-microsoft-defender--sentinel/4569975).

### Local-agent runtime protection

Named agent-native and network-based Windows integrations are GA for supported
clients. The item specifies Defender for Endpoint P2 and Audit/Block modes.
Audit is not blocking; client and transport support must be checked.
[Source follow-up](https://techcommunity.microsoft.com/blog/microsoftthreatprotectionblog/ignite-2026-whats-new-in-microsoft-defender--sentinel/4569975).

### Zero-day and emerging-threat intelligence

Preview threat tags, prioritization views, notifications and Perception
protection-validation workflows support triage and tenant-aware detection.
Research relevance and protection coverage still require investigation.
[Source follow-up](https://www.microsoft.com/en-us/security/blog/2026/11/17/security-for-the-agentic-era-powered-by-microsoft-perception/).

### On-premises security initiative

Exchange, SharePoint and Skype for Business have product-specific guidance
and phased investments. Some protections exist now; further baseline,
update and temporary-mitigation capabilities roll out over time.
Supported versions, timely patching and recovery remain necessary.
[Source follow-up](https://aka.ms/OnpremSecInitiativeBlog).

## Entra

### Agent identity and enterprise access additions

The Microsoft MCP Server for Enterprise and agentic traffic acquisition are
announced GA. Agent-ID extensions, access-policy plans, credential assurance,
backup, cross-tenant configuration, new privilege/group features, MCP Firewall
and adaptive/local-agent controls have previews. Preview language refers to
the named additions, not a claim that established Entra/PIM products are all
preview. [Source follow-up](https://aka.ms/ignite/entra).

### AI readiness initiatives

The new initiatives are planned for preview in January, not delivered on the
capture date. The source ties patching, phishing-resistant authentication and
agent governance to live evidence and IT-controlled remediation.
[Source follow-up](https://aka.ms/exposurenewsignite).

## Intune

### Local-agent governance on managed devices

Preview discovery, software-compliance policy and Conditional Access can
restrict unapproved agents/devices. Execution Containers and Global Secure
Access address local and network boundaries. Discovery, noncompliance and
actual enforcement are separate states.
[Source follow-up](https://techcommunity.microsoft.com/blog/microsoftintuneblog/what%E2%80%99s-new-in-microsoft-intune-at-ignite/4570003).

## Perception

### Security agents and playbooks

Microsoft Perception, formerly Project Perception, is announced GA for the
core agents/playbooks announced in July. The new web pen-test agent and
exposure-reduction workflow are preview; AI-agent-security playbooks are
private preview. MDASH retains separate eligibility/preview boundaries.

The source describes wider third-party investigation, detection recommendations,
API/MCP integration, approval/audit controls and usage transparency.
Reported triage coverage is scoped to a typical Defender queue, not a guarantee
of coverage for every tenant. Authorized testing and changes require explicit
scope and permission. [Source follow-up](https://aka.ms/perceptionignite).

## Purview

### Classification and agent data protection

New classification/labeling, sensitive-content-aware Copilot DLP and Windows
endpoint-agent protection additions are preview. Unlabeled sensitive-content
detection and per-agent restrictions require supported collection and policy
configuration; preview descriptions are not universal data-leak prevention.
[Source follow-up](https://aka.ms/SecureData/Blog).

## Connected Knowledge

- [Agent 365](../../10-Notes/entities/microsoft-agent-365.md)
- [Perception source history](../project-perception-agentic-security-stack.md)
- [Defender ISOC](../microsoft-defender-agentic-isoc.md)
- [ARTEX defensive context](../artex-agentic-attack-defense.md)
- [AI governance](../../10-Notes/concepts/ai-governance.md)
- [Behavior-first detection](../../10-Notes/concepts/behavior-first-agentic-attack-detection.md)
- [Windows controls](windows.md)
- [Ignite map](../moc-ignite-2026-book-of-news.md)
