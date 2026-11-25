# Gemini 4 Carbon — 2026 Vivid GUI & Shader Overhaul Plan

> **Purpose**: High-leverage execution blueprint prepared specifically for **Gemini 4 Carbon** to elevate *Oz: The Road Home* from a verified functional prototype with 100% painted art assets into a **vivid, tactile, 2026 AAA-grade dark-storybook experience** (zero regressions to the 4 mandatory headless Godot 4.8 simulations).

---

## 1. Completed Asset Inventory Ready for Gemini 4 Carbon
Every visual library in `obsidian-oz/10 Prompt Libraries/Image Generation/Generated References/` is **100% archived** and wired into `realdyl/oz/assets/`:
- **Character Portraits (`oz/assets/art/portraits/`)**: 16 painted 256×256 busts (Playable Party: `dorothy`, `scarecrow`, `tinman`, `lion`, `toto`; Story NPCs: `aunt_em`, `uncle_henry`, `locasta`, `glinda`, `wizard`; Enemies/Bosses: `wicked_witch`, `munchkin_enforcer`, `marshal`, `living_tree`, `winged_monkey`, `oz_hologram`), upgraded with studio busts in Phase P4.2.
- **Boutique Couture Icons (`oz/assets/art/icons/shop/`)**: All 13 `SHOP_CATALOG` items mapped to painted 256×256 product renders (`ShopItemIcon`).
- **Quest, Armament & Memory Icons (`oz/assets/art/icons/`)**: `silver_shoes`, `wicker_basket`, `desire_chest`, 4 Kinky Armaments (`arm_whip`, `arm_atomizer`, `arm_chain`, `arm_ribbon`), and all 5 Shattered Memories (`mem_cyclone_ledger`, `mem_aunt_em_locket`, `mem_guild_ledger`, `mem_porcelain_mask`, `mem_emerald_spectacles`).
- **Act Backdrops & Title Cards (`oz/assets/art/scenes/`)**: 9 full-bleed 1280×720 16:9 widescreen paintings (`title_hero_oz`, `title_kansas_cyclone`, `kansas_calm`, `munchkinland`, `poppy_field`, `winkie_castle`, `emerald_city`, `glinda_court`, `kansas_homecoming`).
- **Seamless Triplanar PBR Surface Textures (`oz/assets/textures/`)**: Best-of-batch 512×512 seamless tiles (`yellow_brick`, `kansas_wood`, `winkie_basalt`, `emerald_marble`, `quadling_marble`, `caustic_water`).
- **GUI Master References (`Generated References/GUI/`)**: 7 approved dark-velvet & antique-brass GUI mockups (`ref_01_grimoire_ui.jpg` through `ref_07_dialogue_ui.jpg`).

---

## 2. Priority Targets for Gemini 4 Carbon (Phases P7.2 – P12.2)

### A. 2026 Vivid Shader-Driven GUI Layer (`oz/ui/`)
1. **Custom CanvasItem Shaders (`oz/ui/shaders/`)**:
   - **Gilded Filigree Metallic Sheen**: Animated subtle gold specular sweep across `OrnateFrame` borders (`oz/ui/widgets/ornate_frame.gd`) and active buttons on hover/focus.
   - **Velvet & Frosted Glass Backdrop (`backdrop_blur.gdshader`)**: True screen-space frosted plum-velvet blur with subtle warm vignette behind `shop_menu.gd`, `grimoire_menu.gd`, and `pause_menu.gd`.
   - **Rose Vitality Liquid Shader (`rose_vitality_bar.gd`)**: Animated crimson-rose fluid shimmer, specular glass tube highlight, and thorn-pulse glow when HP drops below 30% or Rapture Mode (`[H]`) activates.
2. **Tactile Micro-Interactions & Spring Animations**:
   - Smooth spring-scale hover/press feedback (`Tween.TRANS_BACK`) on every Boutique card, Grimoire bookmark tab, and Party Medallion Wheel button (`play_hud.gd`).
   - Animated page-turn slide/fade transition in `grimoire_menu.gd` when switching between the 5 tabs (`[Q/E]` or `[1-5]`).
   - Circular Party Medallion Wheel (`play_hud.gd`) radial pop-out with golden tether lines, active-lead crown halo, and animated portrait ring glow.
3. **Dedicated Main Title Screen (`oz/ui/shell/main_title.gd` — Optional Boot Mode)**:
   - Full-bleed `title_hero_oz.jpg` with slow Ken Burns parallax drift, floating golden poppy/emerald dust motes, gilded serif emblem *"OZ: THE ROAD HOME"*, and `NEW JOURNEY / CONTINUE / SETTINGS / QUIT` controls (preserving instant headless sim compatibility).

### B. 2026 Vivid 3D Lighting, Color Grading & Material Richness (`oz/systems/world_kit.gd`)
1. **Per-Act ACES Filmic Tonemapping, Volumetric Fog & Glow Presets**:
   - Match each of the 7 Acts' `WorldEnvironment` precisely to its archived `scene_01a`–`scene_07` lighting style sheet (sepia film-grain & contrast curve in Kansas; warm golden-hour rim bloom + rose mist in Munchkinland & Poppy Field; wet-stone specular rain reflections + lightning flashes in Winkie Castle; emerald volumetric searchlights in Emerald City; sunlit rose-gold caustics in Glinda's Court).
2. **Procedural Normal & Roughness Maps from PBR Tiles**:
   - Auto-generate Sobel normal & roughness textures in `WorldKit.load_pbr_tex()` (cached at runtime) so `yellow_brick.jpg`, `kansas_wood.jpg`, `winkie_basalt.jpg`, `emerald_marble.jpg`, and `quadling_marble.jpg` catch dramatic directional rim-lighting and specular highlights in Godot 4.8!

### C. Verification Guardrail (Non-Negotiable)
Every Gemini 4 Carbon iteration MUST pass all 4 headless Godot 4.8 simulations (`smoke_check.gd`, `kansas_sim.gd`, `play_sim.gd`, `act34_sim.gd`) with exit code `0` and zero script errors, and commit/push both `realdyl/oz` and `realdyl/obsidian-oz`.


---

## 3. Execution Status — Phase P7.2 Shipped (2026-11-24)

### Shipped in `realdyl/oz` (Phase P7.2)
1. **2026 GPU CanvasItem Shader Suite (`oz/ui/shaders/`)**:
   - `frosted_velvet_backdrop.gdshader`: Obsidian-plum damask diamond weave, radial edge vignette, drifting golden/silver dust motes, and Kansas film-noir mix parameter behind `GrimoireMenu`, `ShopMenu`, `PauseMenu`, and `DialogueUI`.
   - `circle_medallion.gdshader`: Anti-aliased circular portrait & armament mask with convex glass-dome sheen, animated metallic brass rim sweep, locked silhouette desaturation, Kansas greyscale toggle, and radial clock-wipe cooldown overlay.
   - `rapture_vignette.gdshader`: *Alice*-class Rapture / Hysteria screen-perimeter thorny crimson-rose & molten-gold veins with unobstructed center combat clarity.
2. **True `ref_03_gameplay_hud.jpg` HUD Architecture (`oz/ui/widgets/` & `oz/ui/play_hud.gd`)**:
   - **Bottom-Left `PartyMedallionWheel` (`party_medallion_wheel.gd`)**: Smoked-velvet & double-brass circular dial with 70×70 center Lead portrait, 4 orbiting 44×44 companion portrait medallions, golden tether spokes, 4 bond pips, spring-elastic Lead swap animation, and attached `[F]` kit verb pill.
   - **Bottom-Right `ArmamentDock` (`armament_dock.gd`)**: 4 circular brass-framed painted Armament medallions (`1`–`4` / `[C]`) with spring selection scale, live radial cooldown wipe, and pulsing `✦ [H] RAPTURE READY` badge.
   - **Top-Right Frameless Vitality & Allure Cluster (`rose_vitality_bar.gd`, `allure_gauge.gd`)**: 5 multi-layered Crimson-Silver Roses on a curved thorny silver vine with scattering petal physics on damage + crested magenta-to-molten-gold `ALLURE` liquid shimmer bar + faceted glowing `DESIRE` crystal plaque with rolling counter.
   - **Exploration Restraint & A11y High-Contrast Hook**: Smoothly dims combat chrome slightly during calm exploration and snaps to `1.0` opacity on threat or when `SaveManager.high_contrast_hud` is enabled.
3. **Grimoire, Boutique, Dialogue & Core Logic Polish**:
   - **`grimoire_menu.gd`**: Framed portrait icons on left-page rows, custom-drawn draping golden silk bookmark ribbon (`BookmarkRibbon`), smooth page-turn fade tween, and `page_turn` / `ui_hover` SFX.
   - **`shop_menu.gd`**: Mouse-wheel camera zoom (`2.25m–4.15m`) on the 3D turntable, `+XX%` stat delta readouts beside the 12-pip bars, `OrnateFrame` detail card, and hover audio feedback.
   - **`save_manager.gd` & `player_controller.gd`**: Fixed save/load slot persistence for `owned_items`, `equipped_outfits`, and `difficulty` (with auto-reapply across level transitions), and wired real Couture gameplay perks (`dorothy_velvet` `+25%` Allure, `dorothy_sovereign` `+40%` Allure & `-15%` Blink cooldown, `dorothy_whip_plus` `+8` Lace Whip damage & `13.5m` reach).

### Next Target: Phase P8.2 → P12.2 Roadmap
- **Phase P8.2**: Dedicated Boot / Title Screen (`main_title.gd` with Ken Burns hero stage, drifting poppy/emerald embers, Continue / New Journey / Load Slot / Settings / Credits) + Diegetic Wicker Basket Quick-Inspect Overlay.
- **Phase P9.2**: Procedural Runtime Sobel Normal & Roughness Map Generation (`WorldKit.load_pbr_tex`) + Per-Act ACES Filmic Tonemapping, Volumetric Fog & Selective Bloom (`scene_01a`–`scene_07` parity).
- **Phase P10.2**: Multi-Phase Boss HUD Stagger/Telegraph Polish + Lock-On Clockwork-Rose Reticle (`[R]` / `MMB`).
- **Phase P11.2**: EnvironmentalCompanion Puzzle Polish & Velvet Sanctum Challenge Trials.
- **Phase P12.2**: Adaptive Multi-Stem Audio Crossfader, Dynamic Gamepad/Steam Deck Glyphs & 60 FPS Shipping Audit.
