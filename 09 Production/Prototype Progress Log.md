---
title: Prototype Progress Log
type: production
status: active
tags:
  - oz
  - oz/production
  - oz/prototype
updated: 2026-11-06
---

# Prototype Progress Log

Living log for Godot `oz/` vs this vault. Agents append dated bullets; do not delete history.

## 2026-11-06 — L5 pad fix · L6 Kansas homecoming finale

- **User:** L5 Road Home pad did nothing (no hourglass / next level). Wanted a return-home scene like L1, balloon-or-book-true mapped; **L6** interactive finale.
- **Book map:** Dorothy does **not** ride the balloon (Wizard's exit). Home = **Silver Shoes** · three heel clicks · prairie landing · Aunt Em. Distant balloon silhouette on L6 = flavor only.
- **L5 fix:** pad live from REVEAL; auto CHOICE on step; tall marker; **E ×3 heels** → `LevelTransition.go_to(homecoming)` (was `play_exit` only). F9 → L6.
- **L6:** `regions/kansas/homecoming.*` — B&W land → Aunt Em → porch FINAL STEP → epilogue sting. F8/F9 skips. Whimsy grey.
- Headless: `SMOKE_L6_OK` · `HOME_OK` · `ACT6_OK` · `GLINDA_PAD_OK`.

## 2026-11-06 — L3 open YBR · Whimsy every level · L5 Glinda

- **User:** Winkie road to Emerald sealed by solid gatehouse block; YBR must always be the path to the next level; whimsy on every level (same pattern, regional variation); develop L5.
- **L3 exit fix:** removed solid `Gatehouse` fill. Open arch = `GatePillarL/R` + `GateArch` lintel; continuous `YellowBrickRoad` / `YellowBrickRoadN` / `YellowBrickRoadGate` through the wall gap; glowing `EmeraldGatePad` at `YBR_EMERALD_GATE (0,0.08,-50)`; `PLAY_BOUND_Z` 56. ROAD_OPEN objective = follow YBR **north** through open arch · E green pad → Emerald (not walk into a building mass).
- **Whimsy autoload** `systems/whimsy.gd` — `setup` / `try_collect` / `prompt_if_near`; palettes `kansas` · candy/munchkin · `winkie` · `emerald` · `glinda`. Wired L1 Kansas, L3 West, L4 Emerald, L5 Glinda (L2 keeps local off-road whimsy; same bounce/giggle/chime/dance pattern). Never story-gated.
- **L5 scaffold:** `regions/quadling/glinda_court.*` — YBR south from Emerald exit → Glinda (Good Witch of the **South**) multi-line counsel (shoes always home) → pink **Road Home** pad FINAL STEP · E → ending sting. F8 skip counsel · F9 ending. L4 curtain/choice/DONE + F9 → Glinda via hourglass.
- Headless: `SMOKE_OK` / `SMOKE_L3_L4_OK` / `SMOKE_L5_OK` · `WEST_YBR_OPEN` / `WEST_OK` / `EMERALD_OK` / `GLINDA_OK` / `ACT34_OK` / `ACT5_OK` · `PLAY_OK`.

## 2026-11-06 — L2 linear YBR geography

- **User correction:** Locasta was wedged in the fallen house; companions sat left/right of spawn (Scarecrow east / Lion NE / Tin west). Request: Locasta **before** the house on a longer approach; **follow the Yellow Brick Road** to find each character in sequence; expand territory as needed.
- **Spine (south = +Z):** spawn `YBR_SPAWN (0,-52)` → Locasta `YBR_LOCASTA (0,-28)` clear of house (~z=-5) → house/Shoes → Scarecrow `(0,28)` → Lion `(0,62)` → Tin `(0,95)` → tree `(0,110)` → marshal `(0,118)` → West gate `YBR_WEST_GATE (0,128)`.
- Bounds `PLAY_BOUND` **72×140**; continuous NS brick strips; cottages/whimsy off-centerline only.
- Locasta counsel + objectives all say “follow the YBR south”; compass OPEN_ROAD points at West gate.
- Headless: `PLACE_OK` (Locasta before house + sequenced z) · `PLAY_OK` · `SMOKE_OK`.

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
- **Locasta first beat:** `MEET_LOCASTA` before Shoes — glowing greeter on the path from spawn, multi-line E dialogue that teaches Shoes / Scarecrow E / Lion / Tin / F kick / West later. Compass points to her until done.
- **Rogue map bounds:** puppets clamp to play half ~56×52 (inside MapBorder); march_from_afar never spawns past rails; always chase Lead (no idle rim); faster far sprint; threat compass ignores/clamps OOB.
- **Auto-git policy:** [[Auto Git Policy]] + AGENTS.md — commit/push oz + vault after verified passes.
- Headless: `LOCASTA_OK` · `BOUNDS_OK` · `HUNT_OK` · `HUNT_BOUNDS_OK` · `PLACE_OK` · `MULTI_TARGET_OK` · `PLAY_OK` · `KANSAS_OK`.

## 2026-11-06

### Act spine L3–L4 (prototype)
- Play order locked in code + [[Regions & Level Flow]] **Prototype spine**:
  - **L1** Kansas → **L2** Munchkinland → **L3** Winkie West castle → **L4** Emerald City Wizard tower
- **Book vs game:** Baum visits Emerald **before** West (commission); vault/prototype put West boss **before** Emerald curtain finale. Documented on Regions note. Optional future short first-Emerald commission on YBR between L2/L3.
- **Not** named "Tower of Oz" — Emerald City / Wizard's palace-tower; approach is **Yellow Brick Road**.

### L3 Winkie · West castle (`regions/winkie/west_castle.*`)
- Dark iron/ember palette, fog, braziers, keep towers — **not** Munchkinland candy.
- Full party starts free (prototype). Court winkie-tint puppets → face **Witch of the West**.
- Boss: hover smoke armor; Tin **axe** (`armor_break`) grounds her; **ruptured cistern water** (E draw → E douse) = **Baum melt** finish (book-true; film bucket is the same undoing).
- F8 force water-ready · F9 / north gate → Emerald.
- Headless: `WEST_OK` · `WEST_PRESENT` · `WEST_WATER_BEAT` via `tools/act34_sim.gd`.

### L4 Emerald City (`regions/emerald_city/wizard_tower.*`)
- YBR strip from approach → green gates → glass spires → throne projection **OZ**.
- Audience multi-line → pull **curtain** → humbug man → road-home stub (Glinda not built).
- F8 skip to audience · F9 done stub.
- Headless: `EMERALD_OK` · `YBR_OK` · `EMERALD_PRESENT`.

### Wiring
- L2 `OPEN_ROAD` spawns south **Yellow Brick Road** gate (E) → West; **F10** West · **F11** Emerald.
- `SMOKE_OK` / `SMOKE_L3_L4_OK` load all four scenes.
- Hourglass `LevelTransition` titles for West / Emerald enter-exit.

### Polish pass (L4 enter + speech + locomotion)
- **Enterable Wizard palace-hall**: gates → approach stairs → glowing palace doors (E) → hollow great hall, columns, throne dais (not a solid exterior box only).
- **Oz projection**: screen + face (eyes/mouth pulse) while mysterious; **body figure** of the humbug appears when curtain is pulled (vault P1 spectacle → P3 man).
- **E audience fix**: dialogue advances inside the hall (was dead because throne radius was too tight after gate teleport).
- **DialogueUI** autoload: on-screen speaker/body panel + OS TTS when available (AI VO path later: clip bank / ElevenLabs / local XTTS into `DialogueUI.speak`).
- **Locasta**: full-ish silhouette (legs, layered robe, bodice, arms, hat brim, wand, aura) — not cone+ball only.
- **Interiors**: title-flavored props (mayor desk/ledger, market counter/shelves, cottage bed/hearth) + plaques — not anonymous junk cubes.
- **Locomotion** autoload: shared step-up (~1.15m) + wall-steer for Dorothy, companions, and rogue munchkins; Tin terrace uses longer shallow stair run.
- **End-gates (Oz-true, no portals)**: L2 south YBR pad E → hourglass West; L3 north Emerald gate E → hourglass Emerald; L4 curtain E → choice E → hourglass sting. Objectives labeled **FINAL STEP**.
- Headless still `SMOKE_OK` / `SMOKE_L3_L4_OK` / `ACT34_OK`.

### Kansas L1 storm + farm rethink
- **Spread objectives:** basket ~barn west path; Toto ~east chicken run; house/Aunt center — no more three E markers in one cluster.
- **Basket:** larger wicker mesh + “Toto's basket” Label3D.
- **Aunt Em** + **Uncle Henry** full-ish B&W figures; Em multi-line porch dialogue (DialogueUI); Henry runs for stock in storm.
- **Cellar clarified:** Em already below; Dorothy too late — not a mystery third E.
- **FINAL STEP (book-true):** glowing farmhouse door E during cyclone → **house lift** ride → white-out hourglass → Munchkinland (not random debris as the only end).
- Distant grey cyclone funnel only — **no Kansas rainbow** (B&W lock + IP: no “Over the Rainbow”).
- Film-only left out: Professor Marvel wagon, Miss Gulch double.
- `kansas_sim` asserts spread distances + house-lift path → `KANSAS_OK`.

### Playability pass (KS layout · L2 YBR · whimsy · L3 melt clarity)
- **Kansas layout:** basket open south yard `(10, 0.05, 24)` — not wedged in a building; Toto east run; expansive prairie pads + map border ~56m; farmhouse/barn/coop **enterable** (E teleport interiors, walls stay solid; storm farmhouse door still wins in `STORM_RUN`).
- **Aunt Em chronology:** lines only **after** Toto is bagged — never “go get Toto” again.
- **L2 after party:** **FINAL STEP** = follow continuous **Yellow Brick Road south** to glowing West gate (pad + tall post + way markers). YBR spine extended to gate; play bounds widened; Locasta greets ~22m **north** on the road (not on top of spawn) with LOCASTA→ markers.
- **Whimsy (optional side fun):** bounce toadstools, giggle blooms, candy chimes, dance ring — **Whimsy** score HUD; not required for story.
- **L3 West defeat (clear path):** F/axe **weaken** only → **GROUNDED — WATER!** → compass → **Cistern** (blue beacon) → **E draw water** → **E douse Witch**. She cannot die by F alone. Lighting brighter (readable dusk, less fog).
- Headless: `SMOKE_OK` / `SMOKE_L3_L4_OK` / `KANSAS_OK` / `ACT34_OK` / `WEST_OK` / `EMERALD_OK`.

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
