---
title: L6 Kansas Homecoming
type: region
status: active
tags:
  - oz
  - oz/region
  - oz/act-6
  - oz/kansas
updated: 2026-11-06
---

# L6 — Kansas Homecoming (interactive finale)

Mirror of [[Kansas Farmyard Prologue]] (L1): B&W, walk + E beats, cannot fail. Book-true return — **not** Dorothy riding a balloon.

## Book vs film

| Source | How Dorothy gets home |
| --- | --- |
| **Baum** | Glinda (South) teaches the **Silver Shoes**. Dorothy clicks heels **three times**, wishes for Aunt Em; shoes carry her over the desert and fall off. She wakes on the prairie; Aunt Em finds her. |
| **1939 film** | Wizard's **balloon** is *his* exit; Dorothy misses it. Glinda (film-North) tells her to click ruby heels. |
| **This game** | **Shoes** are the road home (L5 pad · E ×3). L6 is the **landing and reunion**. A distant balloon silhouette may drift in the sky as flavor — labeled as the **Wizard's**, never Dorothy's ride. |

## Prototype scene

`oz/regions/kansas/homecoming.*`

| Beat | Player does |
| --- | --- |
| Landing | White fade settles; B&W prairie; Toto nearby |
| Find Aunt | Compass → Aunt Em · walk |
| Reunion | E multi-line Aunt Em (home, Toto safe, porch) |
| Walk home | Compass → farmhouse **PorchPad** |
| FINAL STEP | E on porch → epilogue veil + narrator |
| Rest | Hourglass sting · “spine complete” hold |

**Skips:** F8 skip to walk-home · F9 end card.

**Whimsy:** grey prairie palette (optional, off path).

## Spine position

L1 Kansas → L2 Munchkin → L3 West → L4 Emerald → L5 Glinda (heels) → **L6 Homecoming**.

L5 `RoadHomePad` must call `LevelTransition.go_to(homecoming)` after three heel clicks — never `play_exit` alone.

## Related

- [[Q4 - Glinda & the Road Home]]
- [[Kansas Farmyard Prologue]]
- [[Regions & Level Flow]]
- [[IP & Legal]] — avoid marketing the film tagline; in-world paraphrase OK
