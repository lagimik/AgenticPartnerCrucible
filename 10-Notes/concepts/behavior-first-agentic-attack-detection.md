---
title: Behavior-First Agentic Attack Detection
type: concept
created: 2026-11-27
updated: 2026-11-27
tags: [security, behavioral-detection, agentic-ai, telemetry, attribution]
sources:
  - raw/2026-11-27-artex-agentic-attack-defense/source.md
  - https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/
status: active
---

# Behavior-First Agentic Attack Detection

Behavior-first detection prioritizes corroborated sequences of activity across application, endpoint, identity, and cloud systems over a mutable tool name or network indicator. [Microsoft's ARTEX report](https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/#identifying-artex-network-activity) motivates the pattern with adaptive bursts, retries, and short transitions between established attack stages.

## Evidence discipline

| Question | Evidence requirement |
| --- | --- |
| Is the activity unusual? | Compare request diversity, errors, execution, sign-ins, and stage transitions with the environment's ordinary automation. |
| Are events related? | Join affected assets and identities on a common timeline; seek independent application, endpoint, identity, and cloud corroboration. |
| Can the observation be trusted? | Confirm log collection, retention, sensor coverage, schema, and query scope before interpreting results. |
| What can be concluded? | Separate observed compromise or misuse from suspected automation and any specific framework or actor attribution. |
| What response is supported? | Match the incident evidence to approved action scope, deployed controls, permissions, business impact, and recovery ownership. |

Static user-agent matches and ordinary tools can help prioritize review, but their presence is not proof of maliciousness or ARTEX attribution; their absence is not proof of safety. Sample thresholds need calibration, and an empty query over missing data is an evidence gap, not an all-clear. [Source hunting guidance](https://www.microsoft.com/en-us/security/blog/2026/11/25/what-defenders-need-to-know-artex-agentic-ai-framework-threat-actors-abuse/#hunting)

**Interpretation:** Improve resistance to indicator changes by retaining cross-stage evidence and analyst-reviewed verdicts. Speed and correlation are not exclusive fingerprints of AI: other frameworks and legitimate automation can look similar. This is a reusable investigation principle, not a validated detector, attribution method, or promise of complete coverage.

## Related pages

- [ARTEX](../entities/artex.md)
- [ARTEX Agentic Attack Defense](../../40-Resources/artex-agentic-attack-defense.md)
- [AI Threat Landscape and Agent Security](ai-threat-landscape-mddr-2026.md)
- [Project Perception Agentic Security Stack](../../40-Resources/project-perception-agentic-security-stack.md)
