---
title: OneLake Catalog Govern and Govern Skills
type: resource
created: 2026-11-02
updated: 2026-11-02
tags: [microsoft-fabric, onelake, governance, skills]
sources:
  - https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/govern-your-microsoft-fabric-data-estate-from-one-place-with-the-onelake-catalog/5377369
  - https://community.fabric.microsoft.com/oxcrx34285/rss/board?board.id=fbc_fabricupdatesblogs
  - raw/2026-11-02-github-open-issues-136-144/issues.md
  - raw/2026-11-02-github-open-issues-136-144/source-review.md
status: active
---

# OneLake Catalog Govern and Govern Skills

The [October 28 announcement](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/govern-your-microsoft-fabric-data-estate-from-one-place-with-the-onelake-catalog/5377369)
states that the OneLake catalog Govern experience is **generally available**,
and Govern Skills are available in Skills for Fabric. The full announcement was
reviewed through the official public RSS item with stable ID 5377369 after the
article page returned HTTP 403.

## Source Summary

Govern brings tenant and owner views, insights, domains, capacities, workspaces,
tags, and policies into one management surface. The **Policies Center remains
preview**; Govern's GA label does not make every nested capability GA.

Govern Skills add reusable procedures to agent access, organized around:

- **Health:** inventory, unused items, domain assignment, and governance metadata.
- **Protect:** sensitivity label coverage and domain default labels.
- **Trust:** descriptions, tags, endorsements, and curation priorities.

The announced operating sequence is **audit, explain, recommend, remediate**,
with supporting evidence, impact, priority, and action. Missing signals should
be identified as limitations and routed to the Govern experience or Purview,
not interpreted as healthy findings.

## Partner Interpretation

Package a baseline governance review, prioritized owner-approved remediation,
and recurring evidence checks. Supported admin APIs and appropriate permissions
remain prerequisites; skills do not grant permissions or replace platform
enforcement. Sensitive or destructive actions require confirmation.

Treat bulk changes as controlled remediation, not an automatic consequence of
an audit. The initial skill set has broader Health coverage than Protect or
Trust; do not market it as complete compliance assurance.

## Related

- [Skills for Fabric](skills-for-fabric.md)
- [Microsoft Fabric](../10-Notes/entities/microsoft-fabric.md)
- [Capacity observability and protection](fabric-capacity-observability-and-protection.md)
