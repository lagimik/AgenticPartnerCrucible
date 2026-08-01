---
title: "Microsoft Agent 365 Runtime Protection and Threat Detection"
type: resource
created: 2026-08-01
updated: 2026-08-01
tags:
  - security
  - ai-security
  - agent-365
  - microsoft-defender
  - runtime-protection
  - threat-detection
sources:
  - https://techcommunity.microsoft.com/blog/microsoft-security-blog/securing-ai-agents-at-runtime-real-time-protection-and-threat-detection-for-micr/4541255
  - raw/2026-08-01-github-issues/issues.md
status: active
claims:
  - id: claim-001
    text: "Microsoft Defender threat detection for Microsoft Agent 365 agents is in public preview."
    confidence: 0.98
    status: provisional
    evidence:
      - source: https://techcommunity.microsoft.com/blog/microsoft-security-blog/securing-ai-agents-at-runtime-real-time-protection-and-threat-detection-for-micr/4541255
        kind: quote
        excerpt: "Threat detection for Microsoft Agent 365 agents - now in public preview."
    captured: 2026-08-01
    updated: 2026-08-01
  - id: claim-002
    text: "Microsoft Defender real-time protection for WorkIQ and custom MCP servers is generally available."
    confidence: 0.98
    status: provisional
    evidence:
      - source: https://techcommunity.microsoft.com/blog/microsoft-security-blog/securing-ai-agents-at-runtime-real-time-protection-and-threat-detection-for-micr/4541255
        kind: quote
        excerpt: "Real-time protection for WorkIQ and Custom MCP servers (General Availability)"
    captured: 2026-08-01
    updated: 2026-08-01
---

# Microsoft Agent 365 Runtime Protection and Threat Detection

Microsoft Security announcement describing defense-in-depth runtime security for AI agents through Microsoft Defender: inline protection blocks malicious tool interactions, while threat detection supplies SOC teams with alerts and investigation context.

## Capabilities

- **Threat detection:** Analyzes agent interactions, tool usage, and execution patterns and surfaces alerts in Microsoft Defender XDR.
- **Broad agent visibility:** Supports observability signals from Copilot Studio, Microsoft Foundry, Microsoft 365 Copilot Agent Builder, and agents integrated through the Agent 365 SDK.
- **Real-time tool protection:** Evaluates calls and responses for registered WorkIQ and custom MCP servers against security policy and allows or blocks them within the execution flow.
- **SOC integration:** Uses familiar Microsoft Defender workflows, Advanced Hunting, and investigation experiences.

## Threat Coverage

The announcement identifies indirect prompt injection, evasion, malicious content propagation, secret leakage, LLM reconnaissance, suspicious IP access, and communication with untrusted domains as covered scenarios across detection and inline protection.

## Partner Relevance

- Build Agent 365 security assessments around runtime signals, tool boundaries, and SOC readiness.
- Demonstrate the distinction between preventive inline enforcement and detective investigation workflows.
- Connect Copilot Studio, Foundry, and custom-agent projects to Microsoft Defender operations.

## Related Pages

- [Security Workloads](../100-Crucible/SecuritySolutionArea.md)
- [Cyber Pulse: AI Security Report](cyber-pulse-ai-security-report.md)
- [Policy-to-Proof AI Governance](policy-to-proof-ai-governance.md)
- [AI Governance](../10-Notes/concepts/ai-governance.md)
