---
title: Fabric Data Engineering Agent - Project Osmos
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-fabric, project-osmos, data-engineering, agents, preview]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/introducing-the-data-engineering-agent-for-fabric-project-osmos/5377944
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# Fabric Data Engineering Agent - Project Osmos

[Project Osmos](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview)
is a **preview**, Fabric-hosted data engineering agent that plans, executes,
and validates persistent tasks. The October 29 announcement was reviewed via
official RSS item 5377944 after the submitted article page returned HTTP 403;
Microsoft Learn independently confirms status and prerequisites.

## Source Summary

A supported local coding agent creates and steers a remote task through Skills
for Fabric. Fabric executes Spark work, retains state and evidence, and keeps
running after the client disconnects. Tasks can inspect data, create notebooks,
transform Delta tables, validate results, and accept follow-up guidance.

The selected lakehouse is the default Spark-session lakehouse, **not an
automatic resource isolation boundary**. Tasks can reach other authorized
resources. Instructions guide scope; Fabric and OneLake permissions enforce
access.

## Readiness and Review

The [quickstart](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started)
requires eligible nontrial Fabric capacity, a lakehouse, Contributor-or-higher
workspace access, required Copilot tenant settings, Azure CLI, and a supported
client. Review applicable cross-region processing/storage settings. The
OpenAI-subprocessor setting is optional and distinct from the required Azure
OpenAI setting; disabling it does not disable all Project Osmos use.

Review sources, outputs, write safety, promotion, reruns, schema evolution,
artifact destinations, and reasoning effort before execution. Define validation
such as uniqueness, reconciliation, null checks, and business-rule tests.
Execution consumes language-model tokens and Spark resources; validation and
retries are not cost-free.

**Partner interpretation:** use bounded nonproduction pilots for migration,
incremental-load repair, and data-quality work with human acceptance of evidence.
Preview terms do not provide a production SLA; generated output still needs
business validation.

## Related

- [Evidence-validated agentic data engineering](../10-Notes/concepts/evidence-validated-agentic-data-engineering.md)
- [Skills for Fabric](skills-for-fabric.md)
- [Capacity observability and protection](fabric-capacity-observability-and-protection.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
