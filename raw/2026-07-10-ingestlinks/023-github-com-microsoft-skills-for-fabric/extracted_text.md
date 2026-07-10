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

microsoft/skills-for-fabric

Repository files navigation

Microsoft Fabric Skills

Microsoft Fabric Skills are reusable AI assistant instructions for working with Microsoft Fabric. They help GitHub Copilot CLI and compatible AI coding tools understand Fabric workloads, APIs, query patterns, and operational best practices.

Install with GitHub Copilot CLI

Add the public marketplace:

Install the full bundle (except powerbi-authoring ):

Or install a focused bundle:

You can also filter the full bundle by workload:

The full bundle includes skills for SQL data warehouse, Spark and Lakehouse, Power BI semantic models, Eventhouse and KQL, Eventstreams, Dataflows Gen2, catalog search, migration scenarios, and medallion architecture workflows.

See CHANGELOG.md for public release notes.

Try an example prompt

Analytics PDF report

Document my workspace

NYC Taxi medallion architecture

After installing a bundle, open Copilot CLI in a project folder and ask for the Fabric task you want to perform, for example:

Most Fabric operations require Azure authentication. Start with:

SQL, Spark, Power BI, and KQL workflows may require workload-specific endpoints or token audiences. The installed skills provide the detailed commands and API patterns for each workload.

Skills provide guidance and patterns. MCP servers provide live tool access to data sources and APIs. Some bundles include MCP configuration where supported, and you can register additional Fabric MCP servers if your environment provides them.

Other AI coding tools

GitHub Copilot CLI plugin installation is the recommended path. This repository also includes root-level configuration files for compatible AI coding tools — CLAUDE.md for Claude Code, .cursorrules for Cursor, .windsurfrules for Windsurf, and AGENTS.md for Codex / Jules / OpenCode. They are picked up automatically when the repo is cloned.

Gemini CLI also auto-discovers GEMINI.md when the repo is cloned.

Report product issues in the GitHub issue tracker .

For security vulnerabilities, do not open a public issue. See SECURITY.md for the private reporting path.

This project is licensed under the MIT License .

A collection of skills and MCP systems to enable users of CLI, VSCode, Claude to operate over Microsoft Fabric

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information