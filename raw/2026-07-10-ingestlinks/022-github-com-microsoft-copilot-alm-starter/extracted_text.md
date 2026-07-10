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

microsoft/copilot-alm-starter

Repository files navigation

A lightweight ALM toolkit for Copilot Studio agents – CI/CD pipelines, best practices, and deployment guidance for both GitHub Actions and Azure DevOps Pipelines .

This repository provides everything you need to implement Application Lifecycle Management (ALM) for your Power Platform solutions, with a focus on Copilot Studio agents. It includes:

🚀 CI/CD pipelines for export, build, and deployment (GitHub Actions and Azure DevOps)

📁 Recommended folder structure for organizing solutions

📖 Step-by-step guides for common scenarios

🔧 Reusable scripts for automation (work across both platforms)

Use this template – Click "Use this template" (GitHub) or import to your Azure DevOps project

Pick your CI/CD platform – Use the workflows in .github/workflows/ or .pipelines/

Configure authentication – Set up credentials for your Power Platform environments (see Authentication Setup )

Export your solution – Run the export pipeline to pull your agent from the dev environment

Deploy – Push to main to trigger deployment to downstream environments

💡 New to ALM for Power Platform? Start with the Getting Started Guide .

Repository Structure

Azure DevOps Pipelines

See Azure DevOps Setup for detailed configuration instructions.

Power Platform environment(s) with Copilot Studio

Service Principal / App Registration with appropriate permissions

GitHub repository (this template) or Azure DevOps project with Repos + Pipelines

Option A: GitHub Actions (Workload Identity Federation)

We recommend using federated credentials (no secrets to manage):

Create an App Registration

Add federated credentials for GitHub Actions

Configure as Application User in Power Platform

Add variables to GitHub

See Authentication Setup for detailed instructions.

Option B: Azure DevOps (Workload Identity Federation)

Use Workload Identity Federation (WIF) service connections in Azure DevOps (recommended) – no secrets to manage:

Create an App Registration

Create WIF Service Connections in your Azure DevOps project

Configure as Application User in Power Platform

Update .pipelines/environment-variables.yml

See Azure DevOps Setup for detailed instructions.

Configure directly in the targetEnvironments parameter:

Contributions are welcome! Please read our Contributing Guide before submitting a PR.

This project is licensed under the MIT License – see the LICENSE file for details.

A lightweight ALM toolkit for Copilot Studio agents – GitHub Actions workflows, best practices, and deployment guidance

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information