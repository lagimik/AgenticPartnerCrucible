# GitHub Issue #115 — Cowork topic set

**Source:** https://github.com/lagimik/AgenticPartnerCrucible/issues/115
**Captured:** 2026-10-03
**Issue author:** lagimik (Marc-André Morisset)
**Issue state:** open, 2026-10-02

---

## Raw issue body

```
Copilot
Cowork Partner Kit (login using partner email)
https://aka.ms/CoworkPartnerKit

Copilot
Cowork Customer Scenarios
Copilot
Cowork Nifty Fifty Scenarios

Learn
more about Copilot Cowork
https://aka.ms/CopilotCoworkDocs

Cost
management demos on demos.Microsoft.com (login using partner email)
https://demos.microsoft.com/app/present/6694#/0/0

Credits
licensing guide
https://aka.ms/CopilotCredits/LicensingGuide

Copilot
Cowork Micro-skillings
https://aka.ms/MicroSkillingCoworkCopilot

Credit
Planning Model
https://aka.ms/CopilotCreditPlanningModel

Copilot
Credits on Learn (purchase, set-up. cost mgt)
https://aka_ms/CopilotCreditsLLearnCopilot

Cowork
Adoption site
https://adoption.microsoft.com/en-us/copilot/cowork/ai-user/
```

## Per-link resolution (checked 2026-10-03)

| # | Label | URL as given | Resolution |
| --- | --- | --- | --- |
| 1 | Cowork Partner Kit | https://aka.ms/CoworkPartnerKit | Redirects to `microsoftpartners.microsoft.com/Downloads/?filename=abs/protected/Cowork-partner-kit.zip` — protected partner download, login required. Anonymous fetch returned only an offline PWA shell. |
| 2 | Copilot Cowork Customer Scenarios | *(no URL in issue text)* | Not resolvable — label only, no link present in the issue body or its rendered markdown. |
| 3 | Copilot Cowork Nifty Fifty Scenarios | *(no URL in issue text; link supplied by user on 2026-10-03)* | `https://microsoftpartners.powerappsportals.com/Downloads/?filename=abs/protected/Copilot-Cowork-Nifty-Fifty-Scenarios.pptx` — protected partner download portal, login required. Anonymous fetch returned only the portal login shell. See `copilot-cowork-nifty-fifty-scenarios.md`. |
| 4 | Learn more about Copilot Cowork | https://aka.ms/CopilotCoworkDocs | **Public.** Redirects to `learn.microsoft.com/en-us/microsoft-365/copilot/cowork/` — Copilot Cowork overview page. Full content captured; see `copilot-cowork-overview.md`. |
| 5 | Cost management demos on demos.Microsoft.com | https://demos.microsoft.com/app/present/6694#/0/0 | Confirmed gated per issue's own "login using partner email" label. Anonymous fetch returned only the interactive demo-player SPA shell, no readable content. |
| 6 | Credits licensing guide | https://aka.ms/CopilotCredits/LicensingGuide | **Public** CDN link (`cdn-dynmedia-1.microsoft.com/.../Copilot-Credits-Guide.pdf`), but content type is `application/pdf`; binary PDF text was not extractable through the fetch tool used for this ingest. Page preserved as an access-note stub pending a PDF-capable re-ingest. |
| 7 | Copilot Cowork Micro-skillings | https://aka.ms/MicroSkillingCoworkCopilot | Short link does not resolve to the intended destination — redirects to a generic Bing search page. Likely a broken or expired aka.ms link as of capture date. |
| 8 | Credit Planning Model | https://aka.ms/CopilotCreditPlanningModel | **Public** but resolves to a pre-production (PPE) interactive single-page app (`nptnlopcost-ppe-*.azurefd.net`) titled "Copilot Credit Estimator" with no server-rendered text content — a tool, not a document. Page preserved as an access-note stub. |
| 9 | Copilot Credits on Learn | https://aka_ms/CopilotCreditsLLearnCopilot | URL as written in the issue is malformed (`aka_ms` instead of `aka.ms`, and `LLearnCopilot` likely a typo). A corrected guess (`aka.ms/CopilotCreditsLearnCopilot`) also redirects to a generic Bing search page — not resolvable as given or corrected. |
| 10 | Cowork Adoption site | https://adoption.microsoft.com/en-us/copilot/cowork/ai-user/ | **Public.** Content captured: Cowork budget-setting, guardrails, and usage-visibility guidance. See `cowork-budget-and-usage-governance.md`. |

## Disposition

- Full resource pages created for items 4, 10 (public, substantive content).
- Access-note stub resource pages created for items 1, 3, 5, 6, 8 (confirmed real/public entry points, but content is gated, binary, or an interactive tool rather than readable text) — following the established pattern for protected partner assets (cf. `cowork-partner-launch-kit.md`).
- Items 2, 7, 9 were **not** turned into pages — no working link is available for them (either no URL at all, or the short link does not resolve), so there is nothing to preserve or curate without fabricating content. Revisit if the issue is updated with working links.
