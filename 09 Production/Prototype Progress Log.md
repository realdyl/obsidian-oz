---
title: Prototype Progress Log
type: production
status: active
tags:
  - oz
  - oz/production
  - oz/prototype
updated: 2026-11-05
---

# Prototype Progress Log

Living log for Godot `oz/` vs this vault. Agents append dated bullets; do not delete history.

## 2026-11-05

### Flow
- Play order locked: **L1 Kansas farmyard** → **L2 Munchkinland landing** ([[Kansas Farmyard Prologue]]).
- GUI polish deferred until spine is stable (Control Room decision).

### Kansas (L1)
- Beats: basket → Toto → **latch shutter** → **cellar check** → debris storm → large hit → Munchkinland.
- Landmarks: barn, fence ring, clothesline wind, windmill blades, glowing interact markers.
- Cannot fail out of story (debris delays only).
- Headless: `KANSAS_OK` via `tools/kansas_sim.gd`.
- Playtest: **F9** → Munchkinland; **F8** → force storm path.

### Munchkinland (L2)
- Expanded map: hills, road spur, cottage clusters, fence lines (still one scene).
- Combat spine from [[Enemy Roster]] / [[Main Questline]] compressed:
  1. Silver Shoes
  2. Clear landing rogue swarm (kick lesson)
  3. Free Scarecrow → crow-field swarm (CAW confuse)
  4. Calm Lion (trust)
  5. Oil Tin Man
  6. Chop Living Tree (axe armor-break)
  7. Marshal rogue (armored mini)
  8. Open road
- Headless: `PLAY_OK` via `tools/play_sim.gd`.

### Kit verbs (Lead + F) — readable VFX
| Lead | F | Effect |
| --- | --- | --- |
| Dorothy | KICK | Arc + label + knockback/hitstop |
| Scarecrow | CAW | AoE ring + confuse status on puppets |
| Lion | ROAR | Expanding rings + fear flee + knockback |
| Tin Man | AXE | Slash + **armor_break** tag |

Shared FX: `systems/combat_fx.gd`. Enemies chase **current Lead** (Bond).

### Dorothy look (locked)
- Age **18**, M-rated adult presentation (Dylan lock 2026-11-05) — see [[Dorothy & Toto]].
- Full-body procedural mesh: hips, torso, bust silhouette, limbs, pigtails, walk cycle (`actors/dorothy/dorothy_visual.gd`).

### Controls
- Move: arrows primary, WASD secondary.
- Camera: free **360°** yaw (mouse look auto-capture; **RMB+WASD** orbit; **Z/C** orbit).
- Tab / 1–4 Lead when present+unlocked.

### Companions + Lead
- Tab via Party `_unhandled_input`; HUD explains blocks.
- Full-body procedural Scarecrow, Lion, Tin Man.
- Party `reset_party` on landing `_enter_tree`.
- **Follow current Lead**: Dorothy + all bonded friends trail whoever is Leading (not Dorothy-only).

### Playtest polish (v0.4.1)
- Scarecrow moved to east clearing `(10, 0.08, 18.5)` with **SCARECROW** beacon (was wedged at PinkCottage).
- Lion at north road `(0, 0.08, -22)` with orange **LION** posts past the gate.
- Tin Man on **west block terrace** with step ramps + grass; oil can on terrace.
- Label3D signs billboarded (fixes backwards DEBTS / road text).
- Enter/exit cottages with **E** (Pink/Blue/Debt/Guild + new Candy/Mint homes).
- Rogue Munchkin puppets: limbs + head (no snowman silhouette).
- Kansas shadow swim: bias/blur + Ground/player cast_shadow off.
- Headless: `PLACE_OK` · `FOLLOW_OK` · `PLAY_OK` · `KANSAS_OK` · `SMOKE_OK`.
- Scarecrow free is **E at the pole** after shoes + clear landing swarm — not automatic on kill-all. Baked puppets tagged `wave=landing`; empty square auto-advances; HUD explains early E.
- Building enter/exit: keep `_active_interior` while inside so E always exits (fixes Lion stuck after door Area lost). Walls mute while inside; party free members teleport with Lead.
- Companion unlocks (Scarecrow / Lion / oil / Tin) key off **current Lead** position — any bonded Lead can free the next in order.
- Interiors are **large hollow rooms** (~9×7) with furniture + warm lights. Entering hides exterior shell, shows interior fitout, pulls camera in (spring 2.6 / FOV 72) so any Lead can read the room.
- Tin Man unwedged: terrace + oil + Tin at far west `(-32, 1.05, 2)`; BlueCottage relocated to `(-6, 16)`; Mint Home to `(-8, 22)`; west road spur + TIN MAN markers.
- Lion den: open horseshoe thicket at `(6, -24)` — lion peeks from hollow (not buried in a green cube). Orange posts + "a trembling thicket" label.
- Doors: closed **DoorSeal** blocks walk-in; only **E** enters (teleport + interior view). Seal restores on E exit.
- Tin path: **WallWest** moved to x=-48 (was -24 sealing the terrace); east-facing stepped ramp; living tree past Tin at (-38) so FREE_TIN is reachable first.
- **Layout expand (crowding fix):** ground pads out to ~±60; cottages spread far from spawn (Pink 48,40 village edge · Blue −28,30 · Guild −24,−30 · Debt 30,−28 · Candy/Mint far). Scarecrow **east cornfield (44,4)** pole + stalks + approach aisle · Lion 10,−36 · Tin −42 terrace. Clear plaza on enter.
- **Scarecrow not wedged:** moved off PinkCottage; open field east of square with `_build_cornfield` (rows, clearing, west road aisle, low fence).
- **Signposts:** wooden board + painted face + bolts/chain; way markers use 3D chevron aimed at real target (no lying text arrows). Gentle sway.
- **HUD compass** (Kansas-style): 8-way arrow + target label + ahead/left/right/behind + meters; tracks beat target via camera basis.
- **Sticky threat compass:** top-center HUD live-updates nearest live munchkin (arrow · wave · dir · meters · live count). Separate from objective compass.
- **Rogues hunt the Lead:** map-scale `hunt_range` (~120); no freeze-wander outside short notice; faster approach when far; sneak always walks toward Lead.
- **Party fight:** rogues target all unlocked/present bodies via `Party.pick_threat_target` (spread + soft stick). Non-Lead Dorothy/Scarecrow/Lion/Tin auto-engage nearest foe with their kit; Tab still manual Lead.
- **Doors:** walls stay solid inside (no walk-through exit); DoorSeal only; staggered party walk-in/out procession (not pop teleport).
- **Map borders:** solid rails + tree thicket on Kansas and Munchkinland edges (no abyss fall).
- **Tin axe:** arm chop + `CombatFx.axe_arc` swing trail (not torso headbutt flash).
- **Hourglass level transition:** autoload `LevelTransition` — large spinning hourglass ~2s on level enter and on exit/change_scene (Kansas↔Munchkinland, OPEN_ROAD sting). Skipped headless.
- **Witches (book-true):** Locasta (Good North) greets near landing; East witch remains cold-open dead (not a greeter); Wicked West = distant NW omen only until later boss.
- **Auto-git policy:** [[Auto Git Policy]] + AGENTS.md — commit/push oz + vault after verified passes.
- Headless: `PLACE_OK` · `AUTO_LEAD_*` · `LION_PACK_OK` · `TIN_PATH_OK` · `MULTI_TARGET_OK` · `PLAY_OK` · `KANSAS_OK`.

## Related

- [[Kansas Farmyard Prologue]]
- [[Agent Token Efficiency]]
- [[Auto Git Policy]]
- [[Prototype Plan]]
- [[Dorothy & Toto]]
- [[Enemy Roster]]
- [[Party Control and the Bond]]
- [[Ozma, Locasta & Glinda]]
- [[Witch of the West]]
