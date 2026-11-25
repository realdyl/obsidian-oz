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

## 2026-11-23 — Phase P5: Universal Jump, Solid Dais Platforms, Sealed Emerald Double Doors, Volumetric Oz Projection, Unified L7 Kansas & Label3D Sweep

- **Universal `Space` Jump + Low-Curb Step & Solid Platforms (`locomotion_util.gd`, `player_controller.gd`, `scarecrow.gd`, `tinman.gd`, `lion.gd`, `toto_companion.gd`, `glinda_court.gd`, `world_kit.gd`):**
  - Lowered `Locomotion.try_step` foot probe to `y = 0.025m` and added real vertical `Space` jumping (`velocity.y = 7.2–7.6`) across all 5 playable characters.
  - Added full `StaticBody3D` + `CylinderShape3D` colliders to Glinda's Pavilion marble dais (`top y = 0.11m`, Glinda at `y = 0.12m`) and made `YellowBrickRoad` strips flush (`top y = 0.03m`) so feet always rest cleanly on top of every surface.
- **Emerald Palace Sealed Double Doors & Volumetric Oz Projection (`wizard_tower.gd`, `world_kit.gd`):**
  - Added `WorldKit.build_palace_double_doors()` creating full-width `10.0m × 7.5m` ornate hinged Emerald & Gold Double Doors (and outer Emerald City double gates) with full-span colliders so players must press `E` to swing them open `105°` inward.
  - Added custom Fresnel rim-glow + horizontal scanlines spatial shader (`WorldKit.make_hologram_material`) and rebuilt `WorldKit.build_oz_projection_head()` into a multi-plane chiseled titan visage with scowling brow arches, deep orbital cavities, blazing golden-amber eyes, sweeping mustache wings, hinged rune jaw, rear 16-ray sunburst mandorla & rotating astrolabe strictly behind the head, and flanking brass projector pylons.
  - Added `_projection_dismissed` lock so once Oz's projection collapses at `Beat.CURTAIN`, `_pulse_projection` never restores it.
- **L7 Kansas Homecoming Unified with L1 Kansas (`homecoming.gd`):**
  - Upgraded Aunt Em (`build_kansas_farmer(aunt_em, true)`), added interactive Uncle Henry (`build_kansas_farmer(uncle_henry, false)`), removed the static sphere Toto stub so playable 3D Toto accompanies Dorothy, and added dressed Gale Farmhouse, Barn, 3D Clothesline, Lattice Windmill, swaying B&W prairie grass, and collidable horizon hills.
- **Game-Wide `Label3D` Sweep (`wizard_tower.gd`, `west_castle.gd`, `poppy_road.gd`, `glinda_court.gd`, `farmyard.gd`, `homecoming.gd`):**
  - Removed all remaining floating sky titles and raw white labels, replacing them with Tier-1 wooden signposts, Tier-2 architectural crests, and Tier-3 styled world badges.
- **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK` (`BLINK dist=1.70`, `TIN_PATH_OK`, `TAB_CYCLE_OK`), `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`) — all exited 0 with zero script errors.

## 2026-11-23 — Phase P4: Toto Controls, WYSIWYG Ground/Hills, All-Party Sprint, Natural Hill Climbing, Wizard Tower & Glinda's Court Overhaul

- **Toto Controls, All-Party Smooth Sprint & Natural Hill/Stair Climbing (`toto_companion.gd`, `locomotion_util.gd`, `player_controller.gd`, `scarecrow.gd`, `lion.gd`, `tinman.gd`):**
  - Fixed Toto arrow-key/WASD locomotion (switched from non-existent `camera_relative_move` call to `Input.get_vector` + `Party.camera_basis_node()` + `Locomotion.steer`).
  - Replaced Dorothy's instant single-frame teleport skip with a smooth high-speed `Space` sprint burst + continuous `1.8×` running mode, and added `Space` sprinting across **all 5 playable characters** (Dorothy, Scarecrow, Tin Man, Lion, Toto).
  - Removed the `25 m/s` forward teleport on smooth slopes in `Locomotion.try_step()` so hills are climbed naturally at normal walking speed and vertical stairs step rhythmically.
  - Added anti-oblivion failsafe floor recovery (`y < -3.5`) across all 5 party controllers.
- **WYSIWYG Collidable Borders, Emerald Skyline & Oil Can (`world_kit.gd`, `landing_square.gd`):**
  - Made `WorldKit.add_ground_apron()` and `WorldKit.add_horizon_hills()` full `StaticBody3D` collidable geometry and expanded Munchkinland's primary floor (`220×360`) so zero invisible border ledges exist.
  - Removed the legacy floating dark sphere + invisible `8×4×8` blocker (`_spawn_west_omen`).
  - Moved `WorldKit.add_emerald_skyline` ahead down the Yellow Brick Road (`Vector3(0, 0, 195)`) so players walk **toward** the Emerald City towers.
  - Fixed signpost back-face arrow orientation (`⬅  %s  ✦` vs `✦  %s  ➔`) and added a hammered-brass arrowhead cap on the 3D wooden pointer tip.
  - Upgraded Tin Man's Oil Can to `WorldKit.build_oil_can_visual()` (domed brass & copper oiler on a stone plinth).
- **L3 Poppy Field Smooth Rescue & Styled Badges (`poppy_road.gd`):**
  - Replaced instant Dorothy teleport on Clear Air with a smooth 2-second cooperative carry-out tween into `SafeMeadow`, and upgraded Mice Cart & Clear Air labels to styled Tier-3 `WorldKit.make_world_badge()` plaques.
- **L5 Emerald City / Wizard's Palace & L6 Glinda's Court Overhaul (`wizard_tower.gd`, `glinda_court.gd`, `world_kit.gd`):**
  - Crowned the Wizard's Palace with `WorldKit.build_emerald_palace_facade()` matching Munchkinland's crystalline spires; replaced the flat green circle Oz face with `WorldKit.build_oz_projection_head()` (towering 3D emerald-plasma visage, furrowed brow, blazing amber eyes, articulated rune-jaw & flame-shard beard, rotating brass-emerald astrolabe halo rings) and `WorldKit.build_humbug_wizard()`.
  - Transformed Glinda's Court with sculpted 24-segment `WorldKit.build_glinda_visual()` and `WorldKit.dress_glinda_court()` (8-column Alabaster & Rose-Gold Temple Rotunda, chandelier, Ruby-Filigree Throne, mirror-water Reflecting Pools with 3D lotus blossoms, wind-swaying rose trees, swaying meadow grass, and Silver-Shoe Compass Rose Altar).
- **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK` (`BLINK dist=2.27`, `TIN_PATH_OK`, `TAB_CYCLE_OK`), `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`) — all exited 0 with zero script errors.

## 2026-11-23 — Phase P3: Horizon Continuity, Sculpted Lion & Crows, 4-Wall Interiors, Signage Style Guide, Playable Toto, Poppy Carpet & Kansas Overhaul

- **Style Guide & Centered UI Shell (`08 Technical/Typography & Signpost Style Guide.md`, `ui/shell/pause_menu.gd`, `ui/shell/settings_menu.gd`):**
  - Authored [[Typography & Signpost Style Guide]] defining the 3-tier diegetic signage system (flush engraved arrow signposts, wrought-iron & walnut architectural building crests, and dark-velvet/gold world badges).
  - Fixed `SettingsMenu` bottom-right offset by wrapping both Pause and Settings cards in a full-viewport `CenterContainer` (with `"← Back to Pause Menu"` + `Esc` return).
- **Munchkinland Edges, Lion Anatomy, Crows & Enclosed Interiors (`world_kit.gd`, `lion_visual.gd`, `scarecrow_visual.gd`, `tinman_visual.gd`, `combat_fx.gd`, `landing_square.gd`):**
  - Added continuous horizon ground apron (`add_ground_apron`) + tighter outer hill skirts so zero sky-void drop-offs appear at Munchkinland's edges.
  - Rebuilt Cowardly Lion with horizontal organic feline anatomy (chest ribcage, lumbar waist, rounded haunches, 2-tier 18-tuft mane, articulated jaw, 3-toed paws, S-tail) and replaced the blocky green hedge den with `WorldKit.build_lion_sanctuary()` (mossy boulders, twisted-root arch, swaying ferns, lantern-berries).
  - Upgraded Scarecrow & Tin Man with articulated joint cuffs/ball-joints, brass buttons, and glowing clockwork heart jewel; upgraded `CombatFx.crow_storm()` to 9 sculpted 3D crows with continuous 4-cycle flapping 2-segment wings & fanned tails.
  - Closed the 4th front wall (`+Z`) + ceiling slab + ornate interior Exit Doorway in `WorldKit.build_rich_interior()`.
  - Upgraded YBR directional signposts (text flush on both faces of the wooden plank, zero floating text above) and building signs (`make_building_crest_sign`).
- **Playable Toto (`Tab` / Key `5`) + `F` BARK (`toto_companion.gd`, `party_manager.gd`, `play_hud.gd`, `combat_fx.gd`):**
  - Promoted `TotoCompanion` to a playable `CharacterBody3D` Lead (`Party.ID_TOTO`, Slot `5 Toto` in `PlayHUD`) with **`F` BARK** (`CombatFx.bark_wave()` sonic startle/fear ring + scent trail).
- **Winkie Castle Cistern & Witch Melt (`west_castle.gd`, `west_witch_boss.gd`, `world_kit.gd`, `combat_fx.gd`):**
  - Replaced flat cistern box + neon stick with `WorldKit.build_water_cistern()` (octagonal carved stone & copper well, iron arch, chain & wooden bucket, puddles).
  - Choreographed `CombatFx.water_splash_and_melt()` (water splash arc, billowing steam/smoke plumes, spiraling melt into a persistent obsidian-crimson puddle with her pointed gothic hat left behind).
- **L3 Deadly Poppy Field (`poppy_road.gd`, `world_kit.gd`, `dorothy_visual.gd`, `player_controller.gd`, `lion.gd`):**
  - Upgraded `WorldKit.build_poppy_beds()` to hardware-instanced `MultiMeshInstance3D` rendering **2,400+ swaying scarlet poppies**.
  - Added progressive drowsiness dialogue (`35%` Dorothy sleepy line, `65%` Lion yawn), realistic **lying-down sleeping poses** (`set_sleeping`) + rising `"Z · z"` slumber particles, smooth Lead-transition toast, and parabolic lift-and-place loading onto the **top center of the Mice Cart flatbed** (zero wheel clipping).
- **L1 Kansas Farmyard Deep Overhaul (`farmyard.gd`, `world_kit.gd`):**
  - Fixed Farmhouse interior collider trap & waist-clipping (disables exterior collider while inside, enclosed 4-wall monochrome prairie interiors with clear center foyer).
  - Replaced floating grey rectangles with `WorldKit.build_clothesline()` (cedar T-posts, sagging hemp rope, clothespins, hanging shirts/sheets), replaced neon sticks with `WorldKit.build_prairie_lantern_marker()`, sculpted woven wicker `build_wicker_basket()`, 4-leg `build_lattice_windmill()`, articulated `build_kansas_farmer()` for Aunt Em & Uncle Henry, and rolling grey prairie horizon hills.
- **Verification:** `SMOKE_OK`, `KANSAS_OK`, `PLAY_OK`, `ACT34_OK` (`ACT5_OK`, `ACT6_OK`, `ACT7_OK`) — all exited 0 with zero script errors.

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


---

## 2026-11-23 — Phase P5.5 Hotfixes (Oz Curtain Reveal, Glinda Pools, L1/L7 Kansas Parity & Storm) + Retail Audit & P6–P12 Master Roadmap

### Fixes Shipped (`realdyl/oz`)
1. **Emerald City Theatrical Velvet Curtain & Oscar Diggs Reveal (`world_kit.gd`, `wizard_tower.gd`)**:
   - Replaced stationary red box wall with `WorldKit.build_velvet_curtain()` (gilded brass rod, curtain rings, pleated crimson-velvet `LeftDrape`/`RightDrape` panels, gold hem & tassels).
   - Pressing `E` at the curtain now smoothly parts both velvet drapes (`scale.x -> 0.22`), illuminates a warm golden spotlight, and animates sculpted **Oscar Diggs** (`build_humbug_wizard`, facing `+Z` with spectacles, white moustache, coat, and brass projector console) stepping forward out from behind the curtain.
2. **Glinda's Court Reflecting Pools & Surface Clipping Sweep (`world_kit.gd`)**:
   - Upgraded `dress_glinda_court()` reflecting pools from un-collided `0.38 m` visual boxes to solid collidable `StaticBody3D` basins (`top y = 0.08 m`) so characters' feet always stand cleanly on top of every surface with zero leg/body clipping.
3. **L1 Kansas Farmhouse, Enterable Interiors, Storm Softlock Fix & Tornado Takeoff (`farmyard.gd`)**:
   - Dressed L1 `Farmhouse` identically to L7 `homecoming.gd` (`WorldKit.dress_cottage_exterior` + `GALE FARMHOUSE` crest sign + hidden flat `.tscn` roof + swaying B&W prairie grass).
   - Upgraded Kansas Farmhouse & Barn interiors to spacious, warmly lit 4-wall rooms with Exit Doors and Munchkinland's `_set_indoor_camera(true)` (`SpringArm3D` pulls cleanly inside to `2.45 m`, `fov = 72°`) so Dorothy is 100% visible inside every building.
   - Fixed storm-trigger softlock where talking to Aunt Em before finding Toto/Basket burned `aunt_talked = true` and prevented `Phase.NEED_SHUTTER`/`NEED_CELLAR` progression; allowed flexible shutter/cellar progression once Aunt Em has spoken.
   - Upgraded `_add_cyclone_funnel()` to a 9-tier twisting volumetric funnel cloud with overhead storm anvil, orbiting debris planks, dynamic lightning flashes, camera shake, and a dramatic `4.2 s` spiraling house takeoff.
   - Swept all remaining raw floating `Label3D`s in Kansas (`Chicken run`, `HouseDoor`, `Chicken coop`) to styled world badges.

### Obsidian Planning & Master Roadmap (`realdyl/obsidian-oz`)
- Authored [[Retail Completeness Audit & Phase P6-P12 Roadmap]] with an honest human-player audit, Mermaid phase graph, and self-recursive Phase **P6 → P12** execution blueprints (GUI Mega-Upgrade, Rated-M Combat & Kinky Armaments, 3× World Scale, Multi-Phase Bosses, Tailor of Vices Outfit Shop & Side Quests, AAA Visual Pipeline, and Audio/Shipping Polish).
- Authored [[Reference Benchmarks - Thrive & Alice Madness Returns]] and linked both into [[Oz Control Room]].

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK`, `SMOKE_L3_POPPY_OK`, `SMOKE_L3_L4_OK`, `SMOKE_L5_OK`, `SMOKE_L6_OK`, `SMOKE_L7_OK`
- `kansas_sim.gd`: `KANSAS_OK` (`STORM_RUN_OK`, `DOOR_REVEAL_OK`, `HOUSE_LIFT_OK phase=7`)
- `play_sim.gd`: `PLAY_OK` (`BLINK dist=1.70`, `TIN_PATH_OK`, `TAB_CYCLE_OK leader=scarecrow`)
- `act34_sim.gd`: `ACT34_OK`, `ACT3_POPPY_OK`, `WEST_OK`, `EMERALD_OK`, `GLINDA_OK`, `HOME_OK`, `ACT5_OK`, `ACT6_OK`, `ACT7_OK`


---

## 2026-11-23 — Phase P6 Complete (Retail GUI Mega-Upgrade, Diegetic HUD, Oz Grimoire, Save/Load Slots + Polish Fixes)

### Targeted Fixes & World Polish (`realdyl/oz`)
1. **Authentic Kansas Storm Debris (`regions/kansas/debris.gd`)**: Replaced flying grey boxes with 5 sculpted, tumbling Kansas farm debris silhouettes (8-spoke Wagon Wheel, Splintered Prairie Fence Section, Louvered Farmhouse Shutter, Iron-Hooped Farm Barrel, Corrugated Tin Roof Sheet).
2. **Munchkinland Out-of-Bounds Rogue Munchkin Fixed (`landing_square.gd`)**: Cleared baked `WallNorth` and anchored `_tag_baked_landing_puppets()` to a safe in-bounds rally point ahead/beside Dorothy so no rogue Munchkin ever spawns trapped behind her border.
3. **Gothic Bramble & Wrought-Iron Snare Grotto for the Lion (`world_kit.gd`)**: Replaced the rounded blob den with `build_lion_sanctuary()` featuring tiered craggy mossy cliffs, overhanging keystone arch, gnarled roots, crimson-thorn brambles, wrought-iron hunter's snare stakes & iron chain links, and warm amber woodland lanterns.
4. **Grassy Hills Burying Characters Fixed (`world_kit.gd`)**: Pushed `add_horizon_hills()` cleanly outside the `MapBorder` (`margin = visual_r + 14.0`) with matching full-width `SphereShape3D` colliders (`visual_r = rad * 1.35`) so hill skirts never poke into the walkable map or bury characters.
5. **Animated Flowing Water Shader (`world_kit.gd`, `landing_square.gd`)**: Added `WorldKit.make_flowing_water_material()` (dual-layer scrolling wave ripples, shimmering caustics, vertex wave motion, and Fresnel sky reflection) applied across Glinda's Court reflecting pools, Winkie Castle Water Cistern, and Munchkinland WellWater.
6. **Interactive Building Interior Activities (`systems/interior_pickup.gd`, `world_kit.gd`, `farmyard.gd`)**: Populated Kansas Farmhouse, Barn, and all Munchkinland cottage interiors with interactive **Gilded Desire Chests (`+15 Desire`)** and rotating **Shattered Memory Keepsakes** that unlock lore in the Oz Grimoire and restore Silver-Rose Vitality.

### Phase P6 — Retail-Grade GUI Mega-Upgrade & Diegetic M-Rated HUD (`realdyl/oz`)
- **Centralized `SaveManager` Autoload (`systems/save_manager.gd`)**: *Thrive*-style decoupled signal bus managing 3 persistent JSON save slots (`user://saves/slot_1..3.json`), Desire Fragments, Silver-Rose Vitality (`5/5` petals), Allure gauge, and Shattered Memories / Bestiary / Companion catalogs.
- **Diegetic *Alice*-Class Retail HUD (`ui/play_hud.gd`)**: Added top-right **Silver-Rose Vitality Cluster** (5 glowing rose petals), **Allure/Desire Filigree Bar**, live Desire counter, gilded Memory/Desire toast notifications, and the **`[Q]` Companion Quick-Wheel Overlay**.
- **Oz Grimoire / Codex (`ui/grimoire_menu.gd`, `[J]` key)**: *Thriveopedia*-inspired 4-tab dark-velvet & gold-filigree codex (*Quests & Controls*, *Companions*, *Bestiary*, *Shattered Memories*).
- **Pause Menu Save/Load Manager (`ui/shell/pause_menu.gd`)**: Added one-click **Oz Grimoire (J)** and **3-Slot Save / Load / Delete** panel directly inside the centered Pause Shell.

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK` (`SCARECROW_WALK dist=1.76`, `BLINK dist=1.70`, `TAB_CYCLE_OK`)
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)


---

## 2026-11-23 — Phase P7 Complete (Rated-M Kinky Armaments, Allure/Enamored AI, 3-Hit Combos, Rapture/Hysteria Mode + 10 Visual & UX Fixes)

### Screenshot & UX Fixes (`realdyl/oz`)
1. **Oz Grimoire (`J`) Mouse Cursor & Keyboard Tabs (`ui/grimoire_menu.gd`)**: Restored `Input.MOUSE_MODE_VISIBLE` on open (`MOUSE_MODE_CAPTURED` on close) plus `Left/Right` & `1–4` keyboard tab switching.
2. **Kansas Distinct Chicken Coop, Wire Fence & 8 Sculpted 3D Chickens (`world_kit.gd`, `farmyard.gd`)**: Built `WorldKit.build_chicken_coop()` (raised timber coop, sloped roof, nesting bay, wooden ramp, see-through chicken-wire fenced run, and 5 sculpted 3D prairie chickens outside + 3 chickens roosting inside the coop interior).
3. **Toto Grounded + Light Marker Offset (`regions/kansas/toto.gd`, `farmyard.gd`)**: Grounded Toto's paws firmly at `y = 0.0` trotting beside Dorothy (fixed floating `y = 0.55`) and offset the prairie lantern marker `2.0 m` beside Toto so it never impales him.
4. **Removed Obtrusive External Rectangular Doors & Shutter Clipping Text (`farmyard.gd`)**: Removed detached door plates in front of Kansas buildings (triggers sit invisibly flush with each building's built-in architectural door) and removed the wall-clipping shutter badge.
5. **Dorothy Faces Emerald City on Munchkinland Spawn (`landing_square.gd`)**: Oriented Dorothy, her `Visual`, and `CameraPivot` toward `+Z` down the Yellow Brick Road toward Locasta & the Emerald City spires.
6. **Naturalistic Lion Cave Den & Curved-Lid Treasure Chest (`world_kit.gd`, `landing_square.gd`)**: Replaced boxy Lion den slabs with an organic low-poly stone cave vault + draping ivy vines + iron snare chains; upgraded interior chests to vaulted brass-banded treasure chests with inner jewels; hid stray baked pink door slabs & floating `DEBTS` / `Deadly Poppy Field` sky `Label3D`s.
7. **Haunted Living Oak Solid Trunk (`actors/enemies/living_tree.gd`)**: Upgraded to a gnarled multi-root Haunted Oak with glowing amber eyes and `collision_layer = 1 | 4` so rogues can never clip inside the trunk.

### Phase P7 — Rated-M Combat Loop, Kinky Armaments & Rapture/Hysteria Mode (`realdyl/oz`)
- **4 Rated-M "Tools of Allure"** (`player_controller.gd`, `combat_fx.gd`, `puppet_munchkin.gd` — `[C]` cast, `[Z/X]` swap):
  - **The Lace Whip**: Crimson-lace lash pulling enemies into Kick range + `apply_bind(2.2)` + `+5 Desire`.
  - **Silk Bindings**: Magenta-silk cocoon immobilizing up to 3 nearby foes (`+50%` damage vulnerability).
  - **Hypnotic Perfume**: Expanding rose-violet mist applying **`♥ ENAMORED`** (`5.0 s`, halts attacks, bonus `+8 Desire` on execution).
  - **The Gilded Chain**: Tethers 2 foes with a golden beam mirroring `75%` of damage between them.
- **3-Hit Stiletto Kick Combo** (`F`: `10 → 14 → 22` dmg finisher with hit-stop & bonus Desire).
- **Rapture / Hysteria Desperation Mode (`H` key)**: 10-second crimson-vignette overdrive (`2.5×` damage, invulnerability, bonus Desire on every hit, pulsing `RaptureOverlay` on `PlayHUD`).

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK` (`BLINK dist=1.70`, `KICK hp 30 -> 20`, `SCARECROW_WALK dist=1.61`, `TAB_CYCLE_OK`)
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)


---

## 2026-11-23 — Phase P8 Complete (World Expansion, Emerald Boulevard & Tailor of Vices + 14 Visual, Physics & Polish Fixes)

### Screenshot & Gameplay Fixes (`realdyl/oz`)
1. **Kansas Fence Chime, Rustic Fences & Chicken Coop Swinging Gate (`farmyard.gd`, `world_kit.gd`)**: Cleared sporadic flat baked fence slabs, moved Fence Chime clear of obstacles, and added a hinged auto-swinging wooden gate (`95°`) on the chicken-wire run.
2. **Authentic Wicker Basket + Carried in Dorothy's Hand + Toto Forward Walk (`world_kit.gd`, `farmyard.gd`, `toto.gd`)**: Rotated the braided handle vertically (`90°`), offset the lantern marker beside the basket, attached a carried wicker basket directly to Dorothy's hand on pickup, and fixed Toto walking backwards (`atan2(-x, -z)`).
3. **Physical Kansas Storm Debris Knockdown (`farmyard.gd`)**: Storm debris hits now physically knock Dorothy back & down with recoil tilt and recovery instead of vanishing silently.
4. **Rated-M Blood / Ichor Splatter & Hit Reactions (`combat_fx.gd`, `puppet_munchkin.gd`, `west_witch_boss.gd`)**: Added `CombatFx.blood_splatter()` (arterial crimson droplet arcs + ground spatter pool for Munchkins; dark shadow-ichor for the Wicked Witch).
5. **Rebuilt Locasta & Glinda (Zero Waist-Poles!) + Glinda Facing & Water Splashes (`world_kit.gd`, `glinda_court.gd`)**: Removed the protruding tilted waist cylinders on both Locasta and Glinda, rebuilt smooth tiered royal silk ballgowns with detailed eyes & lips, rotated Glinda `180°` to face Dorothy, and added `CombatFx.water_splash()` droplets & ripple rings when wading through the reflecting pools.
6. **Zero Z-Fighting on Treasure Chests & Poppy Gate (`world_kit.gd`, `poppy_road.gd`)**: Offset brass chest bands cleanly outside wood faces and lifted `WestGatePad` cleanly above road height.
7. **Baum-Canon Flanking Fighting Trees (`living_tree.gd`, `landing_square.gd`)**: Replaced the single center-road tree with a flanking pair of Fighting Trees on the left & right of the Yellow Brick Road that lash branches and hurl thorny seed-pods (public-domain Baum Ch. 19 canon, avoiding MGM-only apple-throwing).
8. **Poppy Field Facing & Smooth Sleep Transition (`poppy_road.gd`)**: Oriented party `+Z` down the Poppy Road on spawn and added a smooth `0.75 s` collapse-asleep transition before handing Lead to Scarecrow.
9. **Solid Winkie Water Cistern (`world_kit.gd`)**: Added a solid `StaticBody3D` + `CylinderShape3D` collider to the octagonal stone cistern so characters can never walk through it.
10. **Emerald City Sealed Gates, Flush Approach Terrace & Unobstructed Wizard (`wizard_tower.gd`)**: Sealed the outer gate walls seamlessly to `MapBorder`, added a flush `PalaceLandingTerrace` eliminating the stair drop-off pit, and moved the velvet curtain & Oscar Diggs forward completely clear of the throne wall.

### Phase P8 — World Expansion & Emerald City Boulevard (`wizard_tower.gd`)
- Added **Disney-World Fairy-Tale Emerald Boulevard** gilded crystal lampposts lining the plaza approach and **The Tailor of Vices** ornate velvet boutique pavilion (`+25 Desire` Velvet Blessing).

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK` (`BLINK dist=1.70`, `KICK hp 30 -> 20`, `TAB_CYCLE_OK`)
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)


---

## 2026-11-23 — Phase P9 Complete (Multi-Phase Boss Overhaul, Boss Health HUD, AoE Telegraphs + Emerald Castle Ramparts, Wind Chimes & L7 Barn)

### Targeted Fixes (`realdyl/oz`)
1. **Fanciful Storybook Wind-Chime Whimsies (`systems/whimsy.gd`)**: Replaced bare chime blocks with sculpted curved shepherd-hook stands, gilded crown rings, 5 staggered tubular chime bells, and crystal star wind-catchers.
2. **Enterable Barn on L7 Kansas Homecoming (`regions/kansas/homecoming.gd`)**: Added enterable Barn door trigger, warmly lit 4-wall interior (hay bales, exit door, Desire Chest), and indoor camera matching L1 Kansas.
3. **Disney-World Fairy-Tale Emerald City Ramparts (`world_kit.gd`, `wizard_tower.gd`)**: Dressed the entire Emerald City curtain wall with `WorldKit.dress_emerald_city_wall()` — 6 soaring crystal-roofed castle turrets with gold finials, crenellated battlements, arched glowing stained-glass bays, royal crimson-gold banners, and flanking flowing-water Emerald Crystal Fountains.
4. **Unobstructed Wizard Reveal Stage (`wizard_tower.gd`)**: Widened interior Great Hall colonnade from `x = ±8.0` to `x = ±11.4` so no standing column blocks Oscar Diggs when the velvet curtain draws back.

### Phase P9 — Multi-Phase Bosses, Boss HUD & Telegraphed AoE Rings (`realdyl/oz`)
- **Retail Boss Health & Phase HUD Bar (`ui/play_hud.gd`)**: Added top-center gilded-crimson `BossHealthBar` with live phase readout (`show_boss_bar` / `hide_boss_bar`).
- **Telegraphed Ground AoE Danger Rings (`systems/combat_fx.gd`)**: Added `CombatFx.aoe_telegraph()` — expanding warning rings that fill and detonate.
- **Multi-Phase Wicked Witch of the West & Lollipop Guild Marshal (`west_witch_boss.gd`, `puppet_munchkin.gd`)**: Live Boss Health/Phase HUD tracking + Witch Phase I/II telegraphed violet Hex Fire Rings (accelerating in Phase II below 65% HP) + Phase III Water-Douse vulnerability.

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK`
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)


---

## 2026-11-23 — Phase P10 Complete (Interactive Tailor of Vices Shop UI, Live 3D Outfits & Armory + 10 World & UX Fixes)

### Phase P10 — Interactive "The Tailor of Vices" Shop UI & Live Outfits (`realdyl/oz`)
- **Shop UI (`ui/shop_menu.gd`)**: Accessible via **`[B]` key**, **Pause Menu (`Esc` → The Tailor of Vices)**, or stepping into the Emerald Plaza Boutique. Features 5 character tabs (*Dorothy*, *Scarecrow*, *Tin Man*, *Lion*, *Toto*), live `♦ Desire Fragments` balance, color swatches, perk descriptions, and one-click **Buy / Equip** buttons.
- **Live 3D Outfit & Weapon Application (`systems/save_manager.gd`)**: Purchased outfits & weapon upgrades (`Velvet Corset Couture`, `Silver-Lace Sovereign`, `Lace Whip Mastery`, `Burlap & Leather`, `Obsidian Crowmaster`, `Chrome & Crimson Velvet`, `Primal Gold Harness`, `Silver-Spiked Collar`) immediately apply live to the active 3D character models in the world.

### Targeted World, Animation & HUD Fixes (`realdyl/oz`)
1. **Toto Rides Inside Dorothy's Basket (`regions/kansas/toto.gd`)**: After claiming Toto in Kansas, Toto now hops directly into Dorothy's carried wicker basket with his head, ears, and wagging tail peeking over the rim.
2. **Fighting Tree Throwing Arms & Persistent Fallen Trunk (`actors/enemies/living_tree.gd`)**: Added articulated shoulder-arm boughs that visibly wind back and hurl seed-pods; defeated trees now topple onto the grass and remain fallen instead of disappearing.
3. **Poppy Field Meadow Sleep, Breezy Meadow Shrine & Smooth Cart Rescue (`regions/poppy/poppy_road.gd`)**: Dorothy & Lion now collapse inside the scarlet poppy meadow beside the road (`x = -5.4` / `x = 5.8`), removed mid-air asleep `Label3D`s, replaced the bare Clear Air orb with a sculpted `Breezy Meadow Shrine` archway, and smoothly tweened the Lion stepping off the cart + cart parking with zero popping.
4. **All Whimsical Objects Beautified (`systems/whimsy.gd`)**: Upgraded `bounce` to a Spotted Storybook Toadstool Trampoline and `giggle` to a Floating Crystal Fairy-Lantern with filigree halo ring; moved Emerald City `Gate dance` whimsy clear of the flanking fountains.
5. **Grandiose Portal Archway Checkpoints (`world_kit.gd`, `poppy_road.gd`, `west_castle.gd`, `glinda_court.gd`)**: Added `WorldKit.build_grand_portal_arch()` (gilded columns, crystal-crowned arch, glowing floor rune medallion) on level exits.
6. **Winkie Castle Walls & Boss HUD Overlap Fixed (`west_castle.gd`, `west_witch_boss.gd`, `play_hud.gd`)**: Aligned `WallN_L`/`WallN_R` flush with the north gate pillars, hid the Boss Health Bar immediately on `begin_melt()`, and shifted `LevelCompass` cleanly below the Boss Bar whenever active so HUD elements never overlap.
7. **L7 Kansas Chicken Coop Parity (`regions/kansas/homecoming.gd`)**: Added the matching Chicken Coop + Swinging Fence Gate + 5 sculpted 3D chickens to L7 Kansas Homecoming.

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK`
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)


---

## 2026-11-23 — Phase P11 Complete (2026 AAA Visual Pipeline: ACES Filmic, Glow/SSAO & Destructible Urns + Munchkinland Exit Fix, Animated Chickens & Silver Shoes Anim)

### Targeted Fixes (`realdyl/oz`)
1. **Munchkinland Progression Softlock Fixed (`landing_square.gd`)**: `Beat.TREE_GATE` and `Beat.MARSHAL` now immediately advance if `tree_down` or `marshal_down` was already achieved before entering that beat, and `_ensure_west_road_gate()` now renders the ornate `GrandPortalArch` (`ROAD TO POPPY FIELD`).
2. **Solid Fallen Tree Log (`actors/enemies/living_tree.gd`)**: Defeated Fighting Trees now keep `collision_layer = 1` with their `CollisionShape3D` rotated horizontally along the fallen trunk so players walk around the fallen log instead of passing through it.
3. **Animated Waddling & Pecking Chickens (`systems/chicken_actor.gd`, `world_kit.gd`)**: All sculpted 3D Kansas chickens now actively waddle around their fenced run and bob to peck grain.
4. **Aunt Em No-Repeat Dialogue (`regions/kansas/farmyard.gd`)**: Pressing `E` after Aunt Em finishes her 3 lines no longer repeats her idle line over and over (matching Locasta's clean behavior).
5. **Continuous Flush YBR Curbs (`world_kit.gd`)**: Replaced gapped peg-like curb blocks in `dress_ybr_spine()` with continuous flush golden-stone curbs (`height = 0.06 m`).
6. **Choreographed Silver Shoes Put-On & Full Visible Feet (`player_controller.gd`)**: Claiming the Silver Shoes now triggers a dip-twirl + silver ankle sparkle burst and raises `Visual.position.y = 0.03` so Dorothy's entire Silver Shoes sit cleanly on top of every surface.

### Phase P11 — 2026 AAA Visual Pipeline (`realdyl/oz`)
- **Forward+ ACES Filmic Post-Processing (`world_kit.gd`)**: Added `WorldKit.apply_aaa_post_processing(env, biome)` enabling ACES Filmic tonemapping, subtle HDR Glow/Bloom, and SSAO across Munchkinland, Emerald City, and Glinda's Court.
- **Destructible Gilded Porcelain Urns (`systems/destructible_prop.gd`, `world_kit.gd`, `landing_square.gd`)**: Added breakable porcelain urns along Munchkinland that shatter on `F`/`C` hit and drop `+5 Desire Fragments`.

### Obsidian Planning (`realdyl/obsidian-oz`)
- Authored [[Tailor of Vices - Visual Shop Overhaul Plan]] (3D `SubViewport` turntable preview + custom illustrated icons + stat delta bars).
- Added the **Recursive Sub-Phase Iteration Protocol (`P1.1 → P12.1`)** to [[Retail Completeness Audit & Phase P6-P12 Roadmap]].

### Verified Headless Godot 4.8 Simulations (All Exited 0)
- `smoke_check.gd`: `SMOKE_OK` (`L1–L7`)
- `kansas_sim.gd`: `KANSAS_OK`
- `play_sim.gd`: `PLAY_OK` (`SCARECROW_WALK dist=1.81`, `TINMAN_WALK dist=1.27`, `TAB_CYCLE_OK`)
- `act34_sim.gd`: `ACT34_OK` (`POPPY`, `WEST`, `EMERALD`, `GLINDA`, `HOME`)

## Phase P12 — Procedural SFX Audio, Accessibility/Difficulty Presets & Visual Polish Pass (Complete)
- **Munchkinland Scarecrow Unlock Blocker Fixed (`systems/destructible_prop.gd`, `regions/munchkinland/landing_square.gd`)**: Removed destructible porcelain urns from the `"enemies"` group (moved to `"destructibles"` while keeping `collision_layer = 1 | 4` so kicks still shatter them) and restricted `_count_live_landing()` strictly to `CharacterBody3D` enemies. Threat Compass restored to `7 live` and `Beat.FREE_SCARECROW` unlocks cleanly upon clearing the landing swarm.
- **Illustrated Tailor of Vices Product Icons (`ui/widgets/shop_item_icon.gd`, `ui/shop_menu.gd`)**: Replaced all flat `ColorRect` color blocks with bespoke 64×64 custom-drawn vector illustrations inside gilded velvet medallions (gingham dress, velvet corset gown, silver-lace sovereign gown, coiled crimson lace whip, straw hat/tunic, leather bandolier, raven cloak, tin plate & funnel, crimson velvet sash, lion mane, primal gold crown-harness, Cairn terrier, and silver-spiked collar).
- **Emerald City Skyline Ahead in Poppy Field (`regions/poppy/poppy_road.gd`)**: Added `WorldKit.add_emerald_skyline(self, Vector3(0.0, 0.0, 128.0))` and softened crimson fog density (`0.0042`) so the gleaming Emerald Tower rises on the horizon along the Yellow Brick Road.
- **Enterable Chicken Coop on L7 Kansas Homecoming (`regions/kansas/homecoming.gd`)**: Added full enterable interior (`E` door trigger + 4-wall timber room + nesting boxes + roosting perches + 3 animated sculpted chickens + interior chest + Exit Door badge + indoor camera zoom) matching L1 Kansas.
- **Phase P12 Procedural SFX & Accessibility**:
  - Added zero-dependency `AudioFx` autoload (`systems/audio_manager.gd`) synthesizing 16-bit PCM `AudioStreamWAV` SFX (`kick`, `whip`, `urn`, `chime`, `chest`, `buy`, `ui_click`, `rapture`) with a 6-voice player pool, wired into combat, destructibles, and the shop.
  - Added **Difficulty Presets (`Story 0.6x / Standard 1.0x / Nightmare 1.6x`)**, **Screen Shake toggle**, and **High-Contrast HUD toggle** in `ui/shell/settings_menu.gd` + `SaveManager`.
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.
- **Next**: Ready for recursive polish cycle **`P1.1 → P12.1`**!

## Phase P1.1 — Tailor of Vices 3D Boutique Stage, Drop-In Audio Loader & Prompt Libraries (Complete)
- **Live 3D Boutique Turntable Stage (`ui/shop_menu.gd`)**: Upgraded *The Tailor of Vices* to a `980×560` split-screen retail boutique with a live `SubViewportContainer` (`own_world_3d = true`), gilded rotating marble pedestal, drag-to-spin camera interaction, live sculpted 3D preview of the active character (`Dorothy`, `Scarecrow`, `Tin Man`, `Lion`, `Toto`), hover-to-preview outfit tinting, and a live 3-bar **Stat Comparison Strip** (`Allure Gain`, `Agility / Aura`, `Combat Edge`).
- **Drop-In Studio Audio Loader (`systems/audio_manager.gd`)**: Enhanced `AudioFx` to auto-load custom `.ogg`/`.wav`/`.mp3` files from `oz/assets/audio/{music,sfx,voices}/` (preferring user-generated Suno / ElevenLabs / CC0 assets over procedural fallbacks), and created the `oz/assets/audio/` folder scaffold.
- **Obsidian `10 Prompt Libraries/` Populated**: Created `00 - Asset Sourcing & Folder Guide.md`, `Audio Generation/Music/Suno Music Prompts.md`, `Audio Generation/Sound FX/SFX Generation Prompts.md`, `Audio Generation/Voices & Characters/Voice Profiles & Line Scripts.md`, and `Image Generation/Concept Art, Couture & Texture Prompts.md`.
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P2.1 — Tailored AAA GUI Remodel (Matching Approved References) (Complete)
- **Reusable Antique-Brass Filigree & Rose Vitality Widgets (`ui/widgets/ornate_frame.gd`, `ui/widgets/rose_vitality_bar.gd`)**: Created custom-drawn double-bordered antique-brass corner filigree frames (`#C49E5A` / `#E8C67A`) and the 5 Crimson-Silver Rose Buds on a thorny silver vine matching `ref_03_gameplay_hud.jpg`.
- **The Tailor of Vices Boutique Remodel (`ui/shop_menu.gd`)**: Remodeled directly after `ref_05_boutique_ui.jpg` — Left 40% live 3D spotlight turntable on a dark obsidian-marble pedestal inlaid with concentric golden rings + character nameplate plaque; Right 60% 2×3 gilded square medallion grid, 12-pip segmented gold stat bars (`VITALITY`, `ALLURE`, `COMBAT EDGE`), and hammered-gold `BUY & EQUIP` CTA.
- **Oz Grimoire Two-Page Book Spread (`ui/grimoire_menu.gd`)**: Remodeled directly after `ref_01_grimoire_ui.jpg` — Open leather-and-brass double-page velvet parchment spread with left-edge stitched bookmark tabs (`QUESTS`, `COMPANIONS`, `ARMAMENTS`, `BESTIARY`, `SHATTERED MEMORIES`), glowing silver-rose active tab, selectable left-page entries, center spine crease, and framed right-page lore/portrait view.
- **Gameplay HUD & Pause/Main Menu Shell (`ui/play_hud.gd`, `ui/shell/pause_menu.gd`)**: Added antique-brass filigree overlays (`OrnateFrame`) to the Objective Plaque, Vitality Ribbon, and full-screen Pause Menu with the Silver-Rose `OZ: THE ROAD HOME` crest (`ref_02_main_menu_ui.jpg`), and swapped plain vitality symbols for `RoseVitalityBar`.
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P3.1 — Party Portraits in HUD & Dialogue + High-Detail 3D Character Visual Overhaul (Complete)
- **Painted Party Portraits Wired into Gameplay HUD & Dialogue (`ui/play_hud.gd`, `systems/dialogue_ui.gd`)**:
  - Bottom-left Party Roster slots now display the cropped 256×256 painted character portraits (`Dorothy`, `Scarecrow`, `Tin Man`, `Lion`, `Toto`), dynamically scaling up for the active Lead and dimming for locked companions.
  - Dialogue Box now displays a gilded 92×92 antique-brass Speaker Portrait Medallion whenever Dorothy, Scarecrow, Tin Man, Lion, or Toto speaks.
- **High-Detail 3D Character Visual Overhaul (Gameplay + 3D Boutique Turntable)**:
  - **Dorothy (`dorothy_visual.gd`)**: Procedural royal-blue & white gingham check shader on skirt/bodice, dark-plum Victorian velvet corset waist-cincher with hammered antique-gold filigree buckle & rims, dark-plum back bow & petticoat hem, and ornate silver instep filigree buckles on her Silver Shoes.
  - **Scarecrow (`scarecrow_visual.gd`)**: Cross-stitched leather button eyes, brass gear-button badge & tucked raven feather on hat, crossed rope chest straps, brass belt buckle, and gnarled wooden walking staff with hanging brass key.
  - **Tin Woodman (`tinman_visual.gd`)**: Center gilded filigree clockwork heart cage with glowing crimson heart, twin brass-and-iron steam exhaust pipes on his back, glowing amber-gold clockwork eyes, and spiked riveted shoulder pauldrons.
  - **Cowardly Lion (`lion_visual.gd`)**: Ornate dark-leather & antique-gold chest harness with crimson-ribboned golden Courage Medal & ruby center.
  - **Toto (`toto_companion.gd`)**: Dark leather collar with sculpted gleaming silver 5-point star charm pendant.
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P4.1 — Character-Specific 3D & GUI Fidelity Blueprint + Enemy & Boss Visual Overhaul (Complete)
- **Obsidian Spec (`08 Technical/Character-Specific 3D & GUI Fidelity Blueprint.md`)**: Documented all 20 approved Character, Subcharacter, Enemy, and Boss design sheets into exact 3D mesh/shader construction specs and character-specific GUI treatments.
- **3D Enemy & Boss Visual Overhaul (`actors/enemies/puppet_munchkin.gd`, `systems/world_kit.gd`)**:
  - **Munchkin Guild Enforcer**: Added ruffled cream neck collar, rosy painted porcelain cheeks, bell-tipped rose pointed hat, and gold-filigree short hatchet blade (`enemy_05_munchkin_enforcer.jpg`).
  - **Lollipop Guild Marshal Boss**: Added candied-crimson spiked armored pauldrons, plumed shako hat with golden lollipop-swirl emblem, and massive serrated ceremonial cleaver (`enemy_06_marshal_boss.jpg`).
  - **Wicked Witch of the West (Baum Canon)**: Added sculpted raven head atop her folded dark-iron umbrella-staff, silver-grey braided hair, forged-iron eyepatch, and crown-banded witch hat (`enemy_04_wicked_witch.jpg`).
  - **Oz Volumetric Hologram**: Upgraded twin flanking pylons into coiled brass Tesla towers with glowing emerald arc orbs and giant interlocking brass projector gears (`enemy_02_oz_hologram.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P5.1 — Kansas Farmstead Architecture Fidelity Pass (Complete)
- **Archived 6 Kansas Farmstead References (`Generated References/Buildings/Kansas/`)** & created `08 Technical/Buildings & Architecture Visual Fidelity Spec.md`.
- **3D Architectural Upgrades (`systems/world_kit.gd`)**:
  - **Farmhouse & Cottage Exteriors**: Added leaning spoked wooden wagon wheel beside the front porch (`bldg_01_gale_farmhouse.jpg`).
  - **Parlor & Cottage Interiors**: Added braided oval floor rug and cast-iron pot-belly stove with tall vertical stovepipe (`bldg_05_farmhouse_interior.jpg`).
  - **Prairie Lattice Windmill**: Added wooden water trough and cast-iron hand water pump with lever handle at the tower base (`bldg_06_windmill_clothesline.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P6.1 — Munchkinland Storybook Architecture & Interior Fidelity Pass (Complete)
- **Archived 4 Munchkinland Architecture References (`Generated References/Buildings/Munchkinland/`)** & expanded `08 Technical/Buildings & Architecture Visual Fidelity Spec.md` with Section 2.
- **3D Munchkinland Architectural Upgrades (`systems/world_kit.gd`)**:
  - **Cottage Exteriors**: Added glowing circular stained-glass rosette window in the front gable peak (`munch_04_cottage_exterior.jpg`).
  - **Cottage Interiors**: Added 3 gilded wall-mounted smiling porcelain masks and a tufted rose-velvet parlor settee (`munch_01_cottage_interior.jpg`).
  - **Street Lanterns**: Added a delicate glowing hanging Northern Star charm beneath the iron cross-arm (`munch_02_signpost_lantern.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P7.1 — Winkie Castle & Emerald City Landmarks Fidelity Pass (Complete)
- **Archived 4 Winkie & Emerald References (`Generated References/Buildings/Winkie_Emerald/`)** & expanded `08 Technical/Buildings & Architecture Visual Fidelity Spec.md` with Section 3.
- **3D Landmark Upgrades (`systems/world_kit.gd`)**:
  - **Winkie Courtyard Water Cistern**: Added arched forged-iron dome canopy, spiked finial, spoked winch wheel, and twin hanging wooden water buckets (`we_04_winkie_courtyard.jpg`).
  - **Wizard's Velvet Curtain Throne Room**: Added 3 colossal interlocking brass clockwork gear rings behind the parting crimson velvet drape (`we_01_wizard_throne_room.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.

## Phase P8.1 — Quadling Country Pavilion & Oz Realm Portal Arches Fidelity Pass (Complete)
- **Archived 2 Quadling References (`Generated References/Buildings/Quadling/`)** & completed all 4 sections of `08 Technical/Buildings & Architecture Visual Fidelity Spec.md` (16/16 building & landmark references archived).
- **3D Architectural Upgrades (`systems/world_kit.gd`)**:
  - **Grand Portal Arches (`build_grand_portal_arch`)**: Added the 4 glowing Oz Realm Gemstones (Sapphire Blue, Emerald Green, Ruby Red, Topaz Gold) set into gilded bezels across the arch lintel (`quad_01_portal_arch.jpg`).
  - **Glinda's Ruby-Rose Pavilion (`dress_glinda_court`)**: Added a radiant golden 8-point starburst crown atop Glinda's rose dome and warm rose-gold glowing water lanterns lining the lotus reflecting pools (`quad_02_glinda_pavilion.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.


## Phase P9.1 — Core Story Quest Objects Fidelity Pass & Grimoire Quest Icons (Complete)
- **Archived 5 Core Story Quest Object References (`Generated References/Objects/Quest/`)** & created `08 Technical/Objects, Armaments & Props Visual Fidelity Spec.md` (`obj_01_water_cistern_bucket.jpg` through `obj_05_field_mouse_cart.jpg`).
- **GUI Quest Icons (`oz/assets/art/icons/`, `ui/grimoire_menu.gd`)**:
  - Cropped 256×256 painted icons for `silver_shoes.png` and `wicker_basket.png`.
  - Wired `silver_shoes.png` (Current Chapter) and `wicker_basket.png` (Controls & Keybindings) into the Oz Grimoire Quests tab (`[J]`).
- **3D Hero Quest Prop Upgrades (`systems/world_kit.gd`)**:
  - **Winkie Courtyard Water Cistern (`build_water_cistern`)**: Added the heavy iron-banded oak water bucket sitting beside the cistern rim with dual iron hoops, brimming shimmering water, and forged bail handle (`obj_01_water_cistern_bucket.jpg`).
  - **Tin Man's Vintage Oil Can (`build_oil_can_visual`)**: Upgraded base from stone plinth to a mossy forest tree stump with cut wood rings and moss collar, plus an angled brass filler cap on the reservoir shoulder (`obj_02_oil_can.jpg`).
  - **Dorothy's Wicker Picnic Basket (`build_wicker_basket`)**: Added twin slightly-ajar hinged wicker picnic lids atop the basket rim (`obj_04_wicker_basket.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.


## Phase P10.1 — Kinky Armaments Icon Integration, HUD Slot & 3D Combat VFX Overhaul (Complete)
- **Archived 4 Kinky Armament References (`Generated References/Objects/Armaments/`)** & expanded `08 Technical/Objects, Armaments & Props Visual Fidelity Spec.md` with Section 2 (`arm_01_crimson_whip.jpg`, `arm_02_poppy_atomizer.jpg`, `arm_03_gilded_chain.jpg`, `arm_04_silk_ribbon.jpg`).
- **Painted Armament Icons & Live GUI (`oz/assets/art/icons/`, `ui/play_hud.gd`, `ui/grimoire_menu.gd`)**:
  - Cropped 256×256 PNG icons: `arm_whip.png`, `arm_atomizer.png`, `arm_chain.png`, `arm_ribbon.png`.
  - Added a gilded 24×24 framed `_armament_icon` thumbnail beside the `[C]` Armament HUD slot in `play_hud.gd` that dynamically swaps as the player cycles armaments (`[Z/X]`).
  - Wired all 4 icons into `ARMAMENT_LORE` in `grimoire_menu.gd` (`[J]` → `ARMAMENTS`).
- **3D Combat VFX Fidelity Pass (`systems/combat_fx.gd`)**:
  - `whip_lash`: Burgundy-crimson silk lash with faceted ruby-crystal & golden filigree tip impact burst.
  - `silk_cocoon`: Iridescent dusty-rose/lavender silk rings paired with an orbiting glowing golden knotwork halo.
  - `perfume_cloud`: Dual-shell amethyst-violet and rose-pink narcotic mist bloom.
  - `gilded_chain`: Hammered antique-gold tether with twin engraved rose-copper shackle anchor flashes.
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.


## Phase P11.1 — Shattered Memories Codex Integration & Full Grimoire Art Completion (Complete)
- **Archived 5 Shattered Memory References (`Generated References/Objects/Memories/`)** & expanded `08 Technical/Objects, Armaments & Props Visual Fidelity Spec.md` with Section 3 (`mem_01_cyclone_ledger.jpg` through `mem_05_emerald_spectacles.jpg`).
- **Painted Shattered Memory Icons (`oz/assets/art/icons/`, `ui/grimoire_menu.gd`)**:
  - Cropped 256×256 PNG icons: `mem_cyclone_ledger.png`, `mem_aunt_em_locket.png`, `mem_guild_ledger.png`, `mem_porcelain_mask.png`, `mem_emerald_spectacles.png`.
  - Wired all 5 icons 1-to-1 into `MEMORY_CATALOG` in `grimoire_menu.gd` (`[J]` → `SHATTERED MEMORIES`), completing 100% real painted artwork across all 5 tabs of the Oz Grimoire!
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.


## Phase P12.1 — World Interactive Props, Destructibles & Whimsy Fidelity Pass (Complete)
- **Archived 4 World Prop References (`Generated References/Objects/WorldProps/`)** & completed all 4 sections of `08 Technical/Objects, Armaments & Props Visual Fidelity Spec.md` (**18/18 total Object & Prop references archived!**).
- **Cropped Desire Chest Icon (`oz/assets/art/icons/desire_chest.png`)** from `prop_02_desire_chest.jpg`.
- **3D World Prop & Whimsy Upgrades (`systems/world_kit.gd`, `regions/munchkinland/landing_square.gd`)**:
  - **Munchkinland Crystal Wind Chimes (`build_crystal_chimes`)**: Replaced the placeholder cyan box in `landing_square.gd` with a sculpted scrolling wrought-iron garden hanger, chandelier crown ring, alternating silver bells, and luminous faceted crystal prisms (`prop_01_crystal_chimes.jpg`).
  - **Breakable Porcelain Urn (`spawn_destructible_urn`)**: Upgraded to a rococo mint-and-blush porcelain amphora with scalloped gilded foot & flared rim, twin scrolling gold handles, and blush rose medallions (`prop_03_porcelain_urn.jpg`).
  - **Yellow Brick Road Gas Streetlamp (`make_street_lantern`)**: Added stepped octagonal cast-iron pedestal base, twin Victorian ladder cross-bar, and spiked crown finial atop the glowing amber lantern hood (`prop_04_ybr_streetlamp.jpg`).
- **Verification**: All 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exited `0` with zero script errors.
