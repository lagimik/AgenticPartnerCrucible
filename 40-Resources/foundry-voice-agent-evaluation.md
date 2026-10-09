---
title: Evaluating Voice Agents with Foundry Multi-Turn Evaluators
type: resource
created: 2026-10-09
updated: 2026-10-09
tags: [microsoft-foundry, voice-agents, evaluation, reliability]
sources:
  - https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/evaluating-voice-agents-how-reliable-are-foundrys-multi-turn-evaluators/4559697
  - raw/2026-10-09-github-open-issues-116-124/issues.md
  - raw/2026-10-09-github-open-issues-116-124/sources.md
status: active
---

## Summary

The Microsoft Foundry article assesses multi-turn voice-agent evaluators using task-completion and generated-rubric approaches, call-level accuracy, agent ranking, judge agreement, and repeatability. It treats evaluation as a comparison against labeled benchmark traces, not a guarantee of production reliability.

## Reported Study Results

The article describes an internal Microsoft study using the tau-Voice benchmark. For task completion, it reports approximately 83% balanced accuracy and 85% raw accuracy with gpt-5.6-terra as judge on the retained benchmark calls. In a separate generated-rubric experiment, the article describes scoring 114 conversations. Agent-ranking results across seven retained GPT judges had Kendall's tau values from 0.758 to 0.818, with mean pairwise agreement of 89.8% across the 12 ranked agents.

These figures are specific to the article's retained benchmark traces and study setup. The article says the study did not test statistical significance, establish generalization beyond those traces, or evaluate pricing, latency, or economic value. It does not establish a default judge; do not present the figures as production guarantees or cross-vendor benchmarks.

## Partner Relevance

Use the evaluation dimensions to shape a voice-agent test plan: write task-level pass criteria, retain representative multi-turn traces, compare agent ordering as well as individual-call outcomes, and check whether evaluator judgments are repeatable. Keep a human review path for ambiguous or consequential results.

## Related Pages

- [[reliable-voice-agents-practical-guide]]
- [[ai-agent-lifecycle]]
