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

## Prototype beats (clear 3-step rescue)

1. **WALK_FIELD** — YBR into scarlet beds; **separate sleep meters** on Dorothy **and** Lion bodies (not Lead-only). Both flesh **stick on first pass**.
2. **FLESH_DOWN** — Dorothy parks asleep mid-field; Lion **parks at mid-road** (`LION_FALL`). Auto Lead → Scarecrow.
3. **GET_CLEAR_AIR (1/3)** — SC or Tin walk **south** of the red field → glowing **CLEAR AIR** orb · **E** → Dorothy wakes and **stays parked south** (will not follow Lead back in). Lion snaps/stays mid-field asleep.
4. **GET_CART (2/3)** — **MICE CART** appears east of YBR · **E** to take it (required).
5. **HAUL_LION (3/3)** — with cart, walk to sleeping Lion · **E** starts haul · hold **SOUTH** until clear air.
6. **ROAD_OPEN** — party free · **FINAL STEP** West gate · **E** → L4.

## Code

- `oz/regions/poppy/poppy_road.gd` + `.tscn`
- Markers: `ClearAir`, `MiceCart`, `ClearAirPad`, `WestGatePad`, `YellowBrickRoad`
- L2 south gate → `_go_poppy_road` (not straight West)
- Poppy south gate → `_go_west` → `west_castle.tscn`
- Skips: **F8** clear field · **F9/F10** West · **F11** Emerald · L2 **F12** skips poppies to West

## Whimsy

Optional off-scent only (pre-field north + safe meadow south) — never required for story.

## Design notes

- Home/balloon not involved here.
- Teaches **Bond Lead swap** hard: flesh cannot finish the level alone.
- YBR remains the lost-player spine the whole way.
- Lion cannot walk through while Dorothy is stuck — body sleep + park.
