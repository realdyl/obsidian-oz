# Environments, Lighting & Biome Visual Fidelity Spec

> **Purpose**: Maps every approved widescreen environment, lighting style sheet, and seamless material reference from `10 Prompt Libraries/Image Generation/Generated References/Environments/` directly to Godot 4.8 `WorldEnvironment` presets, shaders, and Level Transition chapter backdrops (`oz/systems/level_transition.gd`, `oz/assets/art/scenes/`).

---

## 1. Act-by-Act Scene & Lighting Style Sheets (`16:9`) — Phase P1.2
Archived in `10 Prompt Libraries/Image Generation/Generated References/Environments/Scenes/`:

| Reference File | Act / Scene | Game Backdrop (`oz/assets/art/scenes/`) | Lighting, Sky & Atmosphere Target |
| :--- | :--- | :--- | :--- |
| `scene_01a_kansas_calm.jpg` | **L1 Kansas Farmstead (Calm)** | `kansas_calm.jpg` | Sepia-monochrome overcast prairie daylight, soft flat dust haze, weathered timber contrast, zero color saturation. |
| `scene_01c_kansas_cyclone_approach.jpg` | **L1 Kansas Cyclone Approach** | — | Darkening charcoal supercell wall cloud & distant twister funnel forming behind the Gale farmhouse and windmill. |
| `scene_01b_kansas_cyclone_strike.jpg` | **L1 Kansas Cyclone Strike** | — | High-contrast monochrome storm lighting, jagged lightning forks, swirling debris planks, battered barn roof. |
| `scene_02_munchkinland.jpg` | **L2 Munchkinland Twilight Valley** | `munchkinland.jpg` | Enchanted lavender-rose dusk sky with warm golden cottage windows, glowing Yellow Brick Road, golden cornfield, and distant luminous Emerald City spires. |
| `scene_03_poppy_field.jpg` | **L3 Deadly Poppy Field** | `poppy_field.jpg` | Endless scarlet poppy meadow bathed in low-lying rose-crimson narcotic mist under a deep plum-violet twilight sky with the Emerald City glowing ahead. |
| `scene_04_winkie_castle.jpg` | **L4 Winkie Iron Castle Courtyard** | `winkie_castle.jpg` | Rain-slick gothic basalt flagstones, bruised violet lightning sky, warm flickering orange standing braziers contrasting cold iron-blue cistern water. |
| `scene_05_emerald_city.jpg` | **L5 Emerald City Grand Boulevard** | `emerald_city.jpg` | Art-Deco emerald-marble & gilded-brass avenue, glowing tiered fountains, mirror-polished emerald street reflections, towering crystalline spires at dusk. |
| `scene_06_glinda_court.jpg` | **L6 Glinda's Quadling Court** | `glinda_court.jpg` | Radiant golden-hour rose-marble colonnades, lotus reflecting pools with warm rose-gold water lanterns, open-work ruby-rose dome crowned by a golden starburst. |
| `scene_07_kansas_homecoming.jpg` | **L7 Kansas Homecoming** | `kansas_homecoming.jpg` | Post-storm rain-puddled sepia Kansas farmyard, clearing prairie sky, Aunt Em & Uncle Henry waiting on the porch, Oscar Diggs's tiny hot-air balloon drifting high overhead. |

### Level Transition Integration (`oz/systems/level_transition.gd`)
- Added a full-bleed `TextureRect` (`_backdrop`, `STRETCH_KEEP_ASPECT_COVERED`) beneath the translucent plum veil (`alpha = 0.56`) and spinning antique brass hourglass.
- `_pick_backdrop_for(title)` automatically maps every Act transition title to its matching 1280×720 painted scene key art in `res://assets/art/scenes/`.


---

## 2. Seamless Tileable PBR Surface Textures (`1:1`, `--tile`) — Phase P2.2
Archived in `10 Prompt Libraries/Image Generation/Generated References/Environments/Textures/` and exported as 512×512 seamless tiles into `oz/assets/textures/`:

| Reference File | Runtime Texture (`oz/assets/textures/`) | Live 3D Integration (`oz/systems/world_kit.gd`) |
| :--- | :--- | :--- |
| `tex_01_kansas_wood.jpg` | `kansas_wood.jpg` | Triplanar-mapped onto monochrome Kansas Gale Farmhouse & Barn exteriors (`dress_cottage_exterior`) in L1 & L7. |
| `tex_02_quadling_marble.jpg` | `quadling_marble.jpg` | Triplanar-mapped onto Glinda's 8-column Pavilion marble dais and rose-marble walkways (`dress_glinda_court`) in L6. |
| `tex_03_winkie_basalt.jpg` | `winkie_basalt.jpg` | Triplanar-mapped onto the octagonal Winkie Castle Courtyard Water Cistern masonry (`build_water_cistern`) in L4. |
| `tex_04_yellow_brick.jpg` | `yellow_brick.jpg` | Triplanar-mapped onto the continuous Yellow Brick Road mosaic paving strip and golden curb rails (`dress_ybr_spine`) across Oz. |
| `tex_05_caustic_water.jpg` | `caustic_water.jpg` | Triplanar-mapped with subtle turquoise glow onto Glinda's Court lotus reflecting pools (`dress_glinda_court`) in L6. |
| `tex_06_emerald_marble.jpg` | `emerald_marble.jpg` | Triplanar-mapped onto the Art-Deco Emerald City Palace forecourt boulevard plaza (`build_emerald_palace_facade`) in L5. |


### Batch 1 vs. Batch 2 A/B Texture Selection (Phase P5.2)
All 5 Batch-2 texture variants archived in `Generated References/Environments/Textures/Batch2/`. Art-direction winners promoted into `oz/assets/textures/`:
- **Yellow Brick Road (`yellow_brick.jpg`)**: **Batch 2 Winner** (`tex_b2_yellow_brick.jpg`) — tighter concentric radial sun-lotus cobble medallions with cleaner 3rd-person road readability.
- **Emerald City Marble (`emerald_marble.jpg`)**: **Batch 2 Winner** (`tex_b2_emerald_marble.jpg`) — richer deep emerald veining and tighter symmetrical Art-Deco gold lattice.
- **Quadling Rose Marble (`quadling_marble.jpg`)**: **Batch 2 Winner** (`tex_b2_quadling_marble.jpg`) — crisper blush-rose marble contrast and octagonal filigree medallions.
- **Kansas Barnwood (`kansas_wood.jpg`)**: **Batch 2 Winner** (`tex_b2_kansas_wood.jpg`) — more uniform plank width and cleaner vertical tiling rhythm across farmhouse/barn walls.
- **Winkie Basalt (`winkie_basalt.jpg`)**: **Batch 1 Winner Kept** (`tex_03_winkie_basalt.jpg`) — symmetric riveted iron cross-strapping avoids the asymmetric corner iron plate repetition in Batch 2.


---

## 3. Act Title Cards & Loading Screens (`16:9`) — Phase P6.2
Archived in `10 Prompt Libraries/Image Generation/Generated References/Environments/TitleCards/`:
- `title_01_kansas_cyclone.jpg` → `oz/assets/art/scenes/title_kansas_cyclone.jpg` (cyclone/storm transitions)
- `title_02_munchkinland.jpg` → promoted to `oz/assets/art/scenes/munchkinland.jpg` (spiral Yellow Brick Plaza + peppermint spires)
- `title_03_poppy_field.jpg` → `oz/assets/art/scenes/title_hero_oz.jpg` (Main Title Screen & default hero transition key art)
- `title_04_emerald_gates.jpg` → promoted to `oz/assets/art/scenes/emerald_city.jpg` (Art-Deco emerald gates + lion-head fountains)
