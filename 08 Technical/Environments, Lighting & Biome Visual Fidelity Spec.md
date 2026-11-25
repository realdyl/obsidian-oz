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
