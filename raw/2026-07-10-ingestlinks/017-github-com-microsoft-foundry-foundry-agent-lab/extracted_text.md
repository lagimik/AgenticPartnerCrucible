Platform AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start EXPLORE Why GitHub Documentation Blog Changelog Marketplace View all features

AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools

GitHub Copilot Write better code with AI

GitHub Copilot app Direct agents from issue to merge

MCP Registry New Integrate external tools

DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes

Actions Automate any workflow

Codespaces Instant dev environments

Issues Plan and track work

Code Review Manage code changes

APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start

GitHub Advanced Security Find and fix vulnerabilities

Code security Secure your code as you build

Secret protection Stop leaks before they start

EXPLORE Why GitHub Documentation Blog Changelog Marketplace

Solutions BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries View all solutions

BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits

Small and medium teams

BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases

BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries

Resources EXPLORE BY TOPIC AI Software Development DevOps Security View all topics EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners View all resources

EXPLORE BY TOPIC AI Software Development DevOps Security View all topics

Software Development

EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills

SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners

Open Source COMMUNITY GitHub Sponsors Fund open source developers PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program REPOSITORIES Topics Trending Collections

COMMUNITY GitHub Sponsors Fund open source developers

GitHub Sponsors Fund open source developers

PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program

Maintainer Community

REPOSITORIES Topics Trending Collections

Enterprise ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform

Enterprise platform AI-powered developer platform

AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

GitHub Advanced Security Enterprise-grade security features

Copilot for Business Enterprise-grade AI features

Premium Support Enterprise-grade 24/7 support

Search code, repositories, users, issues, pull requests...

We read every piece of feedback, and take your input very seriously.

Use saved searches to filter your results more quickly

To see all available qualifiers, see our documentation .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Notifications You must be signed in to change notification settings

Security and quality 0

Security and quality

microsoft-foundry/Foundry-Agent-Lab

Repository files navigation

Microsoft Foundry Agent Demos

A progressive series of demos showing how to build AI agents with the Microsoft Foundry SDK . Each demo builds on the previous one, adding one new concept at a time.

Model Router — One Model to Rule Them All

All agents in this repo use model-router as their model deployment. No model pinning, no per-agent model selection, no routing logic in your code:

Model Router is a Microsoft Foundry capability that intelligently routes each request to the optimal model in real time — balancing quality, latency, and cost. A simple greeting might be handled by a lightweight model, while a complex tool-calling chain gets routed to a frontier model. You get the best of all available models without deploying or managing any of them individually.

Key benefits observed across these demos:

Zero model selection overhead — no need to evaluate which model fits each agent

Significant cost efficiency — simple queries use cheaper models; expensive models only fire when needed

Automatic quality routing — tool-calling, RAG, code generation, and conversational tasks each get the right model

Future-proof — as new models become available, the router picks them up without code changes

For a deep-dive analysis showing which models the router selected for each demo (and why), see MODEL-ROUTER.md .

Progressive complexity — each demo adds exactly one new concept, building on the previous ones

One-command launch — numbered .bat files at the root run everything end-to-end (venv activation, agent creation, chat)

Per-demo configuration — each demo has its own .env file with sensible defaults; change one demo without affecting others

Session logging — append log to any launch command to capture the full session (input + output) to chat-log.txt for slides and documentation

GUI and web logging — desktop (Tkinter) and web (Gradio) demos also log conversations, not just terminal demos

Three UX modes — terminal, desktop, and web interfaces show that the same agent works with any presentation layer

Built-in vs function tools — demos contrast client-side tool execution (Demo 1) with server-side built-in tools (Demos 3–5), open-standard MCP tools (Demo 6), and centralized toolbox governance (Demo 7)

Clean reset — every demo includes a reset.bat to delete agents and resources, so demos are repeatable

Presenter guide — the root DEMO-GUIDE.md covers recommended demo order, time-budget combos, recovery tips, and key messages to land

Demo scripts — every folder includes a DEMO-SCRIPT.md with step-by-step talking points and suggested prompts, so presenters can walk through each demo confidently

Self-contained documentation — each demo folder has its own README, HOW-IT-WORKS, and DEMO-SCRIPT

Shared dependencies — one requirements.txt and one .venv at the root; no per-demo install steps

Python 3.10+ with a virtual environment

Azure subscription with a Microsoft Foundry project

Azure CLI ( az login for authentication)

1. Clone the repository

2. Create a Python virtual environment

A virtual environment isolates this project's dependencies from your global Python installation.

Windows (Command Prompt or PowerShell):

Tip: Verify your Python version first with python --version . Python 3.10 or higher is required.

3. Activate the virtual environment

You must activate the venv before installing packages or running any demo.

Your prompt will show (.venv) when the environment is active.

PowerShell note: If you see an execution policy error, run Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned once, then retry.

4. Install dependencies

All demos share this single install — no per-demo setup required.

5. Configure each demo

In each demo folder you plan to run, copy .env.sample to .env and fill in your Microsoft Foundry project endpoint:

Then edit .env with your values:

Find your PROJECT_ENDPOINT on the Overview page of your Foundry project in the Azure portal.

Deactivating the virtual environment

When you are done, deactivate with:

Each numbered .bat file activates the venv and runs the demo end-to-end.

To capture the full console session to a text file (for slides/docs):

This creates hello-demo\chat-log.txt with the complete session transcript including your input and the agent's responses.

Each demo has its own .env file with three variables:

Each demo folder includes a reset.bat that deletes the agent (and any associated resources like vector stores). Use it if a demo crashes mid-run or you want a clean slate:

All demos share one requirements.txt :

azure-ai-projects — Agent creation and management

azure-identity — Azure authentication

python-dotenv — Environment variable loading

requests — HTTP calls (weather API in Demo 1)

gradio — Web UI (Demo 4 only)

azure-ai-agentserver-responses — Hosted agent server (Demo 8 only)

Contributions are welcome! Please read CONTRIBUTING.md for guidelines on how to submit pull requests, report issues, and follow the Microsoft Open Source Code of Conduct.

This repo uses DefaultAzureCredential — no API keys in code. Never commit .env files. To report a security vulnerability, see SECURITY.md .

This project is licensed under the MIT License .

Copyright (c) 2026 Microsoft Corporation.

Ready-to-use structured and progressively complex agent demos with demo scripts and How-it works.

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information