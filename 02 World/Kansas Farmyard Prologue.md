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
updated: 2026-11-06
---

# Kansas Farmyard Prologue

> Level **1** (Act 0). Black-and-white Gale farm. Teaches move, look, interact. Ends when the **cyclone lifts the house** with Dorothy and Toto inside.

## Book-true spine (Baum ch.1)

Uncle Henry and Aunt Em live on the grey Kansas prairie with Dorothy and Toto. When the cyclone comes: Henry looks after the stock; Em goes to the cyclone cellar; Dorothy runs for Toto, reaches the house too late for the cellar, and the house is carried into Oz.

## Sequence (playable)

1. Dorothy on barren farmland — farmhouse, barn, chicken run, windmill, clothesline.
2. **Find Toto's basket** (west barn path, ~15m+) → **E**. Basket is a readable wicker prop + label.
3. **Find Toto** (east chicken run, spread from basket) → he jumps into the basket.
4. **Talk to Aunt Em** on the porch (multi-line DialogueUI) — urgency, shutter, cellar.
5. **Latch the shutter** (E) on the farmhouse wall.
6. **Check the cellar** (E) — Aunt Em is already below; Dorothy is **too late** to join her. Story beat, not a fail.
7. **FINAL STEP:** Cyclone visible. Soft debris only delays. **E at glowing farmhouse door** with Toto → house lift sequence → white-out → hourglass → Munchkinland (L2).

## Rules

- Pure **B&W** until impact (see [[Art & Audio Direction]]). **No rainbow** in Kansas (would break B&W; “Over the Rainbow” is film IP — [[IP & Legal]]).
- No blink, no kick, no Shoes, no party Lead.
- Cannot fail out of the story (debris soft-reset; door always available in storm).
- Book-true farm tone; **not** a 1939 frame copy.
- **Out of prototype scope (film-only):** Professor Marvel / crystal ball wagon; Miss Gulch as West double; ruby slippers; film songs.

## Characters on farm

| Character | Role |
| --- | --- |
| **Dorothy** + **Toto** | Player; basket duty |
| **Aunt Em** | Porch counsel; already in cellar when Dorothy checks |
| **Uncle Henry** | Near stock/barn; runs for animals when storm starts |

## Prototype path

- Scene: `oz/regions/kansas/farmyard.tscn`
- After house lift: `LevelTransition.go_to` → `regions/munchkinland/landing_square.tscn`
- Playtest: **F9** skip to L2; **F8** force storm-to-door phase
- Headless: `tools/kansas_sim.gd` → `KANSAS_OK`

## Related

- [[Dorothy & Toto]]
- [[Witch of the East]]
- [[Regions & Level Flow]]
- [[Basket & Toto Wayfinding]]
- [[Party Control and the Bond]]
- [[IP & Legal]]
- [[Prototype Progress Log]]
