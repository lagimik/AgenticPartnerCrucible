---
title: "Copilot Studio Plugin (PAC CLI)"
type: resource
created: 2026-07-23
updated: 2026-07-23
tags: [copilot-studio, power-platform-cli, pac, migration, agent-authoring]
sources: [https://github.com/microsoft/copilot-studio-plugin]
status: active
---

# Copilot Studio Plugin (PAC CLI)

Experimental plugin for creating, editing, validating, and migrating classic agents to the new Copilot Studio experience. Successor to the `skills-for-copilot-studio` repository.

## Requirements

- Power Platform CLI (`pac`) version 2.9.3 or greater
- Install from [Microsoft Learn](https://learn.microsoft.com/en-us/power-platform/developer/cli/introduction) or [NuGet](https://www.nuget.org/packages/Microsoft.PowerApps.CLI)

## Installation

```
/plugin marketplace add microsoft/copilot-studio-plugin
/plugin install mcs-assistant@copilot-studio-plugin
```

## Status

Experimental research project — not officially supported. The Copilot Studio YAML schema may change without notice. Always review and validate generated YAML before deploying.

## Links

- [copilot-studio-plugin](https://github.com/microsoft/copilot-studio-plugin) — GitHub
