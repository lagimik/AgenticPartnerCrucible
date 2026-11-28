---
title: ARTEX
type: entity
created: 2026-11-27
updated: 2026-11-27
tags: [artex, agentic-ai, dual-use, threat-intelligence]
sources:
  - raw/2026-11-27-artex-agentic-attack-defense/source.md
  - https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/
status: active
---

# ARTEX

ARTEX is a dual-use AI-powered penetration-testing framework. [Microsoft Threat Intelligence's November 25, 2026 report](https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/) describes threat-actor abuse of its coordinated goal/planning/worker/reporting agents to accelerate existing attack workflows. It is not a Microsoft product, and use of the framework does not inherently identify a particular threat actor.

## Defensive distinctions

- The source reports adaptive, machine-speed retries across web, credential, endpoint, and cloud stages; it does not claim ARTEX invents new techniques.
- Model/provider flexibility means one model vendor's controls and telemetry cannot be assumed to encompass all deployments.
- Default user agents and common tools are supporting investigation clues, not sufficient attribution; compare the sequence with legitimate automation and corroborating evidence.

All observations above are attributed to the report; no framework installation, execution, or independent attack investigation was performed.

## Related pages

- [ARTEX Agentic Attack Defense](../../40-Resources/artex-agentic-attack-defense.md) - Defensive priorities, telemetry prerequisites, and control limitations.
- [Behavior-First Agentic Attack Detection](../concepts/behavior-first-agentic-attack-detection.md)
- [AI Threat Landscape and Agent Security](../concepts/ai-threat-landscape-mddr-2026.md)
- [Project Perception Agentic Security Stack](../../40-Resources/project-perception-agentic-security-stack.md) - Separate Microsoft defensive platform context.
