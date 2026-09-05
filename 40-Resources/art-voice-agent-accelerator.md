---
title: ART Voice Agent Accelerator
type: resource
created: 2026-09-05
updated: 2026-09-05
tags: [voice-agents, azure-communication-services, microsoft-foundry, realtime-ai]
sources:
  - https://github.com/Azure-Samples/art-voice-agent-accelerator
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# ART Voice Agent Accelerator

Azure sample that supplies the end-to-end voice plumbing for customizable, multi-agent-ready experiences: telephony, bidirectional media streaming, speech and realtime inference, orchestration, tools, observability, infrastructure, and load testing.

## Design Choices

- **SpeechCascade:** Azure Speech STT -> LLM -> TTS, with granular control over VAD, phrase lists, voices, and the event loop.
- **VoiceLive:** managed voice-to-voice through Azure Voice Live for lower-latency setup, server-side turn detection, noise reduction, and native tool calling.
- **Transport:** Azure Communication Services plus FastAPI and WebSockets supports PSTN, SIP transfer, IVR/DTMF, barge-in, and scalable streaming.

The repository is an accelerator rather than a production guarantee. Teams still own compliance validation, security hardening, SRE practices, infrastructure policy, and release controls.

## Related Pages

- [[azure-ai-foundry]]
- [[ai-agent-lifecycle]]
- [[reliable-voice-agents-practical-guide]]
