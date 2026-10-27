---
title: Design Note Template
type: meta
status: stable
tags:
  - oz
  - oz/meta
aliases:
  - Template
updated: 2026-10-26
---

# Design Note Template

Copy this into a new note and fill it in.

```markdown
---
title:
type: vision | world | character | system | enemies | boss | quest | technical | production | meta
status: idea | draft | review | stable | cut
tags:
  - oz
  - oz/<area>
aliases:
updated: 2026-10-26
---

# Title

> One-line pitch or founder quote.

## Summary
2–4 sentences. What is this, and why does it exist?

## Details
The real content: rules, beats, tables, diagrams.

## Design Intent
What player feeling or decision does this create?

## Risks / Open Questions
- [ ] ...

## Related
- [[...]]
```

## Conventions

| Rule | Detail |
| --- | --- |
| Filenames | Title Case, spaces allowed, no dates |
| Frontmatter | Required: `title`, `type`, `status`, `tags`, `updated` |
| Tags | Always include `oz` and one `oz/<area>` |
| Links | Use `[[Note Name]]` syntax; link only to existing notes |
| Diagrams | Mermaid preferred |
| Callouts | `> [!note]`, `> [!warning]`, `> [!question]` |
| Status | Move to `stable` only when reviewed; `cut` keeps history |
| Emoji | None |
| Dates | `updated` is ISO `YYYY-MM-DD` |

## Area Tags

`oz/vision` · `oz/world` · `oz/character` · `oz/system` · `oz/combat` · `oz/enemies` · `oz/boss` · `oz/quest` · `oz/technical` · `oz/art` · `oz/production` · `oz/accessibility` · `oz/meta`
