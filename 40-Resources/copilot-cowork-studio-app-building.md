---
title: App Building in Copilot Cowork and Copilot Studio
type: resource
created: 2026-09-12
updated: 2026-09-12
tags:
  - copilot-cowork
  - copilot-studio
  - business-applications
  - agentic-coding
  - governance
  - alm
sources:
  - https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/build-apps-in-copilot-cowork-and-copilot-studio/
  - https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits
  - https://learn.microsoft.com/en-us/microsoft-copilot-studio/add-work-iq
  - raw/2026-09-12-copilot-cowork-studio-app-building/source.md
status: active
---

# App Building in Copilot Cowork and Copilot Studio

Microsoft is adding conversational, full-stack business-app creation to Copilot Cowork and Copilot Studio. Builders start with an outcome and refine a working application through natural language while retaining access to preview and underlying code.

## Build Pattern

```text
Describe outcome, users, data, and actions
  -> generate app scaffold
  -> connect enterprise data and services
  -> preview and inspect code
  -> govern, version, deploy, and operate
```

The experience is intended to support information workers who want to stay focused on the solution and advanced makers or developers who need deeper implementation control.

## Enterprise Foundation

- Connectors provide access to Microsoft and third-party business systems.
- Work IQ can add organizational context from Microsoft 365, subject to its preview terms and administrative controls.
- Connected applications can retrieve data and write results back to permitted systems.
- Apps use open standards and support Git-backed source control, deployment stages, and version isolation.
- Microsoft Entra identity and organizational connector and data policies apply by default.
- The Microsoft 365 admin center provides an inventory of published apps and operational governance controls.

The important distinction is that generating a user interface is only the first step. Enterprise readiness depends on identity, data boundaries, write permissions, lifecycle management, operational visibility, and cost controls.

## Availability and Billing

- The Copilot Cowork `/app` skill is available through the Microsoft Frontier program.
- Native Copilot Studio app building was announced as a public preview rolling out from September 10, 2026.
- Building and running apps uses usage-based billing.
- Apps built with Copilot Cowork consume Copilot Credits and can be governed through spending policies, limits, alerts, and consumption reporting in the Microsoft 365 admin center.
- Work IQ in Copilot Studio is a preview capability with consumptive billing.

## Partner Relevance

- Extend Copilot and agent practices into interactive business-process applications.
- Package discovery around outcomes, users, systems of record, write actions, identity, and governance before generating the app.
- Add application lifecycle management, testing, deployment, support, and cost governance to rapid prototyping offers.
- Treat Frontier and preview capabilities as controlled evaluation opportunities rather than production commitments.

## Related Pages

- [[copilot-studio]]
- [[cowork-partner-launch-kit]]
- [[agent-cicd]]
- [Copilot Studio Workload](../100-Crucible/PowerPlatform-CopilotStudio.md)
