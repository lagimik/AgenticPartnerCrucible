---
title: Azure Catalyst Webapp Target Assessment
type: resource
created: 2026-11-20
updated: 2026-11-20
tags: [azure-catalyst, modernization, assessment, container-apps, app-service]
sources:
  - https://techcommunity.microsoft.com/blog/azuremigrationblog/azure-catalyst-expands-webapp-target-coverage/4574689
  - https://learn.microsoft.com/en-us/azure/migrate/create-application-assessment?view=migrate
  - raw/2026-11-20-agent-governance-context-migration/sources.md
status: active
---

# Azure Catalyst Webapp Target Assessment

## Source Summary

The [November 19 announcement](https://techcommunity.microsoft.com/blog/azuremigrationblog/azure-catalyst-expands-webapp-target-coverage/4574689)
adds **Container Apps** and **Managed Instance on App Service** to assessment
targets alongside App Service Code/Containers and AKS. It does not assign a
blanket GA status to all target platforms.

Discover servers, webapps, databases, applications, and dependencies; choose
region, sizing, and pricing assumptions; compare target-specific readiness,
warnings/remediation, recommended plans, and estimated monthly costs.
Optional GitHub Copilot Modernization code assessment adds changes and effort
estimates.

Managed Instance addresses Windows/.NET Framework dependencies such as COM,
registry, GAC, services, and mapped drives. Container Apps' scale-to-zero
behavior depends on the supported configuration.

## Delivery Boundaries

The [assessment workflow](https://learn.microsoft.com/en-us/azure/migrate/create-application-assessment?view=migrate)
requires discovered inventory and resolved collection issues. An incomplete
inventory can leave dependencies outside the scope.
Assessment is not migration, and cost/effort estimates are not binding quotes.
CAF/WAF design, application-owner-approved waves, reviewed changes, build
validation, deployment, and operational acceptance remain separate work.

## Partner Application

**Interpretation:** Offer a comparative target decision, with assumptions and
dependency evidence visible, rather than selecting containers by default.
Validate OS requirements, identity/network paths, scaling behavior, actual
pricing, migration sequencing, and rollback before committing a target.
No discovery agent, assessment, or deployment was executed.

## Related

- [Azure Catalyst](../10-Notes/entities/azure-catalyst.md)
- [AI-Augmented Modernization](ai-augmented-code-modernization-leader.md)
- [Oracle-to-PostgreSQL Code Migration](oracle-postgresql-application-code-migration.md)
- [Cloud-Native Application Platform](cloud-native-application-platform-leader-2026.md)
- [Digital Apps and Innovation](../100-Crucible/DigitalAppsandInnovationSolutionArea.md)
