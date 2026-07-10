This browser is no longer supported.

Upgrade to Microsoft Edge to take advantage of the latest features, security updates, and technical support.

Access to this page requires authorization. You can try signing in or changing directories .

Access to this page requires authorization. You can try changing directories .

This guidance provides a structured framework to help organizations successfully adopt AI agents as part of their broader AI adoption strategy . It addresses the unique considerations that AI agents introduce. The series highlights Microsoft 365 agents and guidance for building custom agents using Microsoft Foundry and Microsoft Copilot Studio. It also includes strategies for designing an organization-wide data architecture to support AI agents at scale.

Through this guidance, leaders will gain actionable insights across four key areas: (1) plan for agents , (2) govern and secure agents , (3) build agents , and (4) manage agents ( see figure 1. ).

Figure 1. Microsoft's AI agent adoption process.

What is an AI agent?

An AI agent is a flexible software program that uses generative AI models to interpret inputs, such as system events, user messages, or other agent messages, reason through problems, and decide on the most appropriate actions. Unlike traditional applications that rely on fixed rules, agents dynamically orchestrate workflows based on real-time context. This adaptability enables them to manage ambiguity and complexity that deterministic software cannot. Agents are built on five core components:

Generative AI model serves as the agent's reasoning engine. It processes instructions, integrates tool calls, and generates outputs, either as messages to other agents or as actionable results.

Generative AI model serves as the agent's reasoning engine. It processes instructions, integrates tool calls, and generates outputs, either as messages to other agents or as actionable results.

Instructions define the scope, boundaries, and behavioral guidelines for the agent. Clear instructions prevent scope creep and ensure the agent adheres to business rules.

Instructions define the scope, boundaries, and behavioral guidelines for the agent. Clear instructions prevent scope creep and ensure the agent adheres to business rules.

Retrieval provides the grounding data and context required for accurate responses. Access to relevant, high-quality data is critical for reducing hallucinations and ensuring relevance.

Retrieval provides the grounding data and context required for accurate responses. Access to relevant, high-quality data is critical for reducing hallucinations and ensuring relevance.

Actions are the functions, APIs, or systems the agent uses to perform tasks. Tools transform the agent from a passive information retriever into an active participant in business processes.

Actions are the functions, APIs, or systems the agent uses to perform tasks. Tools transform the agent from a passive information retriever into an active participant in business processes.

Memory stores conversation history and state. Memory ensures continuity across interactions, allowing the agent to handle multi-turn conversations and long-running tasks effectively.

Memory stores conversation history and state. Memory ensures continuity across interactions, allowing the agent to handle multi-turn conversations and long-running tasks effectively.

Difference from retrieval-augmented generation (RAG)

Standard RAG applications follow a deterministic retrieval process to answer queries. AI agents use a generative model to decide which knowledge and tools to use at each step. This adaptive approach enables multi-step reasoning and complex problem-solving, but it also introduces nondeterministic behavior that requires robust testing and governance.

For technical definitions, see What is an agent? and what is a workflow? .

Adopting AI agents drives specific organizational outcomes. Understanding these benefits helps justify investment and prioritize use cases.

Efficiency : Agents automate repetitive, low-value tasks. It reduces manual effort and operational costs, allowing resources to focus on strategic initiatives.

Efficiency : Agents automate repetitive, low-value tasks. It reduces manual effort and operational costs, allowing resources to focus on strategic initiatives.

Speed : Agents can process information and execute decisions fast, which can improve service delivery times and responsiveness to market changes.

Speed : Agents can process information and execute decisions fast, which can improve service delivery times and responsiveness to market changes.

Scalability : Agents handle fluctuating workloads, and this elasticity supports growth and seasonal demand spikes.

Scalability : Agents handle fluctuating workloads, and this elasticity supports growth and seasonal demand spikes.

These benefits lead to measurable results such as lower operating costs, improved customer satisfaction, and faster innovation. For leaders, this means AI agents aren't just a technology investment. They're a strategic lever for growth and competitiveness. See Business plan for AI agents for more business rationale and use cases.

Organizations typically deploy three categories of agents. Each category offers a different level of autonomy and business impact.

Productivity agents. These agents focus on information retrieval and synthesis to accelerate decision-making. They use knowledge tools to draw data from various sources and retrieve it for the user. This capability increases employee accuracy and reduces time spent searching for information in scenarios like customer service support and internal knowledge management.

Productivity agents. These agents focus on information retrieval and synthesis to accelerate decision-making. They use knowledge tools to draw data from various sources and retrieve it for the user. This capability increases employee accuracy and reduces time spent searching for information in scenarios like customer service support and internal knowledge management.

Action agents. These agents perform specific tasks within defined workflows, such as updating records or triggering processes. They use knowledge tools combined with action tools to accomplish tasks. This approach streamlines operations and reduces manual data entry errors in use cases like service ticket creation and system monitoring.

Action agents. These agents perform specific tasks within defined workflows, such as updating records or triggering processes. They use knowledge tools combined with action tools to accomplish tasks. This approach streamlines operations and reduces manual data entry errors in use cases like service ticket creation and system monitoring.

Automation agents. These agents manage complex, multi-step processes with minimal oversight. They use knowledge tools and action tools, plus triggers that determine when to run, stop, or escalate an issue. This autonomy enables scalable automation for scenarios like supply chain optimization, though it requires rigorous governance to manage the increased complexity.

Automation agents. These agents manage complex, multi-step processes with minimal oversight. They use knowledge tools and action tools, plus triggers that determine when to run, stop, or escalate an issue. This autonomy enables scalable automation for scenarios like supply chain optimization, though it requires rigorous governance to manage the increased complexity.

To realize the potential of AI agents, align the adoption strategy with specific business outcomes. The following sections explore how to create internal and customer-facing impact and guide teams to use agents effectively.

Was this page helpful?

Need help with this topic?

Want to try using Ask Learn to clarify or guide you through this topic?

Additional resources

Last updated on 2025-12-04

Was this page helpful?

Need help with this topic?

Want to try using Ask Learn to clarify or guide you through this topic?

Consumer Health Privacy