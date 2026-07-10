Microsoft Community Hub

Communities Products

Microsoft Foundry Blog

Tracking Every Token: Granular Cost and Usage Metrics for Microsoft Foundry Agents

As organizations scale their use of AI agents, one question keeps surfacing: how much is each agent actually costing us? Not at the subscription level. Not at the resource group level. Per agent, per model, per request.

This post walks through a solution that answers that question by combining three Azure services Microsoft AI Foundry, Azure API Management (APIM), and Application Insights into an observable, metered AI gateway with granular token-level telemetry including custom dates greater than a month for deeper analysis.

Foundry’s built-in monitoring and cost views are ultimately powered by telemetry stored in Application Insights, and the out-of-the-box dashboards don’t always provide the exact per-request/per-caller token breakdown or the custom aggregations/joins teams may want for bespoke dashboards (for example, breaking down tokens by APIM subscription, product, tenant, user, route, or agent step). Using APIM to stamp consistent caller/context metadata (headers/claims), Foundry to generate the agent/model run telemetry, and App Insights as the queryable store to let you correlate gateway, agent run, tool/model calls and then build custom KQL-driven dashboards. With data captured in App Insights and custom KQL queries, questions such as below can be answered:

Which agent consumed the most tokens last week?

What's the average cost per request for a specific agent?

How do prompt tokens vs. completion tokens break down per model?

Is one agent disproportionately expensive compared to others?

This solution was built to close the observability gap between "we deployed agents" and "we understand what those agents cost." The goals were straightforward:

Per-agent, per-model cost attribution - Know exactly which agent is consuming what, down to the token.

Real-time telemetry, not batch reports - Metrics flow into Application Insights within minutes, query via KQL.

Zero agent modification - The agents themselves don't need to know about telemetry. The tracking happens at the gateway layer.

Extensibility - Any agent hosted in Microsoft Foundry and exposed through APIM can be added with a single function call.

The architecture is intentionally simple three services, one data flow. The notebook serves as a testing and prototyping environment, but the same `call_agent()` and `track_llm_usage()` code can be lifted directly into any production Python application that calls Foundry agents.

Azure API Management acts as the AI Gateway. Every request to a Foundry-hosted agent flows through APIM, which handles routing, rate limiting, authentication, and tracing. APIM adds its own trace headers (`Ocp-Apim-Trace-Location`) so you can correlate gateway-level diagnostics with your application telemetry. After the API request is successfully completed, we can extract the necessary data from response headers.

The notebook is designed for testing and rapid iteration call an agent, inspect the response, verify that telemetry lands in App Insights. It uses `httpx` to call agents through APIM, authenticating with `DefaultAzureCredential` and an APIM subscription key. After each response, it extracts the `usage` object `input_tokens`, `output_tokens`, `total_tokens` — and calculates an estimated cost based on built-in per-model pricing.

Application Insights receives this telemetry via OpenTelemetry. The solution sends data to two tables:

customMetrics - Cumulative counters for prompt tokens, completion tokens, total tokens, and cost in USD. These power dashboards and alerts.

traces - Structured log entries with `custom_dimensions` containing agent name, model, operation ID, token counts, and cost per request. These power ad-hoc KQL queries.

traces - stores your application’s trace/log messages (plus custom properties/measurements) as queryable records in Azure Monitor Logs.

This is where the solution shines. Once telemetry is flowing, you can answer detailed questions with simple KQL queries.

Query the `traces` table to see every individual agent call with full token and cost breakdown:

This gives you a line-item audit trail every request, every agent, every token.

Aggregated Metrics Per Agent

Summarize across all requests to see averages and totals grouped by agent and model:

Now you can see at a glance:

Which agent is the most expensive across all calls

Average token consumption per request useful for prompt optimization

Prompt-to-completion ratio a high ratio may indicate verbose system prompts that could be trimmed

Cost trends by model is GPT-4.1 worth the premium over GPT-4o-mini for a particular agent?

The same can be done in code with your custom solution:

Azure Workbooks - Build interactive dashboards showing cost trends over time, agent comparison charts, and token distribution heatmaps.

Alerts - Trigger notifications when a single agent exceeds a cost threshold or when token consumption spikes unexpectedly.

Azure Dashboard pinning - Pin KQL query results directly to a shared Azure Dashboard for team visibility.

Power BI integration - Export telemetry data for executive-level cost reporting across all AI agents.

The solution is designed to scale with your agent portfolio. Any agent hosted in Microsoft Foundry and exposed through APIM can be integrated without modifying the telemetry pipeline. Adding a new agent is a single function call:

Token tracking, cost estimation, and telemetry export happen automatically. No additional configuration, no new infrastructure.

The notebook is a testing harness, a fast way to validate agent connectivity, inspect raw responses, and confirm that telemetry arrives in App Insights. But the code isn't limited to notebooks.

The core functions `call_agent()`, `track_llm_usage()`, and the OpenTelemetry configuration are plain Python. They can be dropped directly into any production application that calls Foundry agents through APIM:

FastAPI / Flask web service - Wrap `call_agent()` in an endpoint and get per-request cost tracking out of the box.

Azure Functions - Call agents from a serverless function with the same telemetry pipeline.

Background workers or batch pipelines - Process multiple agent calls and aggregate cost data across runs.

CLI tools or scheduled jobs - Run agent evaluations on a schedule with automatic cost logging.

The pattern stays the same regardless of where the code runs:

Start with the notebook to prove the pattern works. Then move the same code into your production codebase, the telemetry travels with it.

AI cost observability matters. As agent counts grow, per-agent cost attribution becomes essential for budgeting and optimization.

APIM as an AI Gateway gives you routing, rate limiting, and tracing in one place without touching agent code.

OpenTelemetry + Application Insights provides a battle-tested telemetry pipeline that scales from a single notebook to production workloads.

KQL makes the data actionable. Per-request audits, per-agent summaries, and cost trending are all a query away.

The solution is additive, not invasive. Agents don't need modification. The telemetry layer wraps around them.

This approach gives developers the abiility to view metrics per user, API Key, Agent, request / tool call, or business dimensions(Cost Center, app, environment).

If you're running AI agents in Microsoft Foundry and want to understand what they cost at a granular level this pattern gives you the visibility to make informed decisions about model selection, prompt design, and budget allocation.

The full solution is available on GitHub: https://github.com/ccoellomsft/foundry-agents-apim-appinsights

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