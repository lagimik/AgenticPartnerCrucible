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

Azure-Samples/claude

Repository files navigation

The Claude on Foundry Starter Kit

Short link: https://aka.ms/claude/start

Deploy Claude (haiku, sonnet, opus) on Microsoft Foundry in one command. Then call it from the Anthropic SDK and the Claude Code CLI over Microsoft Entra ID — no API keys.

Ships in both Bicep and Terraform . Works in the cloud (GitHub Codespaces) or on your laptop.

By running azd up you accept Anthropic's commercial terms for Claude. Three short attestation fields ( CLAUDE_ORGANIZATION_NAME , CLAUDE_COUNTRY_CODE , CLAUDE_INDUSTRY ) are sent to Anthropic with every request and must match your real organization. Read the Terms of use before you deploy.

The Terraform and Bicep in this template both send a modelProviderData block ( organizationName , countryCode , industry ) with each Claude deployment. The Cognitive Services RP uses that block to auto-sign the Azure Marketplace offer for Anthropic Claude on your behalf — no manual click-through. Before deploying, please:

Read the legal docs that govern your use of Claude via Microsoft Foundry: Anthropic Commercial Terms of Service — the master agreement for business / enterprise use (Foundry requires an Enterprise or MCA-E subscription). Anthropic Usage Policy (also called the Acceptable Use Policy / AUP) — incorporated by reference into the Commercial Terms and the doc Microsoft Foundry's own Responsible AI guidance points to. Anthropic Supported Regions Policy — also incorporated by reference; controls which regions are eligible. Microsoft Product Terms for Azure.

Read the legal docs that govern your use of Claude via Microsoft Foundry:

Anthropic Commercial Terms of Service — the master agreement for business / enterprise use (Foundry requires an Enterprise or MCA-E subscription).

Anthropic Usage Policy (also called the Acceptable Use Policy / AUP) — incorporated by reference into the Commercial Terms and the doc Microsoft Foundry's own Responsible AI guidance points to.

Anthropic Supported Regions Policy — also incorporated by reference; controls which regions are eligible.

Microsoft Product Terms for Azure.

Update the three attestation fields so they accurately describe your organization — see the highlighted rows in All configuration variables : CLAUDE_ORGANIZATION_NAME (no default — required) CLAUDE_COUNTRY_CODE (default US ) CLAUDE_INDUSTRY (default technology ) These values are sent to Anthropic on every request and are part of your acceptance — they should match the real legal entity, country of operation, and industry that will use the model.

Update the three attestation fields so they accurately describe your organization — see the highlighted rows in All configuration variables :

CLAUDE_ORGANIZATION_NAME (no default — required)

CLAUDE_COUNTRY_CODE (default US )

CLAUDE_INDUSTRY (default technology )

These values are sent to Anthropic on every request and are part of your acceptance — they should match the real legal entity, country of operation, and industry that will use the model.

Confirm your Azure subscription is eligible to deploy Anthropic models in Foundry .

Confirm your Azure subscription is eligible to deploy Anthropic models in Foundry .

The exact "Agree and proceed" dialog the Azure portal renders for a Claude SKU is generated live from the Marketplace offer metadata (Microsoft template + publisher-supplied links). It can change without notice, so this README does not snapshot its text — instead, open the live marketplace listing for the SKU you plan to deploy:

Sonnet 4.6 — https://azuremarketplace.microsoft.com/en-us/marketplace/apps/anthropic.anthropic-claude-sonnet-4-6-offer

Opus 4.6 — https://azuremarketplace.microsoft.com/en-us/marketplace/apps/anthropic.anthropic-claude-opus-4-6-offer

Haiku 4.5 — https://azuremarketplace.microsoft.com/en-us/marketplace/apps/anthropic.anthropic-claude-haiku-4-5-offer

All Anthropic offers — https://azuremarketplace.microsoft.com/en-us/marketplace/apps?search=anthropic

After azd up , you can audit the auto-signed marketplace agreement record from the CLI (returns metadata only — accepted , signature , signed-by, date, licenseTextLink — not the dialog text):

The main path is azd up on your laptop. Two collapsed alternatives below if you'd rather run in the browser or have an AI agent drive it for you.

An Azure subscription eligible to deploy Claude in Foundry , with Contributor on the target subscription/resource group (see Required permissions for the full breakdown, including the data-plane role you need to call the model).

Region: eastus2 or swedencentral host all three Claude families (haiku / sonnet / opus). westus2 is sonnet + opus only.

Tools: Azure CLI , azd , Python ≥ 3.10, and Terraform ≥ 1.6 (Terraform variant only).

Run az login once (in addition to azd auth login ). The preprovision hook uses az to validate that each requested Claude SKU exists in the Anthropic-on-Foundry catalog and that you have enough TPM quota in the chosen region. If az isn't installed or signed in, the hook warns and skips those checks so azd up still works — you just lose the proactive error messages.

That's it. To deploy other families, tweak capacity, or change attestation, see Choosing which models to deploy and All configuration variables in Advanced.

The fastest way to try this without installing anything locally — the included .devcontainer/devcontainer.json preinstalls az , azd , and Python 3.13 for you.

— click to launch (or use the green Code button on GitHub → Codespaces → Create codespace on main ). The container builds in ~2 min the first time.

— click to launch (or use the green Code button on GitHub → Codespaces → Create codespace on main ). The container builds in ~2 min the first time.

When the terminal is ready, sign in to Azure with device-code (the browser flow works inside a Codespace): az login --use-device-code azd auth login --use-device-code

When the terminal is ready, sign in to Azure with device-code (the browser flow works inside a Codespace):

Pick a variant and deploy: cd infra-bicep # or: cd infra-terraform azd env new my-claude azd env set CLAUDE_ORGANIZATION_NAME " Contoso " azd env set AZURE_LOCATION " swedencentral " azd env set CLAUDE_SONNET_MODEL " claude-sonnet-4-6 " azd up

Pick a variant and deploy:

When azd up finishes, jump to Use Claude below.

When azd up finishes, jump to Use Claude below.

Prefer the Dev Container on your laptop? Click the Dev Containers badge at the top of this README, or install the Dev Containers extension and run "Dev Containers: Reopen in Container" on the cloned repo. Requires Docker Desktop .

This repo ships an open Agent Skills playbook. Any assistant that reads AGENTS.md — GitHub Copilot Chat, Claude Code, OpenAI Codex, Cursor, Gemini CLI, Amp, Goose, and friends — onboards you in plain English and installs the tools it needs along the way.

Copy this into GitHub Copilot Chat (or your AI agent) inside the cloned repo:

Deploy Claude on Microsoft Foundry using this repo. Use Bicep , region eastus2 , model claude-sonnet-4-6 , organization name Contoso .

That's the full one-shot — just swap the bolded values to suit you. Optional additions:

"…also deploy haiku and opus " — multi-family deployment in one shot.

"…country GB , industry finance " — if your org isn't US tech (defaults are US / technology ).

"…with ASSIGN_RBAC=true " — also grant yourself the least-privilege inference role.

"…install Claude Code automatically" — sets CLAUDE_CODE_AUTO_INSTALL=true .

The agent then follows the playbook in skills/claude-on-foundry/SKILL.md and the always-on rules in AGENTS.md — using this repo's scripts, env-var contract, region matrix, and error catalog instead of guessing. It confirms with you before any destructive action.

Already cloned and in a workspace? Your agent picks the skill up automatically — just open the repo in your preferred assistant. GitHub Copilot reads .github/copilot-instructions.md natively; others follow AGENTS.md .

To add the skill to a different workspace:

More example prompts you can also try:

"Why is azd up failing with 715-123420 ?"

"Free up quota held by soft-deleted accounts in swedencentral ."

"Verify Claude Code is wired up to my Foundry deployment."

"Tear it all down cleanly."

The Python sample is the primary hello-world path. It calls your Foundry-hosted Claude deployment with Microsoft Entra ID — no API key.

We use the plain anthropic.Anthropic client. The Entra ID token is captured once at startup and is valid for ~1 hour — fine for a one-shot script or a short-lived process. For long-running processes, use the token-refresh shim below.

Pass the deployment name (not the model id) as model . The SDK appends /v1/messages to the configured base_url .

The plain anthropic.Anthropic client only accepts auth_token: str | None , so a captured token will start failing with 401 Unauthorized after ~1 hour.

For services, daemons, long batch jobs, or notebooks left open, use src/hello_claude_token_refresh.py . It defines a tiny AnthropicIdentity(Anthropic) subclass that overrides the auth_token property to call azure.identity.get_bearer_token_provider(...) per request, giving free per-request token refresh:

If the Anthropic SDK ever accepts a callable for auth_token , this shim becomes unnecessary.

After azd up finishes, the postprovision hook writes a project-scoped activator file. Source it once per shell:

If claude isn't installed, the postprovision hook printed the one-line installer command. Or set azd env set CLAUDE_CODE_AUTO_INSTALL true before azd up to install it automatically.

One command runs every config check plus a live claude -p round trip per deployed family:

Exits non-zero on any failure — safe to wire into CI. Use -SkipClaudeCall for config-only checks (no token cost), or -RunPythonSample to also run the Python Entra ID round trip. For the manual breakdown of what the script does, see Verify Claude Code is wired up — manual checks in Advanced.

Everything below is opt-in. The quickstart above is enough to get a working Claude deployment.

When you're done, free the resources and the TPM quota:

The --purge flag immediately releases the Foundry account from soft-delete; otherwise its TPM quota stays reserved for up to 48 h. If you didn't pass --purge and need to reclaim quota manually, see Free quota held by soft-deleted accounts .

Set one, two, or all three of CLAUDE_HAIKU_MODEL / CLAUDE_SONNET_MODEL / CLAUDE_OPUS_MODEL — each non-empty value deploys that family into the same Foundry account. The postprovision hook writes one ANTHROPIC_DEFAULT_<FAMILY>_MODEL env var per deployed family into the activator + .vscode/settings.json , so Claude Code can route across all three.

Override capacity per family with CLAUDE_HAIKU_CAPACITY / CLAUDE_SONNET_CAPACITY / CLAUDE_OPUS_CAPACITY (TPM ÷ 1000, default 25 each).

Run ./Get-ClaudeCatalog.ps1 to see the live catalog and pick model versions matching your region:

Rows marked Attest below are the three modelProviderData fields sent to Anthropic and used by the marketplace RP to auto-sign the Anthropic Commercial Terms (which incorporate the Usage Policy and Supported Regions Policy by reference) on your behalf — see the Terms of use above. Set them to match your real organization.

After azd up succeeds, the postprovision hook ( scripts/configure-claude-code.ps1 , with configure-claude-code.sh as a POSIX fallback) configures Claude Code for the freshly-deployed Foundry resource. It does four things:

Writes a project-scoped activator at the repo root ( claude-code.env.ps1 and claude-code.env.sh , both gitignored) containing the environment variables Claude Code expects: CLAUDE_CODE_USE_FOUNDRY=1 ANTHROPIC_FOUNDRY_RESOURCE=<your-foundry-account-name> One ANTHROPIC_DEFAULT_<FAMILY>_MODEL=<deployment-name> per deployed family ( HAIKU / SONNET / OPUS ). Only the families you actually deployed get a line. AZURE_CONFIG_DIR=<repo>/.azure-cli — scopes az login (and azd ) to this workspace only. See Workspace-scoped az login below.

CLAUDE_CODE_USE_FOUNDRY=1

ANTHROPIC_FOUNDRY_RESOURCE=<your-foundry-account-name>

One ANTHROPIC_DEFAULT_<FAMILY>_MODEL=<deployment-name> per deployed family ( HAIKU / SONNET / OPUS ). Only the families you actually deployed get a line.

AZURE_CONFIG_DIR=<repo>/.azure-cli — scopes az login (and azd ) to this workspace only. See Workspace-scoped az login below.

(Opt-in) Writes (or merges into) .vscode/settings.json with claudeCode.environmentVariables (the array-of- {name,value} schema the extension actually reads — the display name in the Settings UI is "Claude Code: Environment Variables" ) and claudeCode.disableLoginPrompt: true so the Claude Code VS Code extension skips the Anthropic-account login and uses your Foundry deployment via Entra ID. It also sets terminal.integrated.env.{windows,linux,osx}.AZURE_CONFIG_DIR so every terminal VS Code spawns in this workspace inherits the scoped Azure config automatically — you don't even have to source the activator first. This step only runs if you ask for it — the hook leaves .vscode/settings.json alone by default since most users run Claude from the SDK, the Claude Code CLI (which only needs the activator at step 1), or another OpenAI-compatible client. Using the Claude Code extension? Opt in before azd up with azd env set CLAUDE_WRITE_VSCODE_SETTINGS 1 (or pass -WriteVsCodeSettings / --write-vscode-settings when running the script standalone).

Writes (or merges into) .claude/settings.json at the repo root with { "model": "<family>" } pinned to a deployed family (sonnet > opus > haiku priority). This is the workspace-level Claude Code config and overrides whatever is in your user-global ~/.claude/settings.json — so bare claude / claude -p resolves to a family you actually deployed, even if your global default points elsewhere.

Checks whether claude is on PATH. If not, prints the platform-appropriate one-liner install command. Set CLAUDE_CODE_AUTO_INSTALL=true before azd up to run the official installer automatically.

Authentication uses Microsoft Entra ID through your existing az login session — no API keys to manage. If the Foundry resource lives in a non-default tenant, run az login --tenant <tenant-id> first so the token tenant matches the resource tenant .

To run Claude Code in a fresh shell at any time:

You can also re-run the hook standalone:

Both the activators and .vscode/settings.json set AZURE_CONFIG_DIR=<repo>/.azure-cli so that any az login (or azd auth login ) you do here writes its token cache and config to ./.azure-cli/ inside the repo — never to the global ~/.azure . The benefits:

Other VS Code windows / shells keep their own existing ~/.azure login (different tenant, different account — whatever) and are not affected.

Logging out ( az logout ) or rm -rf .azure-cli only nukes this workspace's credentials.

The directory is gitignored, so credentials never reach the repo.

VS Code applies the env var automatically to any terminal it opens inside this folder. If you launch a terminal outside VS Code, source the activator first ( . ./claude-code.env.ps1 or source ./claude-code.env.sh ) before running az login . Verify with az config get core — the config_path should point inside the repo.

Four ways to confirm the CLI is talking to your fresh Foundry deployment, easiest first.

0. One-command end-to-end check — runs every check in this section plus an SDK round trip in one shot:

The verify script checks the activator file, env vars, .vscode/settings.json shape, az login + tenant, claude on PATH (with -AutoInstall / --auto-install to install it if missing), then runs a non-interactive claude -p per deployed family. Exits non-zero on any hard failure so you can wire it into CI.

The rest of this section is the same checks broken out manually.

1. One-shot prompt (non-interactive) — fastest manual check:

You should see a one-line reply that identifies the deployed model (e.g. "I'm Claude Sonnet 4.6, built by Anthropic." ). macOS/Linux:

2. Interactive REPL — the normal way to use it:

Useful slash commands once inside:

3. VS Code extension — install once, picks up .vscode/settings.json automatically:

Then open the Command Palette → "Claude Code: Start" (or click the Claude icon in the activity bar). No extra config is needed — the postprovision hook already populated claudeCode.environmentVariables and claudeCode.disableLoginPrompt in .vscode/settings.json .

Still seeing a "Sign in to Claude" prompt? Reload the window (Command Palette → "Developer: Reload Window" ) so the extension re-reads .vscode/settings.json . If you used an older version of the hook that wrote a "Claude Code: Environment Variables" key, just re-run pwsh -File scripts/configure-claude-code.ps1 — it strips the stale key and writes the correct claudeCode.environmentVariables schema.

Auth error? If you see 401 / Token tenant doesn't match resource tenant , refresh your Azure login against the right tenant:

Multi-family support. Set any combination of CLAUDE_HAIKU_MODEL / CLAUDE_SONNET_MODEL / CLAUDE_OPUS_MODEL and the template deploys each family as a sibling deployment under the same Foundry account. The hook writes one ANTHROPIC_DEFAULT_<FAMILY>_MODEL per deployed family into the activator + .vscode/settings.json automatically. See Choosing which models to deploy .

If you don't have a data-plane role on the Foundry account yet, you can run a quick check with an API key. Prefer Entra ID for anything beyond local testing — keys can't be scoped per-user and rotate manually.

Microsoft Foundry account ( Microsoft.CognitiveServices/accounts , kind AIServices , SKU S0 , allowProjectManagement = true )

One Claude deployment per requested family ( GlobalStandard , with the required modelProviderData block) — set CLAUDE_HAIKU_MODEL / CLAUDE_SONNET_MODEL / CLAUDE_OPUS_MODEL to control which families. Sonnet/Opus deployments chain on the prior to avoid Foundry's per-account 409s on concurrent create.

Optional RBAC: a single Cognitive Services User assignment on the Foundry account for the deploying principal (set ASSIGN_RBAC=true ). This is the least-privilege role the MS Learn doc recommends for keyless inference — it grants exactly the Microsoft.CognitiveServices/accounts/MaaS/* data action this template's runtime needs and nothing else. If you want broader access (project-scoped APIs, agents, etc.), grant Foundry User or Azure AI Developer yourself afterwards — see the permissions matrix below. Heads up: without this (or a manual post-deploy grant), the Python SDK and claude CLI will return 401 PermissionDenied even though azd up succeeded. See Granting data-plane roles after azd up . When ASSIGN_RBAC=true , the model deployments are ordered to run after the role assignment. The role-assignment PUT returns fast (~5 s) but Foundry data-plane RBAC takes a few minutes to propagate; the slow model-deployment LRO (30 s–20 min) absorbs that propagation time so the first call after azd up succeeds without retries.

Heads up: without this (or a manual post-deploy grant), the Python SDK and claude CLI will return 401 PermissionDenied even though azd up succeeded. See Granting data-plane roles after azd up .

When ASSIGN_RBAC=true , the model deployments are ordered to run after the role assignment. The role-assignment PUT returns fast (~5 s) but Foundry data-plane RBAC takes a few minutes to propagate; the slow model-deployment LRO (30 s–20 min) absorbs that propagation time so the first call after azd up succeeds without retries.

If you do not have Microsoft.Authorization/roleAssignments/write , leave ASSIGN_RBAC=false (the default) and ask an admin to grant one of the roles below on the Foundry account afterwards.

Granting data-plane roles after azd up (one-liner if you own RBAC on the Foundry account):

Wait 1–3 minutes for the role to propagate to the Foundry data plane before retrying — see the intermittent 401 troubleshooting row .

Roles that work for Claude inference:

The role Azure AI Developer was historically called out as insufficient for Foundry inference. That guidance still applies to first-party AIServices models, but Claude/Anthropic deployments dispatch through Microsoft.CognitiveServices/accounts/MaaS/* , which Azure AI Developer already grants. Verified against claude-sonnet-4-6 on 2025-10-01-preview .

Both IaC variants run scripts/preflight-claude.ps1 (with preflight-claude.sh as a POSIX fallback) from the preprovision hook in azure.yaml , to give you a fast, descriptive error for the most common misconfigurations before azd up calls the Cognitive Services RP.

What the preflight does, and does not, do:

Why a quota check? The Cognitive Services RP returns an opaque 400 715-123420 "An error occurred. Please reach out to support for additional assistance." when there isn't enough TPM quota for the requested capacity. Worse, Terraform's azapi_resource skips ARM preflight validation, so the user sees this opaque code with no hint that quota is the cause. (Bicep / az deployment group create surface the real InsufficientQuota error.) The preflight catches the same condition before the deployment is even attempted, with a clear message and remediation instructions.

Run it standalone any time:

If the quota check fails, see what's used:

To list all Anthropic agreements (signed or not) visible on the active subscription:

To pre-accept explicitly (rarely needed thanks to the RP auto-accept; useful for restricted-subscription scenarios):

src/check_claude_quota.py queries the Azure Resource Manager APIs documented for Foundry quota — the Usages API and the Model Capacities API — and prints a single merged table keyed on (model, region) with TPM utilization, derived RPM limits, deployable capacity, and model version.

Caller authenticated via az login / azd auth login (or any other DefaultAzureCredential source).

Cognitive Services Usages Reader (or Reader ) at subscription scope. Without it, the calls return 403 .

The subscription must be Enterprise or MCA-E for Claude quota lines to appear (per the official prerequisites ).

Notes on the output:

RPM is not a separate quota line in the Usages API for Claude — only TPM is allocated. The RPM Limit* column is derived from the per-model RPM:TPM ratios published in the Foundry Claude docs (e.g. Sonnet 4.5 ships at 2 RPM per 1 kTPM; everything else at 1:1).

TPM Limit values are reported in thousands by the underlying API; the script multiplies by 1,000 so the table reads in raw tokens-per-minute.

The Model Capacities API requires modelVersion , not just modelName . The script discovers active versions automatically from locations/{region}/models filtered to format=Anthropic .

The Def RPM / Def TPM columns are the public non-EA defaults (always 0/0 because Claude is gated to Enterprise + MCA-E subscriptions); the TPM Used / TPM Limit / RPM Limit* / Capacity columns are the values your EA/MCA-E subscription is actually getting.

When you azd down (or otherwise delete) a Foundry / AIServices account, Azure does not immediately release the TPM quota it reserved. The account moves to a soft-deleted state and continues to count against your per-model quota for up to 48 hours, after which it is permanently purged automatically.

In day-to-day testing — where you may create and destroy several Foundry accounts in the same region in quick succession — this is the most common cause of "quota looks full but I have no live deployments" failures (which surface as opaque 715-123420 from Terraform or InsufficientQuota from Bicep).

List soft-deleted accounts in the active subscription:

Purge them one at a time (the original RG name is part of the deleted-account id and must be passed verbatim — the RG itself does not have to still exist):

Purge all of them in parallel (faster — each purge is a slow LRO):

After all purges complete, re-check quota:

Claude deployments fail with AnthropicOrganizationCreationException if modelProviderData is missing. industry must be lowercase to match the Foundry portal dropdown.

The Terraform variant uses azapi_resource for both the Foundry account and the Claude deployment, because the native azurerm_cognitive_account / azurerm_cognitive_deployment resources do not yet expose allowProjectManagement or modelProviderData ( tracked here ). The Bicep variant uses native resources at API version 2025-10-01-preview , which support both.

Use Claude models in Microsoft Foundry

azd Terraform support

Issues and PRs welcome. Please open an issue describing the change before sending large PRs.

Deploy Anthropic Claude on Microsoft Foundry with `azd up` (Bicep or Terraform) and call it with the official Claude SDKs over Entra ID.

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information