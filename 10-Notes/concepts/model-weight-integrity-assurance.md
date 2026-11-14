---
title: Model-Weight Integrity Assurance
type: concept
created: 2026-11-14
updated: 2026-11-14
tags: [ai-security, model-integrity, supply-chain, governance, agents]
sources:
  - https://www.microsoft.com/en-us/security/blog/2026/11/10/detecting-sleeper-agents-hiding-in-ai-model-neurons/
  - raw/2026-11-14-sleeper-agent-model-neurons/source.md
status: active
---

# Model-Weight Integrity Assurance

Model-weight integrity assurance evaluates whether a deployed checkpoint and
its updates have trustworthy provenance and suspicious behavioral modifications.
It is separate from model-file malware scanning, ordinary task evaluation, and
runtime agent authorization.

## Layered Evidence

[Microsoft's sleeper-agent research summary](../../40-Resources/detecting-sleeper-agents-model-neurons.md)
shows why passing the tested evaluations is insufficient: trigger-dependent
behavior may remain dormant while normal tasks appear unaffected.

The source recommends verifying publishers and hashes, comparing checkpoints
against declared bases, auditing unusual weight changes, and testing behavior.
Legitimate fine-tuning and quantization also modify weights, so anomaly findings
require investigation rather than automatic attribution to an attacker.
Preserve audit evidence alongside approved model versions and repeat review
after updates.

## Independent Action Boundaries

**Interpretation:** Intake assurance and runtime containment must remain separate
gates. Restrict permissions, isolate execution, constrain egress, and require
approval for consequential actions even when a checkpoint passes intake checks.
An agent's ability to cause harm depends on the authority and tools surrounding
the model, not just on model behavior.

## Limits

Weight comparison requires an appropriate, verifiable base and access to
checkpoint artifacts. The source does not establish comprehensive backdoor
detection; a clean audit is evidence of reduced risk, not proof of safe behavior.
Microsoft reports no observed weaponization of the described technique.

## Related Pages

- [Sleeper-Agent Research Summary](../../40-Resources/detecting-sleeper-agents-model-neurons.md)
- [Deployment-Context AI Risk](deployment-context-ai-risk.md)
- [AI Governance](ai-governance.md)
- [Open-Weight Model Risk](../../40-Resources/open-weight-model-risk-enterprise.md)
