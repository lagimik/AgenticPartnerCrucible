Running OpenClaw safely: identity, isolation, and runtime risk

Running OpenClaw safely: identity, isolation, and runtime risk

Link copied to clipboard!

Products and services

Actionable threat insights

Defending against advanced tactics

Self-hosted agent runtimes like OpenClaw are showing up fast in enterprise pilots, and they introduce a blunt reality: OpenClaw includes limited built-in security controls. The runtime can ingest untrusted text, download and execute skills (i.e. code) from external sources, and perform actions using the credentials assigned to it.

This effectively shifts the execution boundary from static application code to dynamically supplied content and third-party capabilities, without equivalent controls around identity, input handling, or privilege scoping.

In an unguarded deployment, three risks materialize quickly:

Credentials and accessible data may be exposed or exfiltrated.

The agent’s persistent state or “memory” can be modified, causing it to follow attacker-supplied instructions over time.

The host environment can be compromised if the agent is induced to retrieve and execute malicious code.

Because of these characteristics, OpenClaw should be treated as untrusted code execution with persistent credentials. It is not appropriate to run on a standard personal or enterprise workstation. If an organization determines that OpenClaw must be evaluated, it should be deployed only in a fully isolated environment such as a dedicated virtual machine or separate physical system. The runtime should use dedicated, non-privileged credentials and access only non-sensitive data. Continuous monitoring and a rebuild plan should be part of the operating model.

This post explains how the two supply chains inherent to self-hosted agents — untrusted code (skills and extensions) and untrusted instructions (external text inputs) — converge into a single execution loop. We examine how this design creates compounding risk in workstation environments, provide a representative compromise chain, and outline deployment, monitoring, and hunting guidance aligned to Microsoft Security controls, including Microsoft Defender XDR. For organizations that still choose to evaluate OpenClaw, we include a minimum safe operating posture.

Clarifying the landscape: runtime vs platform

To reason about controls and avoid applying the wrong mitigations in the wrong place, it is important to separate where code executes from where instructions propagate. These two surfaces are often discussed together, but they behave differently under attack and are typically owned by different teams.

OpenClaw (runtime): A self-hosted agent runtime that runs on a workstation, VM, or container. It can load skills and interact with local and cloud resources. The key security point: it inherits the trust (and risk) of the machine and the identities it can use. Installing a skill is basically installing privileged code. Skills are often discovered and installed through ClawHub, the public skills registry for OpenClaw. With that said, OpenClaw works within the access users grant on their devices. If it has permission to reach certain apps, files, or accounts, it may be able to retrieve additional information from them. For privacy and security considerations, Microsoft Defender recommends using OpenClaw only in isolated environments that do not have access to any non-dedicated credentials or data which must not be leaked.

Moltbook (platform): An agent-focused platform and identity layer where agents post, read, and authenticate through APIs. The key security point is that it can become a high-volume stream of attacker-influenceable content that agents ingest on a schedule. A single malicious post can therefore reach multiple agents.

In practice, OpenClaw expands the code execution boundary within your environment, while Moltbook expands the instruction influence surface at scale. When these two interact without appropriate guardrails, a single malicious input can result in durable, credentialed execution.

How agents shift the security boundary

Most security teams already know how to secure automation. Agents change the risk because the entity deciding what to do isn’t always the one taking the action. At runtime, the agent loads third‑party code, reads untrusted input, and acts using durable credentials, making the runtime environment the new security boundary.

That boundary has three components:

Identity: The tokens the agent uses to do work (SaaS APIs, repos, mail, cloud control planes).

Execution: The tools it can run that change state (files, shell, infrastructure, messages).

Persistence: The ways it can keep changes across runs (tasks, config, schedules).

To summarize, there are two types of security problems called out here:

Indirect prompt injection: Attackers can hide malicious instructions inside content an agent reads and can either steer tool use or modify its memory to affect its behavior over time unless users put strong boundaries in place.

Skill malware: Agents acquire skills from a variety of sources, basically by downloading and running code off the Internet, and can contain malicious code.

Managed platforms Vs. self-hosted runtimes

With managed assistants and agent platforms, security controls typically center on identity scopes, connector governance, and data boundaries, because the runtime and updates are centrally managed. With self-hosted runtimes, that responsibility shifts to the organization. The host system, plugin surface, and local state become part of the trust boundary, and the runtime often operates in close proximity to sensitive developer credentials.

With a self-hosted runtime, you are responsible for the blast radius. The host, plugins, and local state are all within the trust boundary. If the agent is able to browse external content and install extensions, it should be assumed that it will eventually process malicious input. Controls should therefore prioritize containment and recoverability, rather than relying on prevention alone.

End-to-end attack scenario: The poisoned skill

This scenario represents a plausible compromise chain in open agent ecosystems. It maps directly to control points defenders can influence: what is installed, what the runtime can access, and how persistence is established. Public reporting has documented malicious skills appearing in public registries. In some cases, registry content has been straightforward malware packaged as a skill, rather than a subtle lookalike.

Step 1: Distribution

An attacker publishes a malicious skill to ClawHub, sometimes disguised as a utility and sometimes openly malicious, and promotes it through community channels. In other cases, the skill is discovered organically through search and installed because the ecosystem evolves quickly and low-friction installation encourages experimentation. This creates a direct code supply chain path into the runtime.

Step 2: Installation

A developer or an agent initiates installation because the skill appears relevant to a task. In permissive deployments, the runtime may be allowed to execute the installation flow without human approval. In more controlled environments, installation should be treated as an explicit approval event, equivalent to executing third-party code.

Step 3: State access (tokens and durable instructions)

The attacker’s objective is access to agent state, including tokens, cached credentials, configuration data, and transcripts, as well as durable instruction channels that influence future runs, such as task files, scheduled actions, or agent configuration. If durable instructions can be modified through normal interactions, a single injection can persist across executions.

Step 4: Privilege reuse through legitimate APIs

With valid identity material, the attacker can perform actions through standard APIs and tooling. This activity often resembles legitimate automation unless strong monitoring and logging controls are in place.

Step 5: Persistence through configuration

Persistence frequently manifests as durable configuration changes, such as new OAuth consents, scheduled executions, modified agent tasks, or tools that remain permanently approved. The objective is less about deploying malware and more about maintaining long-term control over the automation pathway.

Variant: indirect prompt injection through shared feeds

If agents are configured to poll a shared feed, an attacker can place malicious instructions inside content the agents ingest. This is indirect prompt injection: the payload rides in the instruction supply chain, embedded in external content rather than provided by a trusted operator. In multi-agent settings, a single malicious thread can reach many agents at once. The practical risk is steering tool use or triggering sensitive disclosure in the subset of agents that have high authority and weak gating.

Microsoft Defender and Microsoft Security controls for self-hosted agents

Minimum safe operating posture (if you choose to run OpenClaw)

The safest guidance is to avoid installing and running OpenClaw with primary work or personal accounts and to avoid running it on a device that contains sensitive data. In its current form, assume the runtime can be influenced by untrusted input, its state can be modified, and the host system can be exposed through the agent.

If there is a legitimate requirement to evaluate OpenClaw, the following guardrails should be treated as a baseline:

1) Run only in isolation

Use a dedicated virtual machine or a separate physical device that is not used for daily work. Treat the environment as disposable.

2) Use dedicated credentials and non-sensitive data

Create accounts, tokens, and datasets that exist solely for the agent’s purpose. Assume compromise is possible and plan for regular rotation.

3) Monitor for state or memory manipulation

Regularly review the agent’s saved instructions and state for unexpected persistent rules, newly trusted sources, or changes in behavior across runs.

4) Back up state to enable rapid rebuild

OpenClaw allows state to be snapshotted and restored:

Backing up .openclaw/workspace/ captures the agent’s working state without including credentials.

Backing up the entire .openclaw/ directory also captures tokens and credentials. While this simplifies restoration, it increases backup sensitivity and may be inappropriate if credentials are suspected to be compromised.

5) Treat rebuild as an expected control

Reinstall regularly and rebuild immediately if anomalous behavior is observed. Persistence may appear as subtle configuration changes rather than overt malware deployment.

The table below maps key security actions to concrete implementation approaches using Microsoft Security solutions and related Microsoft controls. Links to implementation of guidance for the Microsoft controls referenced are provided in the References section.

Hunting queries and triage guidance (Microsoft Defender XDR)

These hunting queries are designed to quickly surface where agent runtimes are operating across the environment and to help distinguish deployments that function as privileged automation from those reflecting normal, user-driven behavior, enabling faster scoping, prioritization, and response.

Hunt 1: Discover agent runtimes and related tooling

Use this to inventory where agent runtimes exist, and which identities and command lines they run under.

Triage: confirm the device is part of an approved pilot, validate any control interface exposure is restricted, and review recent installs if the runtime is unexpected.

Hunt 1b: Cloud workloads variant (CloudProcessEvents)

Use this to extend the same inventory to container and Kubernetes workloads that report process telemetry through Defender for Cloud integration.

Use this when agent runtimes may be running in multicloud container environments onboarded through Defender for Cloud so process telemetry lands in CloudProcessEvents.

Triage: validate the workload and namespace map to an approved pilot, confirm container image provenance, and verify that the process and command line are expected for that service.

Hunt 1c: ClawHub skill installs and low-prevalence skill slugs

Use this to identify ClawHub skill installs and surface rare skill slugs across your environment.

Triage: validate that the skill is approved for the pilot, then review the installed skill folder content and correlate with follow-on activity such as new shells, download tools, or outbound connections. Compare the slug against an approved list to catch lookalike naming.

Hunt 2: Extension installs and churn on developer endpoints

Use this to detect extension churn on developer endpoints that often precedes suspicious execution.

Triage: focus on newly created extension folders and unexpected modification bursts. Validate publisher and installation source, then examine what processes the extension spawned.

Hunt 3: High-privilege OAuth apps and consent drift (App Governance)

Use this to surface new or changed high-privilege OAuth apps associated with agent integrations (requires App Governance).

Prerequisite: App Governance must be enabled, so OAuthAppInfo is populated.

Triage: validate business need for high-privilege apps, confirm publisher identity, and investigate sudden changes in privileges or consent scope.

Hunt 4: Unexpected listening services created by agent processes

Use this to detect agent processes opening listening ports, which can indicate exposed control surfaces or unintended services.

Triage: validate whether the listener is required and restricted. If it is reachable beyond the intended boundary, isolate the host and rotate any identities used by the agent.

Hunt 5: Agent runtimes spawning unexpected shells or download tools

Use this to flag agent runtimes spawning shells or download tools that are uncommon in expected agent operation.

Triage: Separate expected automation from opportunistic execution. Prioritize cases where the child process touches credential stores, installs new packages, or opens network connections to unusual destinations.

Security implications for self-hosted agents

Self-hosted agents combine untrusted code and untrusted instructions into a single execution loop that runs with valid credentials. That is the core risk.

Running OpenClaw is not simply a configuration choice. It is a trust decision about which machine, identities, and data you are prepared to expose when the agent processes untrusted input.

For most environments, the appropriate decision may be not to deploy it. If a team proceeds, the defensible posture is to assume compromise is possible: isolate the runtime, constrain what it can access, monitor it continuously, and be prepared to rebuild without delay.

Three actions should be taken immediately: inventory where the runtime is deployed, verify the identities it uses and the permissions associated with them, and identify which inputs can influence tool execution. Tighten controls accordingly and monitor activity end to end. Use the hunting queries provided as a starting point, and treat every finding as an opportunity to reduce blast radius before it is exploited.

Microsoft Defender XDR Advanced Hunting overview (how to run hunts): https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview

CloudProcessEvents table reference: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-cloudprocessevents-table

OAuthAppInfo table reference and prerequisites: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-oauthappinfo-table

Web content filtering in Defender for Endpoint: https://learn.microsoft.com/en-us/defender-endpoint/web-content-filtering

Entra admin consent workflow overview: https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/admin-consent-workflow-overview

Conditional Access overview: https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview

Defender for Cloud Apps App Governance overview: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance

Microsoft Purview Endpoint DLP overview: https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about

This research is provided by Microsoft Defender Security Research with contributions from Idan Hen.

Review our documentation to learn more about our real-time protection capabilities and see how to enable them within your organization.

Microsoft 365 Copilot AI security documentation

How Microsoft discovers and mitigates evolving attacks against AI guardrails

Learn more about securing Copilot Studio agents with Microsoft Defender

Learn more about Protect your agents in real-time during runtime (Preview) – Microsoft Defender for Cloud Apps | Microsoft Learn

Explore how to build and customize agents with Copilot Studio Agent Builder

Microsoft Defender Security Research Team

July 9 16 min read GigaWiper: Anatomy of a destructive backdoor assembled from multiple malware GigaWiper is a destructive backdoor that combines multiple wiping and ransomware-like capabilities into a single operational platform.

GigaWiper: Anatomy of a destructive backdoor assembled from multiple malware

July 6 6 min read 5 insights from Frost & Sullivan’s 2025 Frost Radar™ for Cloud Security Posture Management Read five key learnings from the Frost & Sullivan 2025 Frost Radar™ for CSPM to learn how CSPM is evolving from point-in-time compliance to continuous risk management.

5 insights from Frost & Sullivan’s 2025 Frost Radar™ for Cloud Security Posture Management

July 1 5 min read Microsoft named a leader in the Frost Radar for cloud and application runtime security Frost & Sullivan names Microsoft a leader as cloud and application security converge into unified, runtime risk reduction.

Microsoft named a leader in the Frost Radar for cloud and application runtime security

Get started with Microsoft Security

Protect your people, data, and infrastructure with AI-powered, end-to-end security from Microsoft.

Connect with us on social