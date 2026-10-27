## Purpose
Obsidian vault for Oz game design: design bible, systems, narrative, and production plan for **Oz: The Road Home** (working title).

## Ownership
Game Design / Production.

## Local Contracts
- This vault is its own git repository (`realdyl/obsidian-oz`, branch `main`); commit design changes there, not to a parent workspace repo.
- Never commit Obsidian workspace state or macOS metadata; see `.gitignore`.
- Preserve YAML frontmatter on every content note (not README.md/AGENTS.md): `title`, `type`, `status`, `tags`, `aliases`, `updated`.
- Keep one topic per note; use wikilinks for relationships.
- Use Mermaid for flows/diagrams; use callouts for notes, warnings, and open questions.
- No emoji.
- Filenames are Title Case with spaces; no dates in filenames.
- Record durable design decisions in the relevant note; record unresolved items in `09 Production/Open Questions.md`.

## Work Guidance
- Follow [[Design Note Template]] for new notes.
- The founder's gameplay notes are canon for intent; cite departures explicitly.
- Respect [[IP & Legal]]: Baum books are public domain; avoid MGM/Warner trade dress (ruby slippers, green-skinned witch, film designs, songs).
- Keep the design legible: rules, counters, and player decisions over lore dumps.
- Update `Oz Control Room.md` when the vault structure changes.

## Verification
- Verify all Markdown renders in Obsidian (tables, Mermaid, callouts, wikilinks).
- Check every new note has complete frontmatter and at least one inbound/outbound link.
- Re-read `09 Production/Open Questions.md` before locking design decisions.
- Run `git status --short` before handoff; the working tree should be clean and `main` should match `origin/main`.

## Child DOX Index
- (none)
