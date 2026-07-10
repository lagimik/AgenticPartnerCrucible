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

microsoft/work-iq-samples

Repository files navigation

Sample clients for the Work IQ API — Microsoft's AI-native interface to Microsoft 365 work intelligence.

All samples target the Work IQ Gateway ( workiq.svc.cloud.microsoft ) — the dedicated entry point for Work IQ. Token audience: api://workiq.svc.cloud.microsoft ; delegated scope: WorkIQAgent.Ask .

Before you run — three prerequisites

Microsoft 365 Copilot license on the test user (license propagation can take 15–30 minutes after assignment).

Entra app registration configured in your tenant — this is a one-time setup per tenant. Details below.

Your language toolchain : dotnet/ samples: .NET 8.0 SDK or later rust/ samples: Rust toolchain (stable) swift/ samples: Xcode 26+ (macOS only)

dotnet/ samples: .NET 8.0 SDK or later

rust/ samples: Rust toolchain (stable)

swift/ samples: Xcode 26+ (macOS only)

App registration setup

You (or your tenant admin) must create an Entra app registration with specific permissions, redirect URIs, and consent. This is a ~5-minute task.

If you're the admin — from the repo root: # Bash / WSL / macOS / Linux scripts/admin-setup.sh # PowerShell scripts\admin - setup.ps1 See ADMIN_SETUP.md for all flags and the manual CLI / portal paths.

If you're the admin — from the repo root:

See ADMIN_SETUP.md for all flags and the manual CLI / portal paths.

If you're not the admin — hand ADMIN_SETUP.md to them. They'll give you back an App ID and Tenant ID .

If you're not the admin — hand ADMIN_SETUP.md to them. They'll give you back an App ID and Tenant ID .

After setup you'll have two values: APP_ID and TENANT_ID . Pass them to any sample via --appid and --tenant .

Authentication methods

All samples support multiple authentication methods. Choose the one that fits your platform.

WAM (Windows Account Manager) — Windows only, .NET samples

Uses the Windows broker for silent SSO. A browser-less sign-in popup appears on first use; subsequent calls in the same process are silent. Across dotnet run invocations you'll be re-prompted (the samples don't persist MSAL state across processes by default).

Note: WAM is only available on Windows. On macOS and Linux, MSAL falls back to an interactive browser sign-in using the http://localhost redirect URI — same command works.

MSAL flows — Rust, Swift

The Rust CLI tries silent → broker (macOS Enterprise SSO / Windows WAM) → browser PKCE → device code, in that order. The Swift app uses MSAL silent + interactive (system browser) on iOS.

Pre-obtained JWT token — all platforms, all samples

Acquire a token externally (e.g. via your own MSAL code) and pass it directly:

A2A protocol specification

MSAL.NET documentation

ADMIN_SETUP.md — detailed admin setup guide

scripts/admin-setup.sh / scripts/admin-setup.ps1 — unified app-registration scripts

Provides samples for use with the work-iq apis

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information