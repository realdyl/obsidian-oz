---
title: Party Control and the Bond
type: system
status: draft
tags:
  - oz
  - oz/system
  - oz/combat
aliases:
  - Character Switch
  - Direct Control
  - Bond of the Road
updated: 2026-11-05
---

# Party Control and the Bond

> The Shoes never leave Dorothy's feet. What she can lend is **agency** — the right for a friend to lead when the road asks for *their* nature.

## The problem this solves

[[Summon System]] keeps Dorothy as the default avatar (readable combat, one AI companion). Players still need moments where **Scarecrow / Tin Man / Lion** are the hands on the stick: puzzles, traversal gates, and story beats that only work if you *are* that friend.

## Design lock (v1)

| Rule | Detail |
| --- | --- |
| Default | Dorothy is the avatar. One companion active as AI ([[Summon System]]). |
| Direct control | Allowed **only** for companions who are **unlocked** and **present** (summoned or standing in the party). |
| What transfers | **Agency**, not the Shoes. Blink / long teleport / heel-click stay Dorothy-only. |
| What the friend keeps | Their kit verbs and body rules (Scarecrow: light, crow call; Tin Man: heavy axe; Lion: roar/cloak — Lion still cannot *enter* hot combat as a summon). |
| Swap input | `Tab` cycle · `1` Dorothy · `2` Scarecrow · `3` Tin Man · `4` Lion (locked slots greyed). |
| Swap cooldown | 0.6 s (feel); no cooldown on story-forced swaps. |
| While you control a friend | The rest of the party **follows the current Lead** (Dorothy included). She can take damage; she does not use blink/Shoes while not Leading. Camera follows the controlled body. |
| Downed / dismissed | Cannot swap into them. Auto-return to Dorothy. |
| Lion exception | Direct control of Lion is allowed in **stealth corridors** and scripted beats; summon-near-enemies rule still applies when calling him into a fight as AI. |

## Why the story allows this — the Bond of the Road

After a companion **trusts** Dorothy (end of their unlock quest), the Silver Shoes recognize the bond. Dorothy can press her will through the bond so the friend walks first.

In-world line (Scarecrow unlock):

> “I don't have a brain worth borrowing. Borrow my *legs* instead — you think, I'll stumble where you point.”

Dorothy's spin: she is not a body-snatcher. She is **lending courage** the same way they lend brain, heart, and nerve. The UI calls it **Lead** (not Possess).

## When the game *requires* a lead swap

Not every corridor. Use **soft gates** (optimal) and rare **hard gates** (teaching).

| Moment | Who must lead | Why |
| --- | --- | --- |
| Scarecrow pole / crow roosts | Scarecrow | Crow paths and confuse-only puzzles; Dorothy's kick can't rearrange the field. |
| Tin barrier / rusted gate | Tin Man | Axe is the key; Shoes cannot cut iron. |
| Mombi scent-blind halls | Lion | Coward's Cloak field; Dorothy alone is seen. |
| Wizard illusion forks | Any bonded | Each friend sees a different false path; player chooses who leads. |
| Ordinary combat arenas | Dorothy default | AI companion + her blink/kick; swap optional for skill expression. |

**Level design rule:** a hard gate always teaches the swap in a safe room first. Never soft-lock a player who has not found Tab.

## When the player *may* swap freely

- Companion unlocked **and** currently present.
- Not in a cutscene, not during Dorothy-only shoe rituals (heel click shrine, prologue).
- Optional in open field combat after Act 1 — skill ceiling, not requirement.

## Prototype (current build)

- Kansas: basket → Toto → shutter → cellar → storm (cannot fail).
- Landing square expands vault join + [[Enemy Roster]] lessons:
  1. Dorothy + Shoes
  2. Clear landing swarm (kick)
  3. Free Scarecrow → crow field (CAW confuse)
  4. Calm Lion (trust)
  5. Oil Tin Man
  6. Living Tree gate (axe armor-break)
  7. Marshal rogue
- `Tab` cycles unlocked Leads. `1`–`4` direct pick.
- Failed Tab prints why (HUD).
- Kit VFX always fire on F while Leading (KICK / CAW / ROAR / AXE labels).
- Enemies chase current Lead body.
- Non-Lead party members trail `Party.follow_body()` (current Lead), not Dorothy-only.
- Wayfinding: emissive posts + billboard Label3D for Scarecrow / Lion / Tin terrace.
- Stepped block terraces with collision + auto step-up (~0.55 m); no walk-through hills.
- Cottages enter/exit via E (door Areas). While inside, E always exits (`_active_interior`); walls mute so Leads cannot soft-lock.
- Companion free/calm/oil interacts use **current Lead** body — Scarecrow can free Lion, Lion can oil Tin, etc. Unlock *order* unchanged.
- Signs use billboard so text is never mirrored from the approach path.
- Party autoload resets on landing enter.

## Rejected alternatives

| Idea | Why not |
| --- | --- |
| Separate character campaigns | Splits the fantasy; Dorothy is the spine of the journey. |
| Always-on free swap with Shoes on everyone | Breaks silver-shoe identity and IP clarity. |
| No direct control ever | Blocks companion-native puzzles; players asked for lead swaps. |
| Full party as equal RPGs | Scope explosion; contradicts one-active-summon readability. |

## Related

- [[Summon System]]
- [[Companion Kits]]
- [[Movement, Red Shoes & Kick]]
- [[Dorothy & Toto]]
- [[Scarecrow]]
- [[Prototype Plan]]
- [[Open Questions]]
