---
title: Evidence-Validated Agentic Data Engineering
type: concept
created: 2026-11-02
updated: 2026-11-02
tags: [agents, data-engineering, validation, governance]
sources:
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-overview
  - https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-agent-get-started
status: active
---

# Evidence-Validated Agentic Data Engineering

Generated code that executes successfully is not sufficient evidence that a
data transformation preserves business meaning. Agentic data engineering needs
an outcome contract, enforced access boundaries, rerun rules, and validation
against the actual target data.

The Project Osmos documentation supplies a concrete preview implementation:
persistent Fabric tasks plan, execute, test, and report results, while people
review settings and decide whether the evidence satisfies requirements.

## Reusable Acceptance Contract

- Specify sources, outputs, business rules, and named resources.
- Enforce least privilege through platform permissions, not task instructions.
- Choose staging and promotion behavior, permitted schema changes, and
  idempotent rerun semantics before writes begin.
- Test row counts, uniqueness, reconciliation, and domain-specific rules;
  include data changes that would invalidate the first plausible result.
- Preserve task history, errors, validation evidence, and human acceptance.
- Budget execution, retries, model reasoning, and validation together.

**Interpretation:** persistent context improves continuity, but it does not
establish correctness or authorize broader access. Local client disconnection
also does not mean a remote task has stopped consuming resources.

## Related

- [Project Osmos prerequisites and preview limits](../../40-Resources/fabric-project-osmos-data-engineering-agent.md)
- [Agent recovery engineering](agent-recovery-engineering.md)
- [Capacity admission and cost governance](capacity-admission-and-cost-governance.md)
