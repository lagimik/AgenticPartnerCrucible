---
title: Securing Edge AI in Customer-Owned Environments
type: resource
created: 2026-09-05
updated: 2026-09-05
tags: [edge-ai, confidential-computing, attestation, provenance, agent-security]
sources:
  - https://www.microsoft.com/en-us/security/blog/2026/09/04/secure-edge-ai-customer-owned-environments/
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# Securing Edge AI in Customer-Owned Environments

Security architecture for AI inference running on infrastructure that customers own and operate, including disconnected environments.

## Trust Model

- **Attestation** verifies that hardware, firmware, runtime, and protected execution state match an approved baseline.
- **Provenance** verifies the model weights, agent definitions, tool descriptors, retrieval indexes, and other behavior-shaping artifacts.
- **Deterministic mediation** keeps authorization outside the model by allowlisting actions, constraining arguments and frequency, and releasing scoped credentials only after policy approval.
- **Renewable evidence** treats access to sensitive models, keys, and data as a lease that expires when the environment no longer proves an acceptable state.

Model output should recommend actions, not authorize them. High-consequence or irreversible operations still require an independent approval or fail-safe interlock.

## Related Pages

- [[ai-governance]]
- [[safe-agent-controls-foundry]]
- [[agent-recovery-engineering]]
