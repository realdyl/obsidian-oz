---
title: Auto Git Policy
type: technical
status: active
tags:
  - oz
  - oz/technical
  - oz/ops
aliases:
  - git policy
  - auto commit
updated: 2026-11-05
---

# Auto Git Policy

Standing ops for agents working **Oz: The Road Home**. Applies to both design and code repos. Read this with [[Agent Token Efficiency]] before shipping.

## Repos

| Repo | Path (typical) | Remote |
| --- | --- | --- |
| Design vault | `obsidian-oz/` | `https://github.com/realdyl/obsidian-oz` |
| Godot game | `oz/` | `https://github.com/realdyl/oz` |

Each is its **own** git repository. Never commit vault notes into `oz/`, or game code into `obsidian-oz/`. Do not commit parent monorepo junk (`.DS_Store`, unrelated tutorials).

## When to update git

After a **landed chunk** of work (not every keystroke):

1. Update the vault progress log / relevant design notes **as you go** (see [[Prototype Progress Log]]).
2. `git status` in **both** repos that changed.
3. Stage only intentional files (respect `.gitignore`; no secrets, no `.godot/`, no Obsidian workspace cache).
4. Commit with a short conventional message describing the player-facing or design change.
5. **Push `main` to origin** when the user asked to ship, or when a multi-item pass is complete and verified (`PLAY_OK` / design notes linked).

Default assumption when the user says "ship it", "push", "save to GitHub", or finishes a playable pass: **commit + push both repos if both changed**.

## Commit message shape

- Vault: design intent first (`Sync vault: …`, `Document …`).
- Game: playable behavior first (`Ship …`, `Fix …`, `Add …`).
- One logical change per commit when practical; a single end-of-pass commit is fine for prototype bursts.

## Do not

- Force-push or rewrite history unless the user explicitly orders it.
- Commit credentials, `.env`, Printful/Clerk tokens, or local Godot editor state.
- Leave `main` ahead of `origin` after a user-requested push.
- Treat "update the vault" as optional — design SoT and git history travel together.

## Verification

- `git status -sb` clean on both touched repos after push.
- `main` tracks `origin/main` (no lingering ahead/behind unless offline).
- For game claims: headless `PLAY_OK` before calling the push "verified playable."

## Related

- [[Agent Token Efficiency]]
- [[Prototype Progress Log]]
- [[Architecture & Pipeline]]
- Root `AGENTS.md` (this vault)
---
