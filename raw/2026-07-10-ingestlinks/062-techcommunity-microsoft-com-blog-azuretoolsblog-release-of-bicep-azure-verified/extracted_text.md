Microsoft Community Hub

Communities Products

Release of Bicep Azure Verified Modules for Platform Landing Zone

After months of collaboration and invaluable community feedback, we're thrilled to announce that Azure Verified Modules for Platform Landing Zone using Bicep is now generally available!

This release represents a significant milestone in the evolution of Azure Landing Zones. Bicep customers can now leverage the same modular, flexible, and battle-tested approach that our Terraform community has been using, all built on the foundation of Azure Verified Modules.

Why Azure Verified Modules?

Azure Verified Modules (AVM) represent Microsoft's unified approach to Infrastructure as Code. Born from the need to eliminate fragmentation across Microsoft's infrastructure-as-code (IaC) ecosystem, AVM provides consistent module standards, rigorous testing frameworks, and clear contribution guidelines.

The ALZ Bicep implementation now leverages AVM exclusively. Every resource you deploy uses verified resource or pattern modules from the AVM registry . This means you're building on modules that follow consistent engineering practices and are backed by official Microsoft support.

Based on your feedback, we've completely refactored the framework into a truly modular architecture, giving you the flexibility to compose your Platform Landing Zone exactly the way you need it.

New to Azure Verified Modules?

Azure Verified Modules is Microsoft's "One Microsoft" approach to IaC modules. It consolidates previously fragmented efforts across the organization into a single, unified library with consistent standards, testing, and support.

Explore the full catalog at azure.github.io/Azure-Verified-Modules .

What's New with this Framework?

Complete Customization

You asked for full control over every aspect of your deployment. We listened.

Every component is now customizable , from management group hierarchies to individual resource names and configurations.

The Bicep AVM starter module composed of 19 separate Azure Verified Modules : 16 resource modules and 3 pattern modules. Each module is independently versioned, tested, and maintained.

Here's how they work together:

The move to AVM delivers tangible benefits:

End-to-end customization: Configure every aspect of your Platform Landing Zone without limitations

Name everything your way: Apply your naming conventions to all resources and management groups

Flexible hierarchy: Restructure management groups with minimal effort as your organization evolves

Minimal hardcoded values: Just about every property is now configurable

Faster innovation: Multiple module owners means features and fixes arrive faster than ever

Azure Deployment Stacks

We've integrated Azure Deployment Stacks and it's a game changer for lifecycle management for Bicep.

Deployment Stacks track the resources that should exist based on your templates and automatically clean up anything that's no longer defined. It's somewhat similar to Terraform's state management, but native to Azure and built into the platform so you don't have to manage a state file.

Modern Parameter Files

We've upgraded from JSON to .bicepparam files , a breath of fresh air for developer experience:

IntelliSense support: Real-time autocomplete and validation in VS Code

Function support: Use Bicep functions directly (no more workarounds!)

Variables: Define once, reuse everywhere

Comments: Document your configuration inline for better team collaboration

Deployment with the ALZ Accelerator

The Azure Landing Zones IaC Accelerator remains your fastest path to a production-ready Platform Landing Zone.

Bicep AVM is now the default starter module and the focus of all future development. It implements enterprise best practices out of the box for both Azure Pipelines and GitHub Actions.

Previously, customization was limited to a handful of parameters like location and network_type . Those days are over.

The new platform-landing-zone.yaml configuration file gives you quite a bit more control (and more is planned in the near term):

Management group structure: Customize the entire hierarchy with your naming and organization

Resource naming: Apply consistent naming patterns across all resource groups

Network architecture: Choose between Hub & Spoke ( hubNetworking ), Virtual WAN ( vwanConnectivity ), or no networking ( none )

Azure regions: Deploy to any combination of regions for your requirements

We plan to add more specific options that can be overridden prior to bootstrapping as well. Comment below if you think anything in particular should be provided – maybe whether or not DDoS should be enabled... 😁

Independent Policy Management with the ALZ Library

Like the Terraform implementation, Bicep AVM now leverages the Azure Landing Zones Library.

The key innovation? Decoupled update cycles. The Library separates policy data from deployment logic, which means:

Update the module to get bug fixes without touching policies

Refresh policies to the latest ALZ Library version without updating other components

No more forced coupling between infrastructure changes and policy updates

The ALZ Bicep specific Library documentation provides full details. Our vision is to make this the single source of truth for policies across all ALZ implementations: Portal, Terraform, and Bicep.

We've heard your frustrations about "upgrade hell" when customizing policies in classic ALZ-Bicep. The new approach aims to solve or at least improve considerably:

Direct library integration: Leverage the ALZ library directly in your deployments

Clean separation: Your custom policies stay separate from ALZ defaults

Built-in customization: Each management group module includes dedicated properties for your custom policies

Update ALZ defaults independently from your custom policies without merge conflicts or upgrade headaches.

The Future of ALZ-Bicep Classic

With Bicep AVM now generally available and set as the default in the ALZ Accelerator for Bicep, we're beginning the deprecation process for classic ALZ-Bicep.

Currently, ALZ-Bicep is still supported in the Accelerator as "Bicep Classic - Complete" ( documentation ), but this will be removed in entirety on February 16th, 2026 .

Although it will be removed from the Accelerator, the ALZ-Bicep repository will still be supported in terms of:

...for a period of 12 months after that date. After February 16th, 2027, the ALZ-Bicep repository will be archived and no longer supported.

A comprehensive migration guide is coming soon to help you transition from classic ALZ-Bicep to Bicep AVM. We'll provide step-by-step instructions and tooling to make the process as smooth as possible. Stay tuned!

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