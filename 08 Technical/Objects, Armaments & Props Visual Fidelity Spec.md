---
title: Objects, Armaments & Props Visual Fidelity Spec
type: spec
status: active
tags:
  - oz
  - oz/props
  - oz/art
  - oz/3d
updated: 2026-11-24
---

# Objects, Armaments & Props Visual Fidelity Spec

Maps approved prop references in `10 Prompt Libraries/Image Generation/Generated References/Objects/` into exact 3D hero prop builds (`systems/world_kit.gd`) and 2D inventory/Grimoire icons (`oz/assets/art/icons/`).

---

## 1. Core Story Quest Objects (5/5 Archived)

| Quest Object | Reference Image | Signature 3D Prop & GUI Details |
|---|---|---|
| **The Silver Shoes (Baum Canon)** | `Objects/Quest/obj_03_silver_shoes.jpg` | Mirror-polished sterling silver pointed-toe Victorian heeled shoes with ornate filigree instep buckles & starlight shimmer; cropped to `icons/silver_shoes.png` for Oz Grimoire Quests tab. |
| **Toto's Wicker Basket** | `Objects/Quest/obj_04_wicker_basket.jpg` | Hand-woven wicker picnic basket with twin slightly-ajar hinged lids, braided arched handle, and folded gingham cloth lining; cropped to `icons/wicker_basket.png`. |
| **Tin Man's Brass Oil Can** | `Objects/Quest/obj_02_oil_can.jpg` | Ribbed tapered antique-brass oil can with curved pouring spout, angled filler cap, and thumb-ring handle perched atop a mossy forest tree stump. |
| **Field-Mouse Wooden Cart** | `Objects/Quest/obj_05_field_mouse_cart.jpg` | Slatted oak farm cart with iron corner straps, spoked wooden wheels with iron rims, and twin front harness shafts with leather yoke straps. |
| **Water Cistern & Oak Bucket** | `Objects/Quest/obj_01_water_cistern_bucket.jpg` | Riveted iron-strapped stone courtyard cistern overflowing water directly into a heavy iron-banded oak water bucket sitting beside the rim. |

---

## 2. Pending Object Batches (Sections 2–4 of Prompt Library 04)
- Kinky Armaments (Lace Whip, Silk Bindings, Hypnotic Perfume, Gilded Chain)
- Shattered Memories (Locket, Weather Ledger, Cracked Mask, Debt Book, Green Spectacles)
- World Interactive Props (Desire Chest, Porcelain Urn, Fence Wind Chimes, Street Lantern)


---

## 2. Kinky Armaments & Combat Tools (`[C]` / `[Z/X]`) — Phase P10.1
Archived in `10 Prompt Libraries/Image Generation/Generated References/Objects/Armaments/`:

| Reference File | In-Game Armament | GUI Icon (`oz/assets/art/icons/`) | Visual & 3D VFX Blueprint |
| :--- | :--- | :--- | :--- |
| `arm_01_crimson_whip.jpg` | **The Lace Whip** (Slot 1 · Bind & Yank) | `arm_whip.png` | Deep burgundy-crimson hand-braided silk bullwhip, engraved antique-brass floral rose hilt with ruby pommel, and a glowing faceted ruby-crystal lash tip caged in gold filigree (`combat_fx.gd:whip_lash` → burgundy-crimson lash + ruby & gold impact burst). |
| `arm_02_poppy_atomizer.jpg` | **Hypnotic Perfume** (Slot 3 · Enamored Mist) | `arm_atomizer.png` | Faceted amethyst-violet crystal perfume bottle encased in gilded brass rose-vine filigree with crimson mesh squeeze bulb & tassel spraying violet-rose narcotic mist (`combat_fx.gd:perfume_cloud` → dual-shell amethyst-violet & rose-pink shimmer cloud). |
| `arm_03_gilded_chain.jpg` | **The Gilded Chain** (Slot 4 · Damage Tether) | `arm_chain.png` | Heavy hammered antique-gold links ending in twin engraved rose-copper shackle clasps with knurled locking screws (`combat_fx.gd:gilded_chain` → hammered gold tether + twin rose-copper shackle anchor flashes). |
| `arm_04_silk_ribbon.jpg` | **Silk Bindings** (Slot 2 · Multi-Cocoon) | `arm_ribbon.png` | Turned wooden tailor's spool wound with iridescent dusty-rose & lavender silk ribbon embroidered with glowing golden Celtic/shibari knotwork (`combat_fx.gd:silk_cocoon` → dusty-rose silk rings + orbiting golden knotwork halo). |

### GUI Integration
- **Main HUD (`oz/ui/play_hud.gd`)**: Added a gilded 24×24 framed `_armament_icon` thumbnail right beside the `[C]` Armament HUD prompt that swaps dynamically in `set_active_armament()` as the player cycles armaments with `[Z/X]`.
- **Oz Grimoire (`oz/ui/grimoire_menu.gd`)**: Wired all 4 painted icons into `ARMAMENT_LORE` so opening `[J]` → `ARMAMENTS` frames each weapon's artwork in antique brass.


---

## 3. Shattered Memories (Codex Lore Collectibles) — Phase P11.1
Archived in `10 Prompt Libraries/Image Generation/Generated References/Objects/Memories/`:

| Reference File | `MEMORY_CATALOG` Key | Grimoire Icon (`oz/assets/art/icons/`) | Visual & Narrative Detail |
| :--- | :--- | :--- | :--- |
| `mem_01_cyclone_ledger.jpg` | `kansas_barn_diary` | `mem_cyclone_ledger.png` | Open oil-stained 1899 barometer & weather observations ledger with hand-drawn storm pressure charts, inkwell, and axle grease tin. |
| `mem_02_aunt_em_locket.jpg` | `kansas_locket` | `mem_aunt_em_locket.png` | Open oval tarnished pewter/silver locket holding a faded sepia daguerreotype of Aunt Em standing before the Kansas prairie homestead. |
| `mem_03_guild_ledger.jpg` | `munchkin_silver_ledger` | `mem_guild_ledger.png` | Silver-clasped dark-leather bound Registry of Names lying open on plum velvet beside a quill pen and silver inkwell. |
| `mem_04_porcelain_mask.jpg` | `munchkin_porcelain_mask` | `mem_porcelain_mask.png` | Uncanny pastel-painted smiling porcelain Munchkin mask fractured down the left eye to reveal intricate brass clockwork gears and steel clock hands. |
| `mem_05_emerald_spectacles.jpg` | `emerald_spectacles` | `mem_emerald_spectacles.png` | Round brass-framed green-tinted glass spectacles with mechanical locking screws on the temples, resting on plum velvet beside a brass case and oil lamp. |

### Oz Grimoire Milestone (`oz/ui/grimoire_menu.gd`)
- **All 5 Tabs of the Oz Grimoire (`[J]`)** — *Quests, Companions, Armaments, Bestiary, and Shattered Memories* — now render 100% real hand-painted 256×256 artwork framed in antique brass!
