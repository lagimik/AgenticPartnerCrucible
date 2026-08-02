# Azure Copilot Observability Agent is generally available, with autonomous operations in preview

Source: https://techcommunity.microsoft.com/blog/azureobservabilityblog/azure-copilot-observability-agent-is-generally-available-with-autonomous-operati/4528213

Published: 6/23/2026, 3:52:27 PM
Modified: 6/23/2026, 7:38:23 PM

Author: EfratNauerman

## Description

Complex cloud environments have outpaced manual operations. Agentic cloud operations connect people, tools, and data to streamline investigation workflows and move teams from scattered signals to evidence-backed next steps. With unified observability, teams can investigate Azure-monitored applications, Azure Kubernetes Service (AKS) environments, VMs, Foundry telemetry, infrastructure, and platform signals with greater context and control.
Powered by Azure Monitor, the Azure Copilot Observability Agent is now generally available. It helps engineering, SRE, DevOps, and operations teams move from telemetry and alert noise to investigated issues, explainable reasoning, and recommended next steps that can reduce Time-To-Mitigate (TTM).&nbsp;
Autonomous operations are also available in public preview. They help prepare context and reduce triage work while people remain responsible for mitigation decisions and any changes to the environment.

&nbsp;
From alert noise to investigated issues
The Observability Agent helps teams reduce the effort required to understand operational problems. Instead of starting every investigation from a dashboard, query editor, or alert payload, teams can work with an AI companion that reasons across telemetry, Azure resource context, discovered topology, and custom instructions to identify what changed, what is correlated, and what evidence supports the conclusion.
Teams can start with natural-language exploration and continue into deeper investigations when an issue requires more evidence. That light-to-deep workflow helps responders move from broad questions to a structured investigation without losing the reasoning trail.
Here's what this looks like in practice: after a deployment, several alerts might fire across an app, database dependency, and compute resource. The Observability Agent can group those signals around the affected service, identify when the regression started, compare related dependencies and infrastructure metrics, and capture the findings in an Azure Monitor issue. The responder can then validate the evidence, add team context, route work to the right owner, and decide whether a rollback, configuration change, or code fix is appropriate.
Explainable investigations across Azure-monitored signals
Operations teams need more than a chatbot that answers questions. The Observability Agent follows an investigation workflow: it frames hypotheses, gathers evidence, compares signals by time, scope, and type, rules out weak explanations, and shows the reasoning path behind its findings.
The Observability Agent can help teams:

Investigate incidents and alerts across Azure-monitored applications, Azure Kubernetes Service (AKS) environments, VMs, Foundry telemetry, infrastructure, and platform signals
Correlate related signals to reduce noise and surface higher-signal issues with context
Explore telemetry using natural language while preserving transparency into the supporting data
Compare signals by time, scope, and type to separate likely causes from coincidental changes
Provide a reasoning trail that shows what the agent found, what it ruled out, and why
Recommend next steps that engineers can review before deciding how to act

This same investigation model applies to specialized skills and issue types, including customer's application, Azure Kubernetes Service (AKS), Foundry, VMs, and GenAI issues. When the relevant telemetry is available, the Observability Agent can correlate logs, metrics, traces, alerts, dependencies, resource graph, resource health, activity logs, Foundry telemetry, and changes. This helps teams investigate customer-visible issues with evidence, including latency, token spikes, tool-call failures, agent errors, hallucinations, deployments, API failures, performance regressions, infrastructure dependencies, and platform incidents.
This explainability is central to the product. In production operations, trust is earned through evidence. The Observability agent is built to support human judgment, not bypass it.
.

Azure expertise, with context from your environment
Context matters in every investigation. The same symptom can mean different things depending on application architecture, recent deployments, dependencies, historical incidents, and team practices.
The Observability Agent brings Microsoft and Azure operational knowledge into the investigation experience. It can use discovered topology, Azure resource context, logs, metrics, traces, and custom instructions to ground investigations in signals that are more relevant to your environment.
Native to Azure Monitor, with humans in control
Because the Observability Agent is built into Azure Monitor, teams can use it close to the telemetry, alerts, and workflows they already rely on. Investigations can also be captured as Azure Monitor issues, creating a shared case file for humans and agents to collaborate on evidence, reasoning, and next steps.
The Observability Agent is designed for governed AI operations inside Azure Monitor. Interactive chat and investigations use the signed-in user's identity and Azure role-based access control (RBAC). Prompts and responses are not used to train foundation models, and the agent doesn't restart resources, change configuration, or resolve issues on its own.
Autonomous operations in public preview
Alongside general availability, autonomous operations for the Observability Agent are available in public preview. When enabled, the agent can analyze alerts in the background, correlate related alerts when they likely represent the same incident, create Azure Monitor issues automatically, and run deep investigations on agent-created issues.
This automatic triage helps reduce alert noise by turning streams of individual alerts into higher-signal issues with context, findings, and recommended next steps. Teams can review the issue, continue the investigation, and decide what action to take.
Autonomous operations are designed to prepare context and reduce triage work, not to remove human control. Engineers remain responsible for decisions, approvals, and any changes to the environment.

Next steps

Check out our latest announcements and related blogs: Azure Blog and OMB Blog.
Learn how to use the Observability Agent in Azure Copilot Observability Agent.
Explore how investigations work in Deep investigations in the Azure Copilot Observability Agent.
Learn more on how to Chat with your observability data
Learn how teams preserve context in&nbsp;Azure Monitor issues.
Review preview details in&nbsp;Autonomous operations in the Azure Copilot Observability Agent.

Stay connected

Follow this blog for ongoing deep dives, updates on current capabilities, and a preview of what's coming next.
Live webinar - a walkthrough of real Observability Agent scenarios, best practices, and what's available today - along with a look at what's coming next, and live Q&amp;A with the product team. Register for the Observability Agent webinar.

We'd love your feedback
The Observability agent continues to evolve based on real-world usage and operator feedback. Share your thoughts directly through the Give Feedback option in the experience, or reach us at enauerman@microsoft.com.
