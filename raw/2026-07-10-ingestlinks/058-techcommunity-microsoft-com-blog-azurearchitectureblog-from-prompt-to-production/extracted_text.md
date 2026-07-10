Microsoft Community Hub

Communities Products

Azure Architecture Blog

From Prompt to Production: Building Azure Architecture Diagrams with AI

Today I'm sharing the Azure Architecture Diagram Builder — an open-source, AI-powered web application that helps cloud architects design, validate, and deploy Azure solutions faster.

Author: Arturo Quiroga, Senior Partner Solutions Architect — Microsoft

Cloud architects spend significant time translating ideas into architecture diagrams. They toggle between Visio, draw.io, pricing calculators, and documentation. According to the 2024 Stack Overflow Developer Survey , 61% of developers spend more than 30 minutes a day searching for answers or solutions, time lost to context-switching rather than design. What if you could describe your architecture in plain English and get a diagram, cost estimate, and deployment guide in minutes?

The Challenge: Fragmented Architecture Workflows

Designing Azure architectures today typically involves multiple disconnected steps:

Sketch the architecture in a diagramming tool

Look up official Azure icons and drag them into place

Research pricing across regions using the Azure Pricing Calculator

Validate the design against the Well-Architected Framework (WAF)

Write deployment documentation and Infrastructure as Code templates

Compare alternative designs manually

Each step lives in a different tool, and keeping them in sync as designs evolve is costly. The Azure Architecture Diagram Builder brings these workflows together in a single browser-based experience.

Describe your architecture in natural language, for example "A HIPAA-compliant healthcare platform with FHIR APIs, event-driven processing, and multi-region disaster recovery" , and the AI generates a diagram with grouped services, data flow connections, and logical organization.

Figure 1. Enter a natural-language prompt describing your architecture. Curated example prompts help you get started, and you can optionally upload an existing diagram for the AI to analyze.

The tool uses Azure OpenAI to power generation across multiple models, enabling you to choose the model that best fits your scenario — from fast iterations to deeper reasoning.

AI-Powered Architecture Generation

Describe what you need in plain English, and the AI creates an architecture diagram with:

714 official Azure service icons across 29 categories

Smart grouping : services are logically organized (Frontend, Backend, Data, Security)

Data flow connections : labeled edges showing how data moves through the system

13 curated example prompts : from simple web apps to complex enterprise scenarios like Zero Trust networks, Industrial IoT with 5,000+ sensors, and global multiplayer gaming backends

Figure 2. A generated industrial IoT architecture. Top: the clean diagram view as initially produced. Bottom: the same diagram with per-service monthly cost overlays toggled on, plus a running subscription total in the toolbar.

Architecture Image Import

Already have an architecture on a whiteboard or in a screenshot? Upload the image and let the AI analyze it, mapping services to official Azure icons and recreating the architecture as an editable, interactive diagram.

Figure 3. Upload a photo of a whiteboard sketch (top-right reference panel) and the AI recreates it as an editable diagram with official Azure service icons and labeled data flow connections.

Import existing ARM templates to visualize your current infrastructure. The AI parses resource definitions and dependencies, groups related resources into logical layers, and produces a meaningful diagram of what you actually have deployed — a fast way to document an inherited environment or sanity-check a template before deployment.

Figure 4. ARM template import in action. Top: the parser status banner while resources and dependencies are being analyzed. Bottom: the resulting diagram, with resources auto-grouped into logical layers (Web Tier, Data Layer, Container Platform, Observability & Logging) and a Generated from: ARM Template badge linking the diagram back to its source file.

Well-Architected Framework Validation

Validate your architecture against all five WAF pillars — Security, Reliability, Performance Efficiency, Cost Optimization, and Operational Excellence. The validator provides:

An overall WAF score with pillar-level breakdowns

Specific findings with severity levels

Actionable recommendations you can select and apply

Select the recommendations you agree with, and the AI regenerates an improved architecture incorporating those changes.

Figure 5. WAF validation results showing the overall score, per-pillar breakdowns, and individual findings with severity badges. Tick the recommendations you want and the AI rebuilds the diagram with those changes applied.

Multi-Model Comparison

Run the same architecture prompt through multiple AI models side-by-side and compare:

Architecture Comparison : service counts, connection counts, groups, token usage, and latency

Validation Comparison : WAF scores across models, severity breakdowns, and finding counts

Apply Winner : pick the best result and apply it to the canvas with one click

Present Critique : a talking avatar narrates the AI-generated ranking with live closed captions

Figure 6. Multi-model comparison. Top: select the models and reasoning effort, then enter the prompt. Bottom: side-by-side results across all selected models with service counts, latency, token usage, and Fastest / Cheapest / Most Thorough badges.

Multi-Region Cost Estimation

Get cost estimates from the Azure Retail Prices API across 8 Azure regions : East US 2, Australia East, Canada Central, Brazil South, Mexico Central, West Europe, Sweden Central, and Southeast Asia. Features include:

Color-coded cost legend (green / yellow / red thresholds)

SKU and tier information for each service

Export options: CSV, JSON, plain-text summary, and an analysis report with top cost drivers, Reserved Instance flags, and a ranked multi-region comparison table

Figure 7. The cost legend overlay shows per-service pricing with color-coded thresholds. The region selector in the toolbar lets you re-price the entire architecture in any of eight Azure regions.

Deployment Guide Generation with Bicep

Generate step-by-step deployment documentation including:

Prerequisites and Azure resource requirements

Step-by-step deployment instructions

Bicep templates for each service (Infrastructure as Code)

Post-deployment verification steps

Security configuration recommendations

Figure 8. Each generated Deployment Guide opens with the architecture name, an estimated deployment time, and a prerequisites checklist covering subscription roles, CLI versions, Microsoft Entra ID permissions, and region requirements, followed by numbered, copy-ready deployment steps.

Figure 9. The Infrastructure as Code section produces a main.bicep orchestrator plus a per-service module (Log Analytics, Key Vault, Cosmos DB, SQL Database, Event Hubs, Azure Functions, and more). The Download All Templates button packages everything into a ready-to-deploy folder.

Workflow Animation & Avatar Presenter

Visualize how data flows through your architecture with step-by-step animations that highlight services on the canvas as each step plays. When the Azure Speech Service is configured, a photorealistic talking avatar can narrate the workflow or present model comparison results, with live word-by-word closed captions in a draggable, resizable panel.

Figure 10. A workflow step is highlighted on the canvas as the Avatar Presenter narrates that step. Live word-by-word closed captions appear in a draggable, resizable panel, useful for accessibility and stakeholder demos.

Figure 11. A single-slide PowerPoint export, available in dark or light theme, ready to drop straight into a stakeholder deck.

The Azure Architecture Diagram Builder unifies the architecture design lifecycle in a single tool:

End-to-end workflow : from natural-language description to deployable Bicep templates without tool switching

Official Azure icons : 714 icons across 29 categories, mapped directly from the Azure service catalog

Live pricing : queries the Azure Retail Prices API at design time rather than relying on static estimates

WAF-integrated validation : architectural best practices built into the design loop rather than applied after the fact

Multi-model flexibility : choose the AI model that best suits each task, with fast models for iteration and reasoning models for complex designs

Open source : the source code is available for customization and contribution

One-Command Deploy with Azure Developer CLI

The fastest way to get your own instance running is with azd :

azd up provisions the following via Bicep:

The Azure Architecture Diagram Builder is available now:

Live demo : https://aka.ms/diagram-builder

Source code : GitHub repository

Documentation : See the Getting Started Guide for detailed setup instructions

We welcome feedback and contributions. Use the GitHub Issues page to report bugs, suggest features, or share your experience.

Tags: artificial intelligence · application · apps & devops · well architected · infrastructure

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