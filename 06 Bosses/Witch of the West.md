---
title: Witch of the West
type: boss
status: draft
tags:
  - oz
  - oz/boss
aliases:
  - West Witch
updated: 2026-10-26
---

# Witch of the West

## Fantasy

The regime's **air power and terror**. She is not a puppet of the Wizard — she is the thing he points at so the land stays afraid. She commands the flying monkeys, burns what she cannot control, and treats the Winkies as fuel.

## Silhouette & Read

- Tall, sharp, wrapped in smoke; a crown of bent silverware; one hand always hidden (her wand).
- Flies on a conjured storm-front; lands rarely.
- Her presence dims the palette and stills the wind.

## Arena

**The Winkie Tower / sky dock:** a vertical arena of catwalks, burner vents, and a captured flying-monkey roost. Phase transitions tear away sections.

## Phases

| Phase | Question | Mechanics | Counter |
| --- | --- | --- | --- |
| **P1 · Air Superiority** | Can you fight what you can't reach? | Flying monkey dives, fire lines, wind push | Blink timing; Tin Man Guard reflect; Crows on monkeys |
| **P2 · The Floor Is Lava** | Can you control terrain? | Burner vents ignite; oil slicks become fire traps | Oil placement, Roar to scatter, teleport routes |
| **P3 · Meltdown** | Can you finish under pressure? | She grounds, armor of smoke, desperation firestorm | Axe armor break, Gilded Edge stun, all-kit combo |

## Signature Mechanics

- **Wind Push:** a cone that shoves Dorothy toward hazards; counter with long teleport or Riveted Guard.
- **Fire Lines:** telegraphed lanes; oil + fire = player-made hazard (risk/reward).
- **Monkey Roost:** destroying roost perches reduces add waves permanently.
- **Smoke Armor:** only armor-breaking (axe/gilded) or environmental water staggers her.

## Tin Man's Role

- **Riveted Guard** turns her fire lines into reflected projectiles.
- **Oil Slick** creates player-controlled fire zones (and slip zones).
- **Hacking Axe** breaks the smoke armor.

## The Water Beat

Canon nod: water undoes her. **Baum-true** — Dorothy douses her and she melts (the film bucket is the same undoing, not a film-only gag). The arena has a ruptured cistern; a late-phase window grounds her so water is a **finisher after pressure**, not a free one-button skip from the start.

### Prototype (Godot L3)
- Scene: `oz/regions/winkie/west_castle.tscn` — dark courtyard, not candy Munchkinland.
- Flow: clear winkie-tint court → fight West (smoke hover) → Tin axe / pressure grounds her → **E** draw cistern water → **E** douse melt → road gate to Emerald City.
- Clarity: HUD/objective/compass name the cistern; blue beacon + **GROUNDED — WATER!** label; brighter dusk lighting so the court is readable.
- F8 playtest forces water-ready.

## Rewards

- Path to the Emerald City opens.
- Tin Man's final upgrade (hazard immunity).
- Flying monkeys defect / flee — seeds the finale.

## Voice

- “The Wizard sells them fear. I *deliver* it.”
- “You have lovely shoes. I'll take them off your little feet.”
- On defeat: “He'll burn it all before he lets her rule…”

## Related

- [[Tin Man]]
- [[Main Questline]]
- [[Boss Framework]]
- [[Enemy Roster]]
