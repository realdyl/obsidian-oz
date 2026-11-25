---
title: Dorothy & Toto
type: character
status: draft
tags:
  - oz
  - oz/character
  - oz/protagonist
aliases:
  - Dorothy
  - Toto
updated: 2026-11-23
---

# Dorothy Gale & Toto

## Dorothy

**Role:** Protagonist. Mobility + summoner. Not a brawler.
**Age:** 18 (M-rated adult presentation locked 2026-11-05). **Voice:** plainspoken Kansas honesty; funny without trying.
**Look target:** Full-body feminine farm girl — capable, alluring, badass — not a capsule blob. Signature look includes layered blue gingham dress with lace petticoat & waist sash bow, **diamond-lattice fishnet stockings**, and **sculpted high-heeled silver stilettos** (Baum book Silver Shoes). Procedural body stand-in until authored mesh.

### Fantasy
You are not strong. You are *fast, kind, and stubborn* — and you make broken people believe they're whole.

### Verbs
| Verb | Input | Purpose |
| --- | --- | --- |
| Walk / run | Left stick | Exploration |
| Blink (short teleport) | Dodge button (tap) | Dodge with i-frames |
| Long teleport | Hold + aim | Traversal, gap crossing, escape |
| Kick | Attack | Stagger, shove, launch, break props |
| Summon / ability | Face buttons | Companion kit (see [[Summon System]]) |
| Call Toto | D-pad | Wayfinding hint |

### Arc
From *“I just want to go home”* → *“home is something I have to make possible for other people first”* → the final choice (see [[The Wizard (Boss)]]).

### Prologue
Kansas is Dorothy's baseline: no shoes, no friends, no powers — just her and the farm. The playable farmyard (basket, Toto, debris) establishes her as **resourceful before she is magical**. She is presented in black and white until the house lands; color arrives with Oz and the Shoes.

### Rules of Characterization
- Dorothy never enjoys killing; she disables, scatters, and outsmarts.
- She talks to her companions constantly — combat barks are conversations.
- She is scared often and acts anyway. Courage is the theme; she is the proof.

### Animation Targets (Shipped in Phase P8.2 — see [[Dorothy 2026 Flagship Character & Dynamic Sky Spec]])
- **2026 Flagship 3D Rig (`dorothy_visual.gd`)**: Sculpted heart-shaped face (blinking eyelids, dual-ring slate-blue irises, twin catchlights, arched brows, nose, Cupid's-bow lips, ears, freckles), articulated 4-joint spring-physics twin braids & silk ribbons, articulated hands with fingers, 12-pleat dynamic skirt + 20 scalloped lace hem beadlets, and 5 bespoke `set_outfit` Couture builds (`kansas_pinafore`, `dorothy_gingham`, `dorothy_velvet`, `dorothy_sovereign`, `dorothy_whip_plus`) across both gameplay and *The Tailor of Vices* Boutique turntable.
- **Grounded, weighty run + turn banking + landing cushion**; automatic & manual (`[V]`) **Silver-Shoe Heel-Click** whimsical flourish.
- **Blink** = aerodynamic dash pose + shimmering silver-cerulean departure silhouette afterimage (`CombatFx.blink_afterimage`) & starlight heel sparks.
- **3-Stage Martial Kick Combo** = Hit 1 Snap Roundhouse (`10 dmg`) → Hit 2 `360°` Spinning Back-Heel Sweep (`14 dmg`) → Hit 3 Leaping Starlight Pirouette Crescent Finisher (`22 dmg`) + dedicated Armament cast choreography (`play_cast`).

---

## Toto

**Role:** Wayfinding + secret-finding companion. Never a combat unit.
**Presence:** Sculpted 3D Cairn Terrier (`actors/companions/toto_companion.gd`, shared with Kansas `toto.gd`) who accompanies Dorothy across **all 7 levels (L1–L7)** and is **fully playable as Lead Slot 5 (`Tab` / Key `5`)** with his **`F` BARK** superpower (sonic terrier bark wave that startles/staggers nearby enemies + emits a directional scent-trail pulse, while remaining non-targeted by enemy aggro).

### Mechanics
| Ability | Trigger | Effect |
| --- | --- | --- |
| **Sniff the way** | Press call, or auto after 10 s idle/lost | Breadcrumb trail toward current objective |
| **Secret scent** | Contextual | Highlights hidden paths, dig spots, false walls |
| **Warning bark** | Passive | Audio/visual tell before ambush |
| **Fetch** | Contextual | Retrieves small quest items within reach |

### Design Intent
Toto replaces the minimap arrow. He is the **diegetic compass** — a living “follow the dog” system that keeps the player in the world instead of in the UI. He also gives the player a warm presence during lonely stretches.

### Accessibility Fallback
A toggle can enable a traditional waypoint marker for players who can't follow the trail (see [[Accessibility & Difficulty]]).

### Relationship
Toto is Dorothy's tether to home. In the finale, Toto is the one who “knows the way” — mechanically and emotionally.

## Related

- [[Basket & Toto Wayfinding]]
- [[Movement, Red Shoes & Kick]]
- [[Vision & Pillars]]
