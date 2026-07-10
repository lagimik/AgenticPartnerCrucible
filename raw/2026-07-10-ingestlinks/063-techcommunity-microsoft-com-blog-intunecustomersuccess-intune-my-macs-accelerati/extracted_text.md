Microsoft Community Hub

Communities Products

Intune Customer Success

Intune my Macs: Accelerating macOS proof of concepts with Microsoft Intune

By: Neil Johnson and Chris Kunze - Principal Product Managers | Microsoft Intune

Intune provides a broad and mature set of capabilities for managing macOS devices across security, compliance, applications, and user onboarding. Many customers, however, aren’t always aware of just how much functionality is available or how to bring it all together. We've developed a starter kit to make it easy to explore and set up macOS configurations in Intune: Intune my Macs. Intune my Macs helps bridge that gap by making it easy to explore some recommended macOS configurations and quickly set up a successful proof of concept using Intune.

What is Intune my Macs ?

Intune my Macs is an open-source project from the Microsoft Intune Customer Experience Engineering team that allows you to deploy a complete macOS proof of concept in minutes. This starter kit brings together over 31 enterprise-grade configurations - identified by Apple’s Mac Evaluation Utility - along with policies, scripts, and applications, all of which can be deployed using a single PowerShell script.

The project operates in dry-run mode by default, letting you preview exactly what will be created before committing any changes to your Intune tenant. When you're ready, simply add the --apply flag to the command-line to commit changes.

Important : From a support perspective, Microsoft fully supports Intune and its ability to deploy PowerShell scripts. However, Microsoft does not support the scripts themselves, even if they are on our GitHub repository. They’re provided for example only. You are responsible for anything that they may do within your environment. Always test!

Want a quick walkthrough before you dive in? Watch the video below to see a deep-dive on Intune my Macs - from authentication to policy creation, app deployment, and beyond.

Why would you use it ?

Instead of building macOS configurations from scratch, Intune my Macs provides a ready-to-use baseline of production quality Intune artifacts. These configurations are designed to help you quickly evaluate Microsoft Intune for macOS management while also serving as reference implementations you can adapt to your environment.

Below is an overview of what Intune my Macs deploys into your tenant, organized by category.

Example configurations

FileVault configuration, firewall enablement, Gatekeeper policies, Microsoft Edge policies

Minimum macOS version (15.0), SIP enforcement, encryption requirements

Platform SSO via Secure Enclave with Microsoft Entra ID

Intune Company Portal, Microsoft 365, Remote Help, Intune Log Watch, Microsoft 365 Copilot, Windows App, and Edge

Dock customization, FileVault key escrow (Escrow Buddy), onboarding automation

Hardware compatibility checks, Intune agent version reporting

Each configuration in the repository serves as a practical reference implementation. The naming conventions follow a consistent pattern (for example, pol-sec-001-filevault, scr-app-100-install-company-portal ), and detailed documentation explains what each setting does and why it's configured that way.

Tasks that typically require extensive research, configuration, and testing can now be completed in just about 5 minutes, thanks to this streamlined approach. The script handles:

Microsoft Graph SDK authentication

Policy creation via Intune settings catalog and custom configuration profiles

Script deployment with proper execution settings

PKG application uploads

Optional group assignments

Optional Microsoft Defender for Endpoint i ntegration

If you're evaluating Microsoft Defender for Endpoint on macOS, the project includes an optional --mde command-line flag that deploys the full Defender for Endpoint configuration, including system extensions, privacy preferences, network filter settings, and a script that can be used to install the client.

This starter kit is driven by XML manifest files that define each configuration artifact. The main PowerShell script reads these manifests, resolves the associated JSON/mobileconfig/script files, and creates the corresponding objects in Intune via the Microsoft Graph API.

You can scope this starter kit to specific artifact types using command-line flags like --apps , --config , --compliance , --scripts , or --custom-attributes . A custom naming prefix defined using the –prefix command-line flag) keeps your deployed objects easily identifiable, and the -- remove-all command-line flag provides a clean way, based on the custom naming prefix, to delete everything created by an earlier run.

For more information on how to use this project, be sure to review the prerequisites and instruction in the readme file.

Bonus: Utility t ools

The project also includes several analysis and documentation tools:

Export-MacOSConfigPolicies.ps1 - Back up existing Intune macOS policies to JSON

Find-DuplicatePayloadSettings.ps1 - Detect conflicting settings across all your Mac configuration files

Generate-ConfigurationDocumentation.py - Create Markdown or Word documentation from the manifests

Get-IntuneAgentProcessingOrder.ps1 - Understand script and app processing sequence

Get-MacOSGlobalAssignments.ps1 - List Mac policies assigned to All Devices or All Users

Intune my Macs isn't meant to be a one-size-fits-all production starter kit, but it’s a great way to get started. Use it to quickly implement a proof of concept, learn from the configuration patterns, and adapt the policies to your organization's specific requirements.

Whether you're evaluating Intune for macOS management, setting up a new tenant, or just looking for reference implementations of common security configurations, this project can save you significant time and effort.

Full Configuration Documentation

Microsoft Defender for Endpoint Setup

If you have any questions, leave a comment below or reach out to us on X @IntuneSuppTeam !

Post Updates 03/30/26: A video walkthrough has been added above. Watch to see Intune my Macs deploy a complete macOS proof of concept in minutes.

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