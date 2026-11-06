---
title: Kansas Farmyard Prologue
type: level
status: draft
tags:
  - oz
  - oz/level
  - oz/prologue
aliases:
  - Act 0 Kansas
  - Farmyard
updated: 2026-11-05
---

# Kansas Farmyard Prologue

> Level **1** (Act 0). Black-and-white dusty farm. Teaches move, look, interact. Ends when the storm takes Dorothy into Oz.

## Sequence (playable)

1. Dorothy on barren farmland — broken fences, farmhouse, barn, windmill.
2. **Find the basket** → **E** to pick up (compass + glowing post).
3. **Find Toto** → he jumps into the basket.
4. **Latch the shutter** (E) — Aunt Em urgency.
5. **Check the cellar** (E) — story beat; storm starts either way.
6. **Storm rises** — dodge windblown debris (soft fail: reset to last safe spot).
7. **Large debris strike** → white-out → load Munchkinland (Level 2).

## Rules

- Pure **B&W** until impact (see [[Art & Audio Direction]]).
- No blink, no kick, no Shoes, no party Lead.
- Cannot fail out of the story (debris resets; large hit always advances).
- Book-true farm tone; not a 1939 frame copy ([[IP & Legal]]).

## Prototype path

- Scene: `oz/regions/kansas/farmyard.tscn`
- Main scene for Play until later flow menu.
- After large hit: `change_scene` → `regions/munchkinland/landing_square.tscn`.
- Playtest: **F9** skip to L2; **F8** force storm.

## Related

- [[Dorothy & Toto]]
- [[Witch of the East]]
- [[Regions & Level Flow]]
- [[Basket & Toto Wayfinding]]
- [[Party Control and the Bond]]
- [[Prototype Progress Log]]
