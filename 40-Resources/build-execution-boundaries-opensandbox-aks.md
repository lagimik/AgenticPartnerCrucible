---
title: Build Execution Boundaries with OpenSandbox and AKS
type: resource
created: 2026-10-03
updated: 2026-10-03
tags:
  - agentic-ai
  - sandboxing
  - aks
  - container-apps
  - architecture-pattern
  - security-boundary
sources:
  - raw/2026-10-03-opensandbox-aks-execution-boundaries/source.md
status: active
---

# Build Execution Boundaries with OpenSandbox and AKS

A practitioner's technical deep-dive (Microsoft Developer Community Blog,
2026-10-02) that untangles MCP, OpenSandbox, and Kata Containers, then
builds and evaluates a concrete reference project: a FastAPI backend
dispatching per-session OpenSandbox/Kata sandboxes on AKS, running Copilot
CLI and local MCP tools, with model inference via an external API (not
hosted on AKS). It is a first-person engineering opinion piece, not official
Microsoft product documentation — treat its recommendations as one
practitioner's tested judgment, while its referenced release-status caveats
and official comparison links are worth verifying independently.

## Why It Matters for Partners

- Gives partners building or advising on agentic AI platforms a vetted,
  three-way comparison (OpenSandbox on AKS vs. Azure Container Apps
  Sandboxes vs. Azure Container Apps Dynamic Sessions) with concrete
  dimensions — isolation guarantee, state/snapshot model, startup latency,
  operational ownership, and team-fit — usable directly in an architecture
  decision record.
- Flags that Azure Container Apps Sandboxes carried mixed GA/early-access
  signals in official docs at review time; partners scoping this capability
  for a customer should confirm current release status, RBAC requirements
  (Container Apps SandboxGroup Data Owner), and regional availability before
  committing delivery timelines.
- Documents a credential-exposure-reduction pattern (Credential Vault egress
  sidecar with placeholder injection) that partners can reuse when designing
  how sandboxed agent tool calls reach governed external APIs without
  handing long-lived secrets to generated/untrusted code.
- Supplies a five-question production-readiness checklist (session
  ownership, state durability, side-effect authorization, failure handling,
  backend portability) that partners can turn into a workshop or assessment
  rubric before recommending any sandbox platform as "production-ready" for
  a customer.
- Reinforces — with concrete engineering examples (Markdown-table
  corruption through a CLI/log pipeline, startup-latency decomposition) —
  that an isolation boundary and a working data/acceptance contract are
  separate engineering problems partners must test independently.

## Summary

See [[agent-execution-sandbox-isolation]] for the full concept notes (the
MCP/OpenSandbox/Kata distinction, the three-way Azure comparison table,
credential handling, and the production-readiness checklist) and the
preserved source at
`raw/2026-10-03-opensandbox-aks-execution-boundaries/source.md`.

## Source

[When AI Starts Taking Action: Building Execution Boundaries with OpenSandbox and AKS](https://techcommunity.microsoft.com/blog/azuredevcommunityblog/when-ai-starts-taking-action-building-execution-boundaries-with-opensandbox-and-/4561601) — Microsoft Developer Community Blog, 2026-10-02.

## Related Pages

- [[agent-execution-sandbox-isolation]]
- [[agent-first-platforms-foundry-container-apps]]
- [[model-context-protocol-mcp]]
- [[multitenant-ai-agent-governance-architecture]]
