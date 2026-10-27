---
title: Project Perception Agentic Security Stack
type: resource
created: 2026-08-01
updated: 2026-10-27
tags:
  - security
  - agentic-security
  - project-perception
  - ai-security
  - mdash
sources:
  - https://blogs.microsoft.com/blog/2026/10/19/securing-the-agentic-insider/
  - raw/2026-10-27-github-open-issues-125-134/issues.md
  - raw/2026-10-27-github-open-issues-125-134/sources.md
  - https://blogs.microsoft.com/blog/2026/07/27/rethinking-security-for-the-age-of-ai/
  - raw/2026-08-01-github-open-issues-30-41/issues.md
status: active
---

# Project Perception Agentic Security Stack

Microsoft blog introducing Project Perception, an agentic security system built around a new cyber stack for the age of AI and machine-speed attacks.

## Summary

Project Perception coordinates red team, blue team, and green team agents in a closed-loop defense system that can perceive risk, reason over context, and take action while keeping humans in control. The proposed cyber stack includes signals and sensors, security context, models, a harness, agents, and actuators.

The article also connects Project Perception to MDASH and MAI-Cyber-1-Flash for software vulnerability management, including reported CyberGym performance and cost improvements.

## October Update: The Agentic Insider

The [October 19 companion article](https://blogs.microsoft.com/blog/2026/10/19/securing-the-agentic-insider/)
extends the earlier security-stack vision to trusted internal agents. Risk can
arise from excessive permissions, changing context, or goal-directed behavior
without an external compromise.

Microsoft describes agent discovery and identity, permission management,
cross-layer signals, dynamic risk assessment, and guardian-agent supervision
and containment across identity, data, endpoints, network, cloud, and runtime.
Human security practitioners remain accountable for judgment and intervention.

**Interpretation:** Inventory agent identities and authority, constrain
side-effecting actions, correlate activity with business context, and exercise
containment and escalation before expanding autonomy. The post's future model
transparency goals are not a present API guarantee, universal protection claim,
or general-availability announcement for every proposed control.

## Partner relevance

- Sharpens the partner narrative for AI defending against AI.
- Connects agentic security, Microsoft Defender/Sentinel/Entra/Purview signals, MDASH, specialized cyber models, and automated remediation.
- Useful for executive security conversations about why legacy alert-centric security operating models need to evolve.

## Related pages

- [SAFE Agent Controls](safe-agent-controls-foundry.md)
- [Deployment-Context AI Risk](../10-Notes/concepts/deployment-context-ai-risk.md)
- [Defender Agentic ISOC](microsoft-defender-agentic-isoc.md)
- [Security Workloads](../100-Crucible/SecuritySolutionArea.md)
