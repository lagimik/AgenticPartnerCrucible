# Build Apps in Copilot Cowork and Copilot Studio

Captured: 2026-09-12

## Provenance

- Source: https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/build-apps-in-copilot-cowork-and-copilot-studio/
- Published: 2026-09-10
- Author: Ryan Cunningham, Corporate Vice President, Microsoft Copilot Studio and Microsoft Power Platform
- Supporting billing documentation: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits
- Supporting Work IQ documentation: https://learn.microsoft.com/en-us/microsoft-copilot-studio/add-work-iq

## Direct Source Summary

Microsoft introduced natural-language app building in Copilot Cowork and Copilot Studio. In Cowork, users invoke the `/app` skill through the Microsoft Frontier program. Native app building in Copilot Studio was announced as rolling out in public preview.

Builders describe the business outcome, users, data, and actions they need. The system creates a working app scaffold that can be refined through conversation, previewed, and inspected at the code level.

The apps can connect to organizational and third-party data through connectors, including Work IQ for Microsoft 365 organizational context. Connected apps can both retrieve information and write results back to permitted systems.

Microsoft describes the resulting applications as full-stack apps built with open standards. The lifecycle includes Git-backed source control, deployment stages, and version isolation. Microsoft Entra identity and organizational data and connector policies apply by default. Published apps appear in the Microsoft 365 admin center for centralized inventory and operational control and can be discovered at `managedapps.cloud.microsoft.com`.

Building and running apps follows usage-based billing. Microsoft Learn identifies apps built with Copilot Cowork as a Copilot Credits service that administrators can govern through spending policies, limits, alerts, access controls, and consumption reporting.

## Availability Boundaries

- The `/app` skill in Copilot Cowork requires the Microsoft Frontier program.
- Native Copilot Studio app building was announced as public preview rolling out over the following week.
- Work IQ in Copilot Studio is a preview capability and uses consumptive billing.
- Preview features are not intended for production use and can have restricted functionality.

## Evidence Excerpts

- "App building starts with a conversation."
- "Full-stack apps built using open standards."
- "Git-backed source control, deployment stages, and version isolation."
- "IT administrators have centralized visibility in the Microsoft 365 admin center."
- "App building and running follows the usage-based billing model."

## Interpretation

This announcement expands Copilot Studio from agent and workflow authoring toward a unified business-solution surface that also produces interactive applications. The durable delivery pattern is conversational intent followed by enterprise grounding, governed action, inspectable implementation, application lifecycle management, centralized administration, and usage controls.
