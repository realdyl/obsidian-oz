---
title: Gemini 4 Carbon — P1.5 to P12.5 Master Plan (True 2026 Visual Fidelity, Gameplay Depth & Optional OpenXR VR)
type: production
status: active
tags:
  - oz
  - oz/production
  - oz/roadmap
  - oz/carbon
  - oz/2026-fidelity
  - oz/vr
updated: 2026-11-26
---

# *Oz: The Road Home* — Gemini 4 Carbon Master Plan (`P1.5 → P12.5`)

> **Core Diagnosis (2026-11-26):** Our GUI shell, gothic filigree frames, and Nano Banana Pro iconography already hit a **2026 retail standard**, while the **3D characters, environments, lighting/materials, and combat/movement feel currently read closer to ~2022 indie 3D**.
>
> **Mission of `P1.5 → P12.5`:** Close the gap from **2022 → True 2026 AA/AAA Stylized Dark-Fairytale Fidelity** (think *Alice: Madness Returns* remastered in 2026 on Godot 4.8 Forward+ Metal) across shaders, character silhouettes, cloth/hair secondary motion, volumetric lighting, 15-minute-per-act world density, vivid HUD micro-detail, and an optional **OpenXR VR mode** for Meta Quest 3 & Apple Vision Pro.

---

## 1. Visual Leap: Pushing Characters & Worlds from 2022 → 2026

| Pillar | Current (~2022) | `P1.5 → P12.5` Target (True 2026) |
| --- | --- | --- |
| **Skin, Fabric & Metal Shaders** | Flat `StandardMaterial3D` albedo + uniform roughness | Custom **Subsurface Scattering (SSS)** skin tint, **Anisotropic Silk/Velvet sheen** (Fresnel velvet rim on Dorothy's corset, Glinda's gown, Witch's lace), **Micro-scratched Brushed Tin PBR** on Tin Man, and **Procedural Fur-Shell Parallax** on Lion & Toto! |
| **Lighting, Atmosphere & Post** | Basic single DirectionalLight + mild fog | **Godot 4.8 Volumetric Fog + God-Rays**, **SSAO + SSIL** (real-time bounce light from the Yellow Brick Road onto Dorothy's gingham & legs!), **ACES Filmic Tonemapping + Chromatic Bloom**, and **Regional Color-Grading LUTs** (Kansas Silver-Gelatin Noir → Munchkinland Candy-Gloom → Poppy Crimson Haze → Emerald Cathedral Neon → Quadling Rose-Gold). |
| **Character Anatomy & Motion** | Procedural primitive limbs with simple sine gait | **Smooth Curved Lathe/Lofted Torso & Limb Meshes (`SurfaceTool`)** eliminating visible sphere seams at shoulders/knees, **Foot-IK Ground Planting** on stairs & slopes, **Velocity-Driven Cloth/Skirt Hem Shader**, **Dynamic Eye-Look-At** tracking the active speaker or nearest enemy, and **Micro-Breathe + Blink + Viseme Blend** in every cutscene. |
| **World Materiality & Ground** | Flat color-box ground planes | **Triplanar PBR Cobblestone & Yellow-Brick Relief Shader** (real normal-mapped mortar grooves + wet puddle speculars in Winkie Keep + glazed porcelain reflections in China Country), **Interactive Foliage Bending** for all 5 party members, and **3D Volumetric Cloud Decks + Distant Parallax Silhouettes**. |
| **GUI Vivid 2026 Micro-Detail** | Clean dark-velvet & gold panels | **Animated Specular Gold-Leaf Sheen** sweeping across unlocked medallions, **Live 3D Particle Embers** behind active Grimoire pages, **Dynamic Controller Glyph Auto-Swap** (PS5 DualSense `✕ ○ □ △` / Xbox `A B X Y` / Switch `B A Y X` / Keyboard `[E][F][C]`), and **Directional Damage Vignette + Hit-Confirm Reticle**! |

---

## 2. True 15-Minute-Per-Act Pacing & Mechanical Depth (`L1 → L7`)

Every single one of the **9 playable levels** gets upgraded to a rich, unhurried **15+ minute experience** with zero filler:
1. **L1 · Kansas (`15 min`)**: Expand pasture & creek culvert, add 3-hen herding minigame through the swinging coop gate, Storm Barometer & Barn Heirloom secrets, and interactive Cyclone wind-gust debris dodge.
2. **L2 · Munchkinland (`20–25 min`)**: Multi-terrace village markets, 2-phase Lollipop Guild Marshal with parryable telegraph, hidden subterranean Munchkin Debt Vault.
3. **L3a · Kalidah Wilds (`15–20 min`)**: Add **3rd Rope-and-Boulder Gorge Puzzle** (Scarecrow triggers crow-counterweight + Tin Man chops pine bridge), **Alpha Kalidah Matriarch** mini-boss with leap telegraphs, and **12+ Whimsies + River Raft Crossing** (Baum Ch. 8!).
4. **L3b · Deadly Poppy Field (`15–20 min`)**: Raised Clear-Air bluff terraces with 2 Field-Mouse Scout rescues, Wildcat Ambush before Mouse Queen coronation, and tactical Mice Cart escort.
5. **L4 · Winkie Iron Castle (`20–25 min`)**: Climbable outer ramparts, Winkie Forge interior, Winged Monkey rooftop dive telegraphs, and 3-phase Wicked Witch of the West boss arena.
6. **L5 · Emerald City (`20–25 min`)**: Walk-in Tailor of Vices couture showroom, `[G]` Green Spectacles optical-illusion treasure hunt across East/West Market Terraces, and live Hot-Air Balloon launch sequence.
7. **L6a · Fighting Trees & Dainty China Country (`15–20 min`)**: Expanded 4-Oak Orchard Gauntlet, climbable porcelain stile wall, delicate "Don't Break the Porcelain" optional bonus challenge in the Delft village, **Giant Forest Spider** multi-phase web-arena boss with broodling waves.
8. **L6b · Quadling Country (`15 min`)**: 3 Alabaster Reflecting Pool chime puzzles, Quadling Hammer-Heads ridge overlook (Baum Ch. 22!), Glinda's full party farewell & 3× `C` Silver Heel-Click ceremony.
9. **L7 · Kansas Homecoming (`15 min`)**: Interactive Porch Memory Gallery (view all unlocked Shattered Memories in 3D), Aunt Em & Uncle Henry reunion, and **`★ THE VELVET ROAD` (New Game+)** modifier unlock.

---

## 3. Optional OpenXR VR Support Roadmap (Meta Quest 3 / Apple Vision Pro)

Godot 4.8 ships with native **`OpenXR` (`XRServer`, `XROrigin3D`, `XRCamera3D`, `XRController3D`)**:
- **Phase VR-1 (Diorama Third-Person VR — Zero Motion Sickness!)**: Like *Moss* & *Astro Bot*, render Oz as a **living tabletop/life-size 3D diorama** where the player looks around with full 6-DoF head tracking while controlling Dorothy & the party with DualSense / Quest Touch / Vision Pro hand-pinch + gamepad!
- **Phase VR-2 (Optional First-Person Inspection & Boutique Mirror)**: Toggleable 1st-person view inside interiors & The Tailor of Vices with snap-turn (`30°` increments) and vignette comfort blinders.
- **Target Platforms**: **Meta Quest 3 / 3S** (native Android OpenXR APK export) and **Apple Vision Pro** (Godot 4.8 visionOS Metal/OpenXR compositor).

---

## 4. Phase Execution Order (`P1.5 → P12.5`)

- **P1.5**: Custom 2026 PBR Shaders (Velvet Fresnel, Skin SSS, Brushed Tin, Triplanar YBR Cobblestone, Wet Speculars).
- **P2.5**: Godot 4.8 Forward+ Lighting Overhaul (Volumetric Fog, SSAO, SSIL, ACES Tonemap, Regional LUTs).
- **P3.5**: Smooth Seamless Character Geometry (`SurfaceTool` lofted limbs/torsos, Foot-IK, Dynamic Eye-Look-At, Cloth Hem Shader).
- **P4.5**: Combat Feel & Juice Pass (Directional Hit-Stop, Weapon Trails, Parry Sparks, Multi-Whimsy Combo Popups, Controller Rumble/Haptics).
- **P5.5**: Vivid 2026 GUI Polish (Animated Gold Sheen, Dynamic PS5/Xbox/Switch/KB Glyph Auto-Detection, Grimoire Page-Turn & Particle Embers).
- **P6.5 → P10.5**: 15-Minute Deep Level Expansion & Set-Piece Polish across all 9 Acts (`L1` through `L7`, including River Raft in `L3a` and Hammer-Heads in `L6b`).
- **P11.5**: Optional OpenXR VR Diorama Rig (`systems/vr_manager.gd`) with automatic desktop fallback.
- **P12.5**: Full 5-Suite + VR/Controller Headless QA, Performance Profiling (60 FPS locked), Obsidian Sync & Signed Release.
