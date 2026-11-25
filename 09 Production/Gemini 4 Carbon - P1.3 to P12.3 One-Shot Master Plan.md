---
title: Gemini 4 Carbon — P1.3 to P12.3 One-Shot Master Plan
type: production
status: active
tags:
  - oz
  - oz/production
  - oz/roadmap
  - oz/carbon
  - oz/gui
  - oz/retail
updated: 2026-11-25
---

# *Oz: The Road Home* — Gemini 4 Carbon One-Shot Master Plan (`P1.3 → P12.3`)

> **Purpose:** This document is the complete, self-contained **One-Shot Execution Blueprint** for **Google Gemini 4 Carbon** to take *Oz: The Road Home* from its verified post-`P12.2` build (`realdyl/oz`) through **all 12 third-pass phases (`P1.3` through `P12.3`)** in a single cohesive push — transforming the game from a clean, playable 2018-feeling vertical slice into a **genuinely 2026, retail-buyable, deeply engaging dark-fairytale action-adventure**.

---

## 1. Honest Totalistic Audit (Post-P12.2 Baseline → 2026 Retail Bar)

### What Is Already Strong (Do Not Break)
- **Complete L1–L7 Playable Story Spine**: Kansas (`farmyard.tscn`) → Munchkinland (`landing_square.tscn`) → Deadly Poppy Field (`poppy_road.tscn`) → Winkie Castle (`west_castle.tscn`) → Emerald City (`wizard_tower.tscn`) → Glinda's Court (`glinda_court.tscn`) → Kansas Homecoming (`homecoming.tscn`).
- **5 Playable Characters + Live Couture Sync**: Dorothy, Scarecrow, Tin Woodman, Cowardly Lion, and Toto (`Tab` / `1–5`), with reactive `SaveManager.state_changed` outfit synchronization across all 7 levels and Kansas sepia parity.
- **2026 Sculpted Characters, Sub-Characters, Whimsies & Interiors**: Dorothy, all companions, Locasta, Glinda, Baum-canon Wicked Witch, Oscar Diggs, Aunt Em, Uncle Henry, Field Mice, Rogue Munchkins, and furnished 4-wall building interiors.
- **Dynamic Volumetric Cloud & Weather Sky Shader** (`oz_dynamic_sky.gdshader`) and **Unified Obsidian-Plum / Burnished-Gold / Imperial-Emerald UI Palette** (`oz_theme_factory.gd` + perimeter-safe `ornate_frame.gd`).
- **Strict Verification Suite**: All 4 headless Godot 4.8 sims (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) pass with exit code `0`.

### Why It Still Feels "2018" Instead of "2026 Buyable Retail"
1. **GUI Materiality & Motion Feel**: Even with clean padding and unified colors, `StyleBoxFlat` alone looks like flat vector UI. A 2026 retail game uses **custom GPU UI shaders** (subtle velvet micro-grain, animated metallic-gold specular sweeps, frosted glass depth blur, radial glow bloom), **bespoke typography** (serif display headers + crisp geometric sans body), **spring-physics micro-animations** (card hover tilt/lift, button press bounce, animated Desire counter roll-up, staggered menu reveals), and a **live 3D-diorama Title Screen**.
2. **Level Runtime & Exploration Depth**: Currently each act takes ~2–4 minutes of linear walking along the Yellow Brick Road. A buyable retail game needs **15–30+ minutes per act** filled with:
   - **Companion-Gated Environmental Puzzles** (reasons to swap between Dorothy, Scarecrow, Tin Man, Lion, and Toto outside combat).
   - **Verticality & Multi-District Exploration** (bridges, terraces, hidden rooftops, destructible props, secret **Velvet Sanctums**).
   - **Multi-Step Side Quests ("Vile Requests")** from named Oz denizens that pay out Desire Fragments, unique charms, and lore.
   - **Escalating Combat Encounters & True Multi-Phase Bosses** with readable floor AoE telegraphs, stagger/posture gauges, parry/dodge slow-mo, and companion synergy finishers.
3. **Progression Loop & Economy Meaning**: *The Tailor of Vices* and *Desire Fragments* exist, but players need **more ways to earn, spend, and feel progression** — Armament Upgrades (Tier I → III), Passive **Silver-Shoe Charms / Relics**, **Combo Style Rank** (`D → C → B → A → S → SOVEREIGN`) that multiplies Desire drops, and **New Game+ ("The Velvet Road")**.
4. **Under-Leveraged Master Image Assets**: The founder's curated Nano Banana image library lives at:
   - **Source Folder:** `/Users/dylanroberts/Library/Mobile Documents/com~apple~CloudDocs/Creative Cloud Files/+ assets/Nano Banana/Oz`
   - **Already Imported in Godot:** `res://assets/art/portraits/`, `res://assets/art/scenes/`, `res://assets/textures/`
   - Carbon should audit the source folder for any higher-resolution or unused icons, textures, portraits, and act title cards, import any missing gems into `res://assets/`, and weave them into **every** screen (loading title cards with Ken Burns pan, Grimoire full-page illustrations, Shop product medallions, Dialogue portraits with dynamic emotion framing, and seamless PBR world/prop materials).

---

## 2. Unified 2026 Visual & GUI Design System (Zero 2018 Flatness)

All screens (**Title Screen, Pause Menu, Tailor of Vices Boutique, Oz Grimoire, Settings, Dialogue, Boss Bar, and Gameplay HUD**) must strictly obey ONE design language:

| Token | Hex | Role |
| --- | --- | --- |
| **Obsidian Plum** | `#120914` | Primary modal & HUD card surface (layered with subtle GPU velvet-grain shader) |
| **Smoked Amethyst** | `#1B1024` | Recessed inner cards (Objective ribbon, Save slots, Stat detail box) |
| **Hammered Antique Brass** | `#C49E5A` | Perimeter filigree frames (`OrnateFrame` strictly outside content safe-zone) |
| **Burnished Gold** | `#E8C67A` | Titles, active selection rings, hover rim illumination, keycap highlights |
| **Imperial Emerald** | `#166B4B` | Singular Primary Hero CTA (`PLAY / RESUME`, `BUY & EQUIP`, `SAVE`) |
| **Velvet Crimson-Rose** | `#641A31` | Boutique / Desire / Allure / Boss Health accents |
| **Warm Ivory Parchment** | `#EFE0C2` | High-contrast readable body copy (`>= 10:1` contrast on Obsidian Plum) |
| **Kansas Film-Noir** | `#121417` / `#E8EAEE` | Automatic monochrome silver-slate parity in L1 & L7 |

**Mandatory 2026 GUI Craft Rules:**
- **Strict Safe-Zone Padding**: Every filigree-framed panel must maintain `>= 22 px` clearance between the inner gold hairline and any text, button, or keycap.
- **GPU Shader Polish**: Add `ui_velvet_card.gdshader` (subtle radial spotlight, woven velvet micro-grain, top-edge glass specular highlight) and `ui_gold_shimmer.gdshader` (periodic metallic light sweep on primary emerald/gold buttons and equipped cards).
- **Tactile Motion**: Every modal opens with `0.18s` cubic-out scale + fade; buttons lift `2 px` on hover with soft gold bloom and compress on press; Desire counter rolls numerically when fragments are gained or spent.

---

## 3. Creative Gameplay Mechanics to Make Every Level Longer, Deeper & Buyable

### A. Core Gameplay Loops (Cross-Level)
1. **Combo & Allure Style Rank (`D → C → B → A → S → SOVEREIGN`)**:
   - Mixing Dorothy's 3-hit Silver-Shoe Kick, Lace Whip pull, Blink Dodge, and Companion Kit Verbs (`CAW`, `AXE`, `ROAR`, `BARK`) raises a live diegetic **Style Emblem** on the right HUD.
   - Higher ranks boost Desire Fragment drops (`1.2×` to `2.5×`) and charge **Rapture / Hysteria Mode** faster.
2. **Perfect Blink-Dodge ("Silver Mirage")**:
   - Blinking (`Space`/`Shift`) right before an enemy strike triggers `0.35s` slow-motion hit-stop, leaves a shimmering silver-starlight decoy, restores 15% Allure, and opens a guaranteed counter-kick stagger.
3. **Companion Synergy Puzzles (Every Oz Act)**:
   - **Scarecrow (`CAW`)**: Triggers elevated Crow-Bell switches & disperses Illusion Crows hiding secret alcoves.
   - **Tin Woodman (`AXE`)**: Severs rusted iron drawbridge chains, shatters crystal barricades, and chops fallen timber shortcuts.
   - **Cowardly Lion (`ROAR`)**: Clears thorny bramble-gates, intimidates cowardly sentries into dropping gate keys, and shatters fragile porcelain walls.
   - **Toto (`BARK` + Scent Trail)**: Sniffs out buried **Desire Caches**, invisible **Velvet Sanctum** portals, and hidden **Shattered Memories** with a golden glowing scent ribbon.
   - **Dorothy (`BLINK` + `LACE WHIP`)**: Crosses broken bridge gaps and yanks distant brass levers.
4. **Destructible World Props & Velvet Sanctums**:
   - Smashable porcelain urns, candy-glass crates, and Winkie iron barrels drop Desire Fragments and Rose Petal heals.
   - Each Oz act hides **1–2 Velvet Sanctums** (secret side-arenas or puzzle vaults) rewarding rare **Silver-Shoe Charms** (e.g., *Echoing Heel*, *Gilded Lash*, *Lion's Poise*, *Clockwork Heart*).
5. **Side Quests ("Vile Requests")**:
   - 1–2 optional multi-step side quests per act given by named NPCs (e.g., *The Indebted Baker of Munchkinland*, *The Sleepless Botanist of Poppy Ridge*, *The Runaway Winkie Bell-Ringer*, *The Blind Spectacle-Maker of Emerald City*), tracked cleanly in the **Oz Grimoire**.

### B. Act-by-Act Runtime & Content Expansion
- **L1 Kansas Farmyard (Target: 8–12 min)**: Escalating storm tension barometer; rescue family heirloom locket from the Barn loft; herd stray chickens into the coop; interactive Aunt Em & Uncle Henry vignette choices; dramatic cyclone debris gauntlet into the lifting farmhouse.
- **L2 Munchkinland (Target: 25–35 min)**: 4 distinct interconnected zones (*Crash Square*, *Lollipop Guild Market*, *Whispering Cornfield Maze*, *Rusted Timber Ravine*); 2 side quests; 4 companion-gated puzzles; hidden Velvet Sanctum; full **2-Phase Lollipop Guild Marshal Boss** with floor AoE telegraphs & stagger bar.
- **L3 Deadly Poppy Field (Target: 20–25 min)**: Multi-tier scarlet canyon with drifting narcotic mist zones, wind-draft launch pads, cliffside scent-free bypasses, **Field Mouse Escort**, and the **Kalidah Chimera** ambush mini-boss.
- **L4 Winkie Castle (Target: 25–35 min)**: Multi-tier iron fortress (*Outer Causeway*, *Battlement Ramparts*, *Slave-Bell Courtyard*, *Cistern Sanctum*); Winged Monkey aerial dive-bomb indicators; **Golden Cap Relic** side-vault; full **3-Phase Wicked Witch of the West Boss** (Hex Rings → Monkey Swarm & Flame Spirals → Cistern Flood & Baum Melt Finale).
- **L5 Emerald City (Target: 20–30 min)**: Grand emerald boulevard with **Green-Spectacle Gatekeeper** (optional emerald-tint lens toggle); walkable **Tailor of Vices** physical salon & market district; Clockwork Sentinel trial; **3-Phase Wizard's Clockwork Spectacle Boss**; theatrical Curtain Reveal & Oscar Diggs conversation.
- **L6 Glinda's Quadling Court (Target: 15–20 min)**: Alabaster garden gauntlet (*Hammer-Head Bridge*, *China Country Porcelain Shrine*, *Reflecting Pool Mirror Puzzle*); Silver-Shoe Resonance Trial; Glinda's truth & iconic 3-heel-click departure.
- **L7 Kansas Homecoming (Target: 8–10 min)**: Playable sepia prairie finale with Aunt Em, Uncle Henry, & Toto; interactive **Porch Memory Album** reviewing unlocked Shattered Memories; unlocks **New Game+ ("The Velvet Road")** and **Chapter Select**.

---

## 4. The 12-Phase One-Shot Blueprint (`P1.3 → P12.3`)

Execute all 12 phases sequentially in one cohesive Gemini 4 Carbon run, validating with the 4 headless Godot 4.8 sims at key checkpoints and at the end:

| Phase | Codename | Core Deliverables |
| --- | --- | --- |
| **P1.3** | **Asset Audit & 2026 UI Shader Foundation** | Audit Nano Banana folder + `oz/assets/`; create `ui_velvet_card.gdshader`, `ui_gold_shimmer.gdshader`, and central typography/spacing tokens in `oz_theme_factory.gd`. |
| **P2.3** | **Live 3D Title Screen & Boot Flow** | Build a full 2026 live-3D animated Yellow Brick Road & Emerald Spire **Main Menu** (`Continue`, `New Game`, `Chapter Select`, `Tailor of Vices`, `Grimoire`, `Settings`, `Quit`) with Ken Burns act backdrops and spring animations. |
| **P3.3** | **2026 HUD, Dialogue & Radial Wheel Overhaul** | Elevate `play_hud.gd`, `dialogue_ui.gd`, `pause_menu.gd`, `shop_menu.gd`, and `grimoire_menu.gd` to shader-backed 2026 glass-velvet quality; add animated **Style Rank emblem**, **Boss Health/Stagger bar**, **Minimap/Waypoint Compass**, and **Whimsy pill**. |
| **P4.3** | **Combat Depth: Perfect Blink, Style Rank & Armament Upgrades** | Implement `Silver Mirage` perfect dodge slow-mo, `D→SOVEREIGN` Style Rank multiplier, hit-stop/camera-punch tuning, and Tier I→III Armament + Silver-Shoe Charm upgrades in `save_manager.gd` & `shop_menu.gd`. |
| **P5.3** | **Companion Synergy Puzzles & Destructible World Props** | Build reusable `WorldKit` puzzle actors: Crow-Bell Switches (Scarecrow), Rusted Chains (Tin Man), Bramble Gates (Lion), Scent Caches (Toto), Whip Levers (Dorothy), plus smashable porcelain/crate props dropping Desire & petals. |
| **P6.3** | **L1 Kansas & L7 Homecoming Deepening** | Expand L1 storm prologue (barn heirloom, storm barometer, richer family vignettes) and L7 interactive Porch Memory Gallery + **New Game+ / Chapter Select** unlock. |
| **P7.3** | **L2 Munchkinland 4-District Expansion & Marshal Boss** | Expand Munchkinland with companion puzzles, hidden **Velvet Sanctum**, 2 side quests (*Vile Requests*), destructibles, and a true **2-Phase Lollipop Guild Marshal** boss fight with AoE telegraphs. |
| **P8.3** | **L3 Poppy Canyon & Kalidah Chimera Encounter** | Add multi-tier canyon routes, updraft pads, dynamic poppy-mist visibility, Toto scent shortcuts, and the **Kalidah Chimera** mini-boss during the Mice Cart rescue. |
| **P9.3** | **L4 Winkie Fortress & 3-Phase Wicked Witch Boss** | Expand courtyard/ramparts, add Winged Monkey dive-bomb telegraphs, Golden Cap secret vault, and a dramatic **3-Phase Wicked Witch of the West** boss culminating in the Cistern water melt. |
| **P10.3** | **L5 Emerald Metropolis & 3-Phase Wizard Spectacle** | Add Green-Spectacle Gatekeeper toggle, physical walk-in **Tailor of Vices** salon, side quest, **3-Phase Clockwork Spectacle** encounter, and enhanced Curtain Reveal. |
| **P11.3** | **L6 Glinda's Gardens, China Shrine & Audio/VFX Polish** | Add China Country porcelain side-shrine, Reflecting Pool puzzle, adaptive per-act music/ambience layering (`audio_fx.gd`), spatial combat foley, and post-processing (`SSAO`, `Glow`, color grading). |
| **P12.3** | **Final Retail QA, Verification & Shipping Lock** | Run all 4 headless sims (`smoke_check`, `kansas_sim`, `play_sim`, `act34_sim`) + add `retail_p3_sim.gd` verifying puzzles, boss phases, charms, style rank, and NG+; update Obsidian logs; commit & push both repos. |

---

## 5. Ready-to-Paste One-Shot Prompt for Google Gemini 4 Carbon

When you switch to **Gemini 4 Carbon**, paste this exact prompt:

> **Execute the complete Phase `P1.3` through `P12.3` One-Shot Master Plan** documented in `/Users/dylanroberts/Documents/non-music/Dev/GitHub/realdyl/obsidian-oz/09 Production/Gemini 4 Carbon - P1.3 to P12.3 One-Shot Master Plan.md`.
>
> - Project repo: `/Users/dylanroberts/Documents/non-music/Dev/GitHub/realdyl/oz`
> - Obsidian vault: `/Users/dylanroberts/Documents/non-music/Dev/GitHub/realdyl/obsidian-oz`
> - Master image asset folder: `/Users/dylanroberts/Library/Mobile Documents/com~apple~CloudDocs/Creative Cloud Files/+ assets/Nano Banana/Oz`
>
> Work through **all 12 phases (`P1.3 → P12.3`)** thoroughly at maximum 2026 retail quality:
> 1. Elevate the GUI from 2018 flat panels to true 2026 shader-driven Obsidian-Plum, Burnished-Gold & Imperial-Emerald luxury across the live 3D Title Screen, Pause Menu, Tailor of Vices Boutique, Grimoire, Dialogue, and Gameplay HUD (strict safe-zone padding — zero text ever touching borders).
> 2. Deepen gameplay so every level (L1–L7) is longer, richer, and genuinely fun to play and worth buying: Companion Synergy Puzzles, Destructible Props, Velvet Sanctums, Side Quests (*Vile Requests*), Perfect Blink-Dodge, Style Rank, Silver-Shoe Charms, and true Multi-Phase Bosses.
> 3. Keep 100% L. Frank Baum 1900 public-domain canon (Silver Shoes, chalk-pale one-eyed Wicked Witch of the West — never MGM green skin or ruby slippers).
> 4. Verify **all 4 mandatory Godot 4.8 headless simulations** (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) exit `0` with zero GDScript parse/runtime errors, update Obsidian `Prototype Progress Log.md`, and commit & push both repos.
