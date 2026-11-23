---
title: Prototype Progress Log
type: production
status: active
tags:
  - oz
  - oz/production
  - oz/prototype
updated: 2026-11-23
---

# Prototype Progress Log

Living log for Godot `oz/` vs this vault. Agents append dated bullets; do not delete history.

## 2026-11-23 — Phase P2: World Polish, Combat Choreography, Interiors, Toto L1–L7 & Whimsy Boons

- **Horizon, Hills & Foliage (`oz/systems/world_kit.gd`, `oz/regions/munchkinland/landing_square.gd`):**
  - Removed the giant mint-green `EmeraldSpeck` rectangle, tilted `EastCrook` monolith, and `WinkieHaze` slab; replaced with a distant crystalline **Emerald City skyline** (`add_emerald_skyline`).
  - Pushed decorative horizon hills strictly outside playable bounds and added **walkable, collidable meadow hills** (`add_walkable_meadow_hills` with matching `StaticBody3D` + `SphereShape3D`) so characters climb hills instead of sinking/swimming through them.
  - Replaced random ground pegs with swaying multi-blade **grass tufts & wildflowers** outside the YBR corridor (`absf(x) > 4.2`), driven by a custom wind + character-rustle vertex shader (`make_wind_grass_material`, updated live via `PlayHUD`), plus wind-sway shader on tree canopies (`make_leaf_wind_material`).
  - Replaced giant floating billboards (`"The road goes on."`, Locasta head text, duplicate interior labels) with crooked 3D **wooden signposts** (`make_wooden_signpost`) and distance-culled `Label3D`s.
- **Characters, Locomotion & Combat Choreography:**
  - **Dorothy (`dorothy_visual.gd`, `player_controller.gd`, `silver_shoes.gd`):** Added diamond-lattice **fishnet stockings** shader (`make_fishnet_material`), sculpted **high-heeled silver stilettos**, smoother 24-segment curves, multi-joint walk/run/idle breathing, `E` interact gesture, choreographed high-heel roundhouse/snap kick (`play_kick()` + `CombatFx.kick_arc` — removing rigid root bobbing), and a 3-ring starlight vortex on Silver Shoes pickup.
  - **Wicked Witch of the West (`west_castle.gd`, `world_kit.gd`):** Replaced the 3-primitive red triangle with a Baum-canon silhouette (pale gaunt face, black eye-patch, single glowing eye, obsidian & crimson velvet corset gown, gothic witch hat, iron umbrella-staff) and upgraded castle braziers to ornate iron lanterns.
  - **Companions (`scarecrow_visual.gd`, `lion_visual.gd`, `scarecrow.gd`, `lion.gd`, `combat_fx.gd`):** Centered **Scarecrow** inside a lush cornfield (`Vector3(4.5, 0.08, 28.0)`); added `play_caw()` + 8 articulated 3D flapping crows (`CombatFx.crow_storm`), `play_roar()` (rearing up on hind legs) + golden sonic shockwave (`CombatFx.roar_shockwave`), and idle breathing.
  - **Toto Across All Levels (`actors/companions/toto_companion.gd`, `kansas/toto.gd`, `ui/play_hud.gd`):** Sculpted 3D Cairn Terrier visual shared between Kansas and L2–L7, auto-spawned by `PlayHUD` to trot alongside Dorothy throughout Oz.
- **Interiors, Poppy Field & Whimsy Intrinsic Value:**
  - **Interiors (`WorldKit.build_rich_interior`):** Furnished `DebtCottage` and cottages with planked floors, parlor rug, wainscoting, rafters, hanging candelabrum, brick fireplace with 3D fire, stocked bookshelves, desk/ledgers, and framed wall plaques.
  - **L3 Deadly Poppy Field (`poppy_road.gd`):** Replaced flat red boxes with swaying 3D scarlet poppy flower beds (`build_poppy_beds`) and a carved wooden **Mice Cart** with spoked wheels & 6 harnessed 3D field mice (`build_mice_cart_visual`).
  - **Whimsy (`systems/whimsy.gd`, `landing_square.gd`):** Added interactive 3D squash/launch/spin pickup celebrations + `CombatFx` bursts and **Road's Blessing** intrinsic boon tiers (`25` Swift Heels +15% blink, `50` Bonded Courage, `75` Silver Trail) with HUD toast notifications.
- **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK`, `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`) — all exited 0 with zero script errors.

## 2026-11-23 — GUI & Presentation Overhaul (Unlocked & Master Architecture)

- **User:** Unlocked GUI overhaul phase. Current GUI is very rudimentary and basic (looks like a poor Minecraft clone). Must look **2026, modern, & sophisticated**. Provided open-source reference repos in `+ Gaming` (notably *Thrive* in Godot).
- **Status:** GUI Phase formally **UNLOCKED** in [[Oz Control Room]] and [[GUI & UX Roadmap]].
- **Planning & Architecture (Gemini 3 Flash):**
  - Analyzed Godot 4.8 project state, test harnesses, current `PlayHUD`, `DialogueUI`, and `LevelTransition`.
  - Confirmed 100% pass on all headless simulation suites (`smoke_check`, `kansas_sim`, `act34_sim`).
  - Outlined 2026 Modern & Sophisticated UI Architecture:
    1. **Design System & Theme Engine**: Procedural vector styling (`StyleBoxFlat`, high-DPI font overrides, dynamic margins, rounded corner geometry, subtle inner borders, drop shadows, and dual-palette system for Oz Warm Storybook vs Kansas Cold Prairie).
    2. **Modern Modular HUD (`ui/play_hud.*`)**: Retains 100% API compatibility (`set_objective`, `set_prompt`, `set_kansas_mode`, `set_party_roster`) while replacing flat `ColorRect`s with responsive widgets (`ObjectiveBanner` with `FINAL STEP` badge, `ContextPrompt` keycap badge, `ControlsStrip` pill, `LeadRoster` character chips, and modern threat radar).
    3. **DialogueUI v2 (`systems/dialogue_ui.gd`)**: Upgraded to a polished storybook frame with speaker badge, typewriter animation, advance indicator, and audio cue hooks.
    4. **In-Game Shell (`ui/shell/`)**: Full Pause menu (Esc toggle with mouse capture release), Settings modal (Volume, Display, A11y, Controls), and Restart Checkpoint.
    5. **Visual & Presentation Upgrades**: Alignment with *Alice: Madness Returns* beauty-and-decay mood and Rockstar-class cinematic camera & HUD restraint.
- **Execution Plan**: Staged execution for Gemini 4 Neon across G1 (Theme & Core HUD), G2 (Dialogue & Shell), and G3 (Polish & Visual integration).
- **Shipped (2026-11-23 — Execution Complete):**
  - `oz/ui/theme/oz_theme_factory.gd` — dual 2026 theme engine (Oz Storybook warm glass/gold vs Kansas Prairie film-noir slate).
  - `oz/ui/widgets/threat_radar.gd` — directional top-HUD threat rail with shape-accessible pips (Marshal diamond vs rogue circle), distance, and live count (retaining hidden `ThreatCompass` contract label for `play_sim`).
  - `oz/ui/play_hud.tscn` & `oz/ui/play_hud.gd` — Objective plaque with `★ FINAL STEP` highlight, `[E]` keycap-parsed Context Prompt pill, Lead Roster + `[F]` Kit Verb chip wired to `Party`, `show_toast` connected to `Party.swap_failed`, sleek Controls pill, auto-styled/relayouted level external labels, and `Fade` contract preserved.
  - `oz/systems/dialogue_ui.gd` — DialogueUI v2 storybook card with raised Speaker Nameplate, 75 cps typewriter reveal, `[E]` continue chip, Oz/Kansas auto-matching, and `set_tts_enabled`.
  - `oz/ui/shell/pause_menu.gd` & `oz/ui/shell/settings_menu.gd` — `Esc` pause shell with objective recap, checkpoint restart, and Settings (Master Volume, Mouse Sensitivity, UI Scale 80–140%, Fullscreen, TTS toggle).
  - `oz/systems/level_transition.gd` — refined vector brass/glass `HourglassCanvas` and storybook chapter title card plaque.
  - **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK`, `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`), `UI_API_SMOKE_OK` — all exited 0 with zero script errors.

## 2026-11-23 — Phase P1: 3D Characters, Rogue Munchkins, Storybook Architecture & Auto-Git Policy

- **Auto-Git Policy:** Created `oz/AGENTS.md` and updated `oz/README_DEV.md` so both `oz` and `obsidian-oz` enforce the [[Auto Git Policy]] (commit + push after verified passes).
- **3D Label Culling & Dialogue Quiet Hours:**
  - `oz/systems/world_kit.gd` (`WorldKit.apply_label3d_culling`) applies `visibility_range_end = 15.0` self-fade and restrained `pixel_size` across all world `Label3D`s so distant signs no longer pile up on the horizon.
  - `oz/ui/play_hud.gd` hides `LeadBar`, `PromptCenter`, and `ControlsPanel` while `DialogueUI` is open so party badges never peek behind the dialogue card.
- **Character & Rogue Munchkin Visual Overhaul:**
  - `oz/actors/enemies/puppet_munchkin.gd` — replaced static capsule/stick primitives with articulated Cabaret-Horror Marionettes (flared waistcoat, brass buttons, ruffled collar, cracked porcelain mask, glowing button eyes, crooked top hat, licorice cane; Marshal gets gilded shako + plume, shoulder epaulettes, breastplate, and halberd) plus procedural walk/telegraph/lunge/confused/feared limb animation.
  - `oz/actors/dorothy/dorothy_visual.gd` — layered gingham skirt with lace petticoat hem, wrap-around waist sash with sculpted back bow & ribbon tails, puffed sleeves, crossed pinafore straps, braided pigtails with bows.
  - `oz/actors/companions/` (`scarecrow_visual.gd`, `tinman_visual.gd`, `lion_visual.gd`) — ragged coat tails/floppy hat/straw bursts, riveted boiler chest/pauldrons/heart-latch/funnel/curved axe, and 10-tuft storm-cloud mane/muzzle/ears.
  - `WorldKit.build_locasta_visual` — layered starlight gown, capelet, silver hair, filigree star crown, and crystal wand.
- **Munchkinland Architecture, Trees, Lanterns & Horizon (`landing_square.gd` + `world_kit.gd`):**
  - Replaced flat box roofs on all cottages and Guild Hall with pitched storybook gable roofs, overhanging eaves, stone plinths, half-timbered beams, glowing paned windows with shutters & flower boxes, front porch awnings, crooked chimneys, and subtle stitch seams.
  - Upgraded border trees to gnarled multi-limb trees, lined the YBR spine with gold curb stones & alternating crooked wrought-iron street lanterns, and ringed the outer border with rolling horizon hills.
- **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK`, `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`) — all exited 0 with zero script errors.

## 2026-11-06 — GUI & UX Roadmap (handoff)

- **User:** Vault must hold a GUI roadmap so a future agent can significantly enhance GUI/UX when polish phase starts.
- **Note:** [[GUI & UX Roadmap]] under `08 Technical` — pillars, current `play_hud` / DialogueUI / LevelTransition APIs, UX debt, phases **G0–G5**, component checklist, per-level acceptance, handoff blurb.
- Linked from [[Oz Control Room]], [[Art & Audio Direction]], [[Milestones & Backlog]], [[Accessibility & Difficulty]], `AGENTS.md`.
- Gate unchanged: do not start chrome work until founder unlocks GUI phase; spine logic first.

## 2026-11-06 — Presentation north star (anti-Minecraft / real 3D)

- **User:** Do not ship looking like a Minecraft knockoff from prototype basics; want a **real 3D game**. Use vault Alice references; Rockstar (RDR / GTA V–VI) as deep craft research.
- **Updates:** [[GUI & UX Roadmap]] Visual north star + **P0–P4** presentation track interleaved with G chrome; anti-targets; Alice + Rockstar craft tables; quality bar; per-level presentation acceptance.
- [[Art & Audio Direction]] pillars + references + UI minimal-chrome note aligned.
- Control Room decision locked. Still **do not execute** presentation rebuild until founder unlocks GUI/visual phase.

## 2026-11-06 — L3 Deadly Poppy Field (book spine insert)

- **User:** Poppy nap is book (Baum ch.VIII–IX), not MGM-only. Want **own level** in proper sequence between Munchkin party and West.
- **Renumber:** L1 Kansas · L2 Munchkin · **L3 Poppy** · L4 West · L5 Emerald · L6 Glinda · L7 Homecoming.
- **Code:** `regions/poppy/poppy_road.*` — sleep meter (flesh), SC/Tin immune, carry Dorothy south, wildcat→Mouse Queen, mice cart haul Lion, YBR south FINAL STEP → West. Whimsy off-scent only.
- **Wiring:** L2 south gate / F10 → Poppy (`_go_poppy_road`); F12 L2 skips to West; Poppy F9/F10 → West.
- Headless: `SMOKE_POPPY_OK` · `POPPY_OK` · `L2_POPPY_WIRED` · `ACT3_POPPY_OK`.

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

### 2026-11-06 — L3 Poppy rescue clarity
- Both flesh stick first pass; Clear Air (1/3) · Mice Cart (2/3) · E Lion haul (3/3)
- oz ship after smoke/act34 OK
