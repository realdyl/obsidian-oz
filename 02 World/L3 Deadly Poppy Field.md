---
title: L3 Deadly Poppy Field
type: region
status: active
tags:
  - oz
  - oz/world
  - oz/prototype
  - oz/poppy
updated: 2026-11-06
---

# L3 · The Deadly Poppy Field

**Book:** Baum ch. VIII *The Deadly Poppy Field* + ch. IX *The Queen of the Field Mice* (public domain). MGM adapted the nap; we use **book** rules.

**Spine:** after full party (L2 Munchkinland) · before West castle (now L4). Continuous **Yellow Brick Road** N→S.

## Rules (Baum-true)

| Who | Poppy scent |
| --- | --- |
| Dorothy, Toto, Lion (flesh) | Sleep forever if left in the field |
| Scarecrow, Tin Man | **Immune** (not flesh) |

## Prototype beats

1. **WALK_FIELD** — YBR into scarlet beds both sides; **sleep meter** rises on Dorothy/Lion Lead  
2. **DOROTHY_DOWN** — auto-swap Lead to Scarecrow; **E** carry Dorothy **south** out of scent  
3. **LION_DOWN** — Lion too heavy mid-field  
4. **SAVE_QUEEN** — wildcat east of road · **E** stop cat · **E** Mouse Queen counsel  
5. **MICE_CART** — hitch mice (**E** cart)  
6. **HAUL_LION** — haul south to clear air  
7. **ROAD_OPEN** — **FINAL STEP** glowing West gate · **E** → L4 West castle  

## Code

- `oz/regions/poppy/poppy_road.gd` + `.tscn`
- L2 south gate → `_go_poppy_road` (not straight West)
- Poppy south gate → `_go_west` → `west_castle.tscn`
- Skips: **F8** clear field · **F9/F10** West · **F11** Emerald · L2 **F12** skips poppies to West  

## Whimsy

Optional off-scent only (pre-field north + safe meadow south) — never required for story.

## Design notes

- Home/balloon not involved here.  
- Teaches **Bond Lead swap** hard: flesh cannot finish the level alone.  
- YBR remains the lost-player spine the whole way.
