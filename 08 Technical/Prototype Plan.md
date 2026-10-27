---
title: Prototype Plan
type: technical
status: draft
tags:
  - oz
  - oz/technical
  - oz/production
aliases:
  - Prototype
  - Vertical Slice
updated: 2026-10-26
---

# Prototype Plan

## Goal

Prove the **feel** and the **choice** in ≤ 6 weeks:

1. Blink + kick feels great.
2. Summoning a friend and using one ability is legible and fun.
3. One arena can be replayed with each companion and feel different.

## Scope

| In | Out |
| --- | --- |
| 1 greybox arena (Munchkinland square) | Full regions |
| Dorothy: move, blink, long teleport, kick | Full animation set |
| 2 companions: Scarecrow + Tin Man | Lion (add in slice) |
| 3 enemies: rogue munchkin, living tree, bear | Bosses |
| One ability each (Crows, Axe) | Full kits |
| Placeholder audio | Final music |
| Keyboard/mouse + gamepad | Accessibility suite (basic only) |
| — | Kansas prologue / house-flight set piece |

## Build Order

| Week | Milestone |
| --- | --- |
| 1 | Godot project, Dorothy controller, camera, greybox arena |
| 2 | Blink, long teleport, kick; dummy enemies; feel tuning |
| 3 | Companion follow/hold/engage; summon/dismiss; Scarecrow Crows |
| 4 | Tin Man Axe; meter economy; enemy variants |
| 5 | Arena waves; kit-swap combat; UI (health, meters) |
| 6 | Playtest rounds, tuning, capture trailer clips |

## Feel Tests (exit criteria)

- [ ] 10 playtesters can blink a telegraphed attack without instruction.
- [ ] 8/10 use the correct companion for a mixed wave at least once.
- [ ] Players describe the loop unprompted as “dodge, summon, use ability.”
- [ ] Kick has measurable hit-stop (80–120 ms) and reads on mute.
- [ ] No one asks “which character am I controlling?”
- [ ] Frame time stable at 60 fps with 8 enemies.

## Playtest Protocol

- 5 sessions/week, 20 min each.
- Record: deaths, kit swaps, ability usage, confusion moments.
- Ask: “What were you trying to do when you got stuck?”
- Never explain the Lion restriction; observe if the UI is enough.

## Deliverables

- Playable build (Godot export).
- 60–90 s capture for pitch.
- Tuning notes + next-slice backlog.

## Decision Gate

After prototype:
- If feel is **not** there → cut scope or re-evaluate engine.
- If feel **is** there → greenlight vertical slice (Act 1, full Scarecrow kit, first boss).

## Related

- [[Tech Stack Decision]]
- [[Architecture & Pipeline]]
- [[Game Plan - Roadmap]]
