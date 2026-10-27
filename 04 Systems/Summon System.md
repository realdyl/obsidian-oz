---
title: Summon System
type: system
status: draft
tags:
  - oz
  - oz/system
  - oz/combat
aliases:
  - Summons
  - Companions
updated: 2026-10-26
---

# Summon System

## The Rule

**One companion active at a time.** Dorothy + one friend. Swapping is the core tactical decision.

This keeps the screen readable, the AI scope small, and the fantasy clear: *you are never alone, but you are always outnumbered.*

## Summon Rules

| Rule | Detail |
| --- | --- |
| Summon time | 0.8 s cast; interruptible by damage |
| Swap cooldown | 3 s after dismiss |
| Range | Must be within 8 m of Dorothy to appear |
| Duration | Stays until dismissed, downed, or meter empty |
| Downed | Companion retreats at 0 meter; 12 s recovery |
| Restrictions | Lion **cannot** be summoned near enemies (see below) |

### Lion Restriction (founder rule)

> “Summon lion — cannot summon close to enemies.”

- Applies **only** to the Lion.
- “Close” = within 12 m of a hostile in combat state.
- Enforced with a clear UI reason (“He won't come out here”).
- Design purpose: Lion is the **stealth/escape** answer; his entrance is a planned beat, not a panic button.

## Control Model

**Recommended:** AI-driven companion + player-triggered abilities.

- Companion follows, holds position, or auto-engages based on a simple behavior toggle.
- Player presses ability buttons to fire the kit; the companion animates it.
- Dorothy always remains the avatar — no full control swap.

**Alternative (stretch):** direct control swap. Cut from v1; it doubles animation and camera work. See [[Open Questions]].

## Ability Inputs

| Input | Action |
| --- | --- |
| Companion button (hold) | Summon menu / quick-summon last |
| Ability 1 (shoulder) | Primary kit ability |
| Ability 2 (face) | Secondary kit ability |
| Ability 3 (face) | Utility |
| Ability 4 (face) | Ultimate (costs full meter) |
| Dismiss | Double-tap companion button |

## Meter Rules

- Each companion has a dedicated meter (**Brain/Heart/Courage**).
- Abilities drain the meter; it refills slowly out of combat and on successful kicks.
- **Kick refunds meter** on hit — this is the loop that keeps Dorothy active while her friend is spent.

## Companion AI States

| State | Trigger | Behavior |
| --- | --- | --- |
| Follow | Default | Trails Dorothy at 2–3 m |
| Hold | Player command | Stays, guards an area |
| Engage | Enemy nearby | Uses basic attacks (low damage, mostly utility) |
| Downed | Meter 0 / heavy hit | Retreats, cannot act |
| Scripted | Boss/story | Fixed position and beats |

## Synergies (design targets)

| Combo | Effect |
| --- | --- |
| Oil Slick + Murder of Crows | Crows dive at slicked enemies; heavy stagger |
| Confuse + Gilded Edge | Confused enemies cluster; axe turns them to gold |
| Roar + Kick | Fleeing enemies get launched from behind |
| Decoy + Blink | Dorothy blinks to the decoy's “shadow” (upgrade) |
| Stitch + Axe | Tethered enemies share axe damage |

## Failure States

- Summoning into a one-shot AoE → companion downed (teaches positioning).
- Meter mismanagement → no answer for the next wave (teaches economy).
- Lion refusal → wasted input if not planned (teaches the restriction).

## Related

- [[Companion Kits]]
- [[Core Loop]]
- [[Accessibility & Difficulty]]
- [[Open Questions]]
