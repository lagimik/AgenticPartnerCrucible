---
title: ASCII Smuggling in Phishing Evasion
type: resource
created: 2026-09-05
updated: 2026-09-05
tags: [phishing, prompt-injection, unicode, defender-for-office-365]
sources:
  - https://www.microsoft.com/en-us/security/blog/2026/09/03/ascii-smuggling-crosses-over-from-ai-prompt-injection-to-phishing-evasion/
  - raw/2026-09-05-github-open-issues-72-85/issues.md
status: active
---

# ASCII Smuggling in Phishing Evasion

Microsoft research showing an AI prompt-injection technique crossing into conventional phishing evasion.

Attackers inserted invisible Unicode tag characters from U+E0000-U+E007F inside finance-related lure words so messages looked normal to recipients while disrupting literal keyword detection. A detector must account for legitimate tag-character uses, including the subdivision flag emoji sequences for England, Scotland, and Wales.

The campaign illustrates a broader defensive lesson: normalize and inspect what software processes, not only what users see, and rely on layered protections rather than one Unicode signature.

## Related Pages

- [[ai-governance]]
- [[ai-red-teaming-tool-selection]]
