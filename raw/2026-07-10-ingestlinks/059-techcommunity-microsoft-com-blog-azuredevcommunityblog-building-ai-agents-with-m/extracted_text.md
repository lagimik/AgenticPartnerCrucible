Microsoft Community Hub

Communities Products

Microsoft Developer Community Blog

Building AI Agents with Microsoft Foundry: A Progressive Lab from Hello World to Self-Hosted

AI agent development has a steep on-ramp. The combination of new SDKs, tool-calling patterns, model selection decisions, retrieval-augmented generation, and deployment concerns means most developers spend more time wiring things together than actually building anything useful. The Microsoft Foundry Agent Lab is a structured, open-source demo series designed to change that — nine self-contained demos, each adding exactly one new concept, all built on the same Microsoft Foundry SDK and a single model deployment.

This post walks through what the lab contains, how each demo works under the hood, and the architectural decisions that make it a useful reference for AI engineers building production agents.

Why a Progressive Lab?

Agent frameworks can be overwhelming. A developer who opens a rich example with RAG, tool-calling, streaming, and a custom UI all at once has no clear line of sight to which parts are essential and which are embellishments. The Foundry Agent Lab takes the opposite approach: start with the absolute minimum and introduce one new primitive per demo. By the time you reach Demo 8, you have seen every major capability — not in one monolithic sample, but in a layered sequence where each addition is visible and understandable.

The Model Router: One Deployment to Rule Them All

Before diving into the demos, it is worth understanding the one architectural decision that ties the entire lab together: every agent uses model-router as its model deployment.

Model Router is a Microsoft Foundry capability that inspects each request at inference time and routes it to the optimal available model — weighing task complexity, cost, and latency. A simple factual question goes to a fast, cheap model. A complex tool-calling chain with code generation gets routed to a frontier model. You write zero routing logic.

The lab's MODEL-ROUTER.md file contains empirical observations from running all nine demos. A sample of what the router selected:

This is the strongest signal in the lab: you do not need to reason about model selection. You declare what your agent needs to do; the router handles the rest, and it chooses correctly.

Demo 0: The Minimum Viable Agent

The hello-demo establishes the baseline pattern used by every subsequent demo. Two files: one to register the agent, one to chat with it.

Registering the agent

Authentication uses DefaultAzureCredential , which works with az login locally and with managed identity in production — no API keys anywhere in the code.

Chatting with the agent

The conversation object is server-side. You pass its ID on every turn; the history lives in Foundry, not in a local list. This is the Responses API pattern — distinct from the older Completions or Chat Completions APIs.

Demo 1: Function Tools and the Tool-Calling Loop

Demo 1 adds function calling against a real weather API. The key insight here is that the model does not execute the function — it requests the execution, and your code executes it locally, then feeds the result back.

Declaring a function tool

The tool-calling loop

The strict=True parameter on FunctionTool enforces structured outputs — the model must return arguments that match the declared JSON schema exactly. This eliminates argument parsing errors in production.

Demo 2: UI Is Not Your Agent

Demo 2 runs the exact same agent as Demo 1 but surfaces it in a Tkinter desktop window. The point is pedagogical: your agent definition, conversation management, and tool-calling logic are entirely independent of your UI layer. Swapping from terminal to desktop requires changing only the presentation code — nothing in the agent or conversation path changes.

This is a principle worth internalising early: agent logic and UI logic should never be entangled. The lab enforces this separation structurally.

Demo 3: Server-Side Built-In Tools

The web search demo introduces a sharp contrast with Demo 1. With WebSearchTool , the tool-calling loop disappears entirely from client code:

The agent decides when to search, executes the search server-side, and returns a grounded response with citations. Your client code looks identical to Demo 0 — a simple responses.create() call with no tool loop.

The distinction matters architecturally:

Function tools (Demo 1) — tool execution happens on your client; you control the code, the API call, the error handling.

Built-in tools (Demo 3+) — tool execution happens inside Foundry; you get results without managing execution.

Demo 4: Code Interpreter and the Gradio Web UI

Demo 4 attaches CodeInterpreterTool , which gives the agent a sandboxed Python execution environment inside Foundry. The agent can write code, run it, observe output, and iterate — all server-side. Combined with a Gradio web interface, this demo shows an agent that can perform data analysis, generate charts, and explain results through a browser UI.

Model Router is particularly interesting here: the empirical data shows it selects a more capable frontier model ( gpt-5.4-2026-03-05 ) for code-generation tasks, while simpler conversational turns stay on lighter models.

Demo 5: Retrieval-Augmented Generation with FileSearchTool

Demo 5 introduces RAG. The setup phase uploads a document, creates a vector store, and attaches it to the agent:

At query time, the agent embeds the question, searches the vector store semantically, retrieves matching chunks, and generates an answer grounded in the retrieved content — entirely server-side. The client code remains a plain responses.create() call.

An important detail: the .vector_store_id file is written to disk during setup and read back during the chat session, so the demo survives process restarts without re-uploading the document. The .gitignore excludes this file from source control.

Demo 6: Model Context Protocol

Demo 6 connects the agent to a GitHub MCP server, giving it access to repository and issue data via the open Model Context Protocol standard. MCP servers expose tools over a standardised wire protocol; the agent discovers and calls them without any client-side function declarations.

The demo also demonstrates human-in-the-loop approval: before executing any MCP tool call, the agent surfaces the proposed action and waits for the user to confirm. This is an important safety pattern for agents that can trigger side effects on external systems.

Demo 7: Toolbox — Centralised Tool Governance

Where Demo 6 connects to a single MCP server directly, Demo 7 uses a Toolbox — a managed Microsoft Foundry resource that bundles multiple tools into a single, versioned, MCP-compatible endpoint. The Toolbox in this demo exposes both GitHub Issues and GitHub Repos tools, curated into an immutable versioned snapshot.

This pattern is significant for production multi-agent systems:

Centralised governance — one team owns the tool definitions; all agents consume them via a single endpoint.

Versioned snapshots — promoting a new Toolbox version is explicit; agents pin to a version and upgrade intentionally.

MCP compatibility — any MCP-capable agent or framework can connect, not just Foundry SDK agents.

Demo 8: Self-Hosted Agent with the Responses Protocol

The final demo departs from the prompt-agent pattern. Instead of registering a declarative agent in Foundry, Demo 8 implements a custom agent server using the Responses protocol . The server exposes a streaming HTTP endpoint; Foundry's Agent Inspector can connect to it and route user turns to it just as it would to a hosted prompt agent.

This demo includes a Dockerfile and an agent.yaml , enabling deployment to Foundry's container hosting service. It uses gpt-4.1-mini directly rather than the model router, because the custom server owns the entire inference path.

When to consider this pattern:

Your agent requires custom pre- or post-processing logic that cannot be expressed in a system prompt.

You need to integrate with infrastructure that is not reachable through MCP or built-in tools.

You want to own the inference call for cost control, A/B testing, or compliance reasons.

You are building a multi-agent orchestrator that needs to expose itself as an agent to other orchestrators.

The lab requires Python 3.10 or higher, an Azure subscription with a Microsoft Foundry project, and the Azure CLI.

1. Clone and set up the virtual environment

Your PROJECT_ENDPOINT is on the Overview page of your Foundry project in the Azure portal. It takes the form https://your-resource.ai.azure.com/api/projects/your-project .

Each numbered batch file at the root activates the virtual environment, runs create_agent.py , and launches chat.py . Append log to capture the full session transcript:

Every demo includes a reset.bat that deletes the registered agent and any associated resources (vector stores, uploaded files). Demos are fully repeatable.

Architecture Principles Demonstrated

Across the nine demos, the lab illustrates a set of design principles that apply directly to production agent systems:

Keyless authentication throughout

Every demo uses DefaultAzureCredential . No API keys appear anywhere in the code. Locally, az login provides credentials. In production, managed identity takes over automatically — same code, no secrets to rotate.

Server-side conversation state

The Responses API stores conversation history server-side. Your application passes a conversation ID; Foundry maintains the thread. This eliminates the common bug of truncating history due to local list management and makes multi-process or multi-instance deployments straightforward.

Client-side vs server-side tool execution

The lab makes the distinction explicit. Function tools execute in your process — you control the code, the external call, and the error handling. Built-in tools (WebSearch, CodeInterpreter, FileSearch) execute inside Foundry — you get results without managing execution infrastructure. MCP tools (Demo 6, 7) fall between these: they execute in a separately deployed server, with the protocol mediating the call.

Progressive tool introduction

Each demo's create_agent.py registers the agent once. The chat.py file handles the conversation loop. These two responsibilities are always separate, making it easy to update agent definitions without modifying conversation logic, and vice versa.

Security Considerations

When building agents for production, keep the following in mind:

Never commit .env files. The .gitignore excludes them, but verify this before pushing. Use Azure Key Vault or environment variable injection in CI/CD pipelines.

Use managed identity in production. DefaultAzureCredential automatically picks up managed identity when deployed to Azure, eliminating the need for any stored credentials.

Apply human-in-the-loop for side-effecting tools. Demo 6 demonstrates this pattern for MCP tool calls. Any agent that can modify external state (create issues, send emails, write files) should surface proposed actions for confirmation.

Validate tool outputs before use. Treat data returned by external tools (weather APIs, search results, document retrieval) as untrusted input. Prompt injection through tool results is a real attack surface; grounding instructions in your system prompt reduce but do not eliminate this risk.

Scope Toolbox permissions narrowly. When using a Toolbox (Demo 7), use allowed_tools to restrict which tools the agent can call, rather than granting access to all tools in a Toolbox version.

Start with the minimum. A prompt agent with no tools requires fewer than 30 lines of code using the Foundry SDK. Add tools only when the use case demands them.

Use model-router unless you have a specific reason not to. The empirical data in the lab shows the router selects appropriate models across all task types — factual, creative, tool-calling, RAG, and code generation.

Understand the client/server tool boundary. Function tools give you control; built-in tools give you simplicity. MCP and Toolbox give you governance and interoperability. Choose based on where you need control and where you need scale.

Conversation state belongs on the server. Do not maintain conversation history in application memory if you can avoid it. The Responses API conversation object is designed for this.

The hosted-demo pattern is for when you need to own the inference path. For most use cases, a declarative prompt agent is sufficient and far simpler to operate.

Explore the repo: github.com/microsoft-foundry/Foundry-Agent-Lab

Microsoft Foundry SDK documentation: learn.microsoft.com/azure/ai-studio/

Responses API quickstart: Prompt agent quickstart

Model Router conceptual documentation: Model Router for Microsoft Foundry

Model Context Protocol: modelcontextprotocol.io

Azure Identity SDK (DefaultAzureCredential): azure-identity Python SDK

The Foundry Agent Lab is open source under the MIT licence. Contributions, bug reports, and feature requests are welcome through GitHub Issues . See CONTRIBUTING.md for guidelines.

Surface Laptop Studio 2

Copilot for organizations

Copilot for personal use

Explore Microsoft products

Microsoft Store support

Certified Refurbished

Microsoft Store Promise

Microsoft in education

Devices for education

Microsoft Teams for Education

Microsoft 365 Education

How to buy for your school

Educator training and development

Deals for students and parents

Microsoft Power Platform

Microsoft 365 Copilot

Support for AI marketplace apps

Microsoft Tech Community

Microsoft Marketplace

Privacy at Microsoft

Diversity and inclusion