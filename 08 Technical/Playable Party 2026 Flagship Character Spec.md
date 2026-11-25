---
title: Playable Party 2026 Flagship Character Spec
type: technical-spec
status: shipped
phase: P9.2
updated: 2026-11-25
tags:
  - oz
  - oz/technical
  - oz/character
  - oz/shaders
---

# Phase P9.2 — Playable Party 2026 Flagship Character Overhaul

Replicates Dorothy's Phase P8.2 flagship benchmark ([[Dorothy 2026 Flagship Character & Dynamic Sky Spec]]) across all four remaining playable party members — **The Scarecrow**, **The Tin Woodman**, **The Cowardly Lion**, and **Toto** — across gameplay (L1–L7) and *The Tailor of Vices* Boutique 3D turntable (`shop_menu.gd`).

---

## 1. The Scarecrow — *The Unbound Mind* (`actors/companions/scarecrow_visual.gd`, `scarecrow.gd`)
- **Custom Spatial Shaders**: Woven cross-hatch burlap (`_make_burlap_material`) and anisotropic obsidian crow-velvet (`_make_crow_velvet_material`).
- **Sculpted Anatomy & Secondary Physics**:
  - Contoured burlap sack head, beveled cross-stitched button eyes, triangular stitched nose, curved 7-segment cross-stitched grin, and bursting cheek/collar/wrist/ankle straw tufts.
  - **Physics-Swaying Bent Witch Hat (`_hat_piv` / `_hat_peak`)** with twisted hemp hatband, antique-brass spoked gear badge, and swept raven feather.
  - **Dynamic Split Swallowtail Coat (`_coat_piv`)**, articulated 4-finger + thumb hands gripping his gnarled walking staff with a **swinging brass skeleton key (`_key_piv`)**, and curled-toe lace-up leather boots.
- **3 Bespoke Couture Builds (`set_outfit`) + Real Combat Perks**:
  1. `scarecrow_classic` (*Cornfield Straw* — `char_01_scarecrow.jpg`): Patchwork ochre burlap, crossed hemp rope harness, leather waist pouch.
  2. `scarecrow_leather` (*Burlap & Leather*): Oiled espresso-leather coat & straps (`+0.9m` wider Crow Scatter radius).
  3. `scarecrow_obsidian` (*Obsidian Crowmaster* — `scarecrow_obsidian.png`): Midnight velvet cloak with 14-feather raven mantle, glowing faceted amethyst-violet winged brooch, feather-trimmed coat hems, and amethyst button eyes (`3.8s` Confusion + `+3` bonus Caw damage).
- **Dexterity & Whimsy**: Turn banking, airborne loose-limbed straw float pose, landing squash, dramatic Crow-Summon Caw pose (`play_caw`), and automatic / `[V]` **Hat-Tip & Staff-Lean** flourish (`play_flourish`).

---

## 2. The Tin Woodman — *The Clockwork Heart* (`actors/companions/tinman_visual.gd`, `tinman.gd`)
- **Custom Spatial Shader**: Anisotropic brushed tin & oxidized rust patina (`_make_tin_material`).
- **Sculpted Automaton Anatomy & Living Clockwork**:
  - Contoured steel helmeted head with brow visor, glowing amber-gold clockwork lens eyes in brass aperture rings, angular riveted nose, **hinged metallic jaw (`_jaw`)**, and angled oil-funnel helm with spout, loop handle, and brass spikes.
  - Domed boiler cuirass housing a **beating, pulsing crimson Clockwork Heart (`_heart_piv`)** inside a gilded filigree cage, twin back brass steam boiler tanks & angled exhaust pipes, and **continuously spinning brass clockwork gears (`_gears`)** at his waist, elbows, and knees.
  - Articulated 4-finger + thumb steel gauntlets, fluted greaves, sculpted armored sabaton boots (zero boxy feet), and a curved double-bevel crescent Woodsman Axe with rear armor-piercing pick.
- **2 Bespoke Couture Builds (`set_outfit`) + Real Combat Perks**:
  1. `tinman_classic` (*Polished Tin* — `char_02_tin_woodman.jpg`): Mirror-buffed silver-tin plate with glowing ruby heart inside brass cage.
  2. `tinman_velvet` (*Chrome & Crimson Velvet* — `tinman_royal.png`): Dark gunmetal-chrome mirror armor draped with a fringed crimson-velvet diagonal sash & hip tail (`_sash_tail`) and an exposed golden-brass anatomical clockwork heart (`+10` Axe Cleave damage + crimson axe trail).
- **Dexterity & Whimsy**: Weighty armored march, turn banking, **2-Stage Alternating Axe Cleave (`play_axe_swing(1 | 2)` — Overhead Heavy Chop & Horizontal Reverse Sweeping Cleave)**, and automatic / `[V]` **Clockwork Heart-Tap** flourish (`play_flourish`).

---

## 3. The Cowardly Lion — *The Burden of Courage* (`actors/companions/lion_visual.gd`, `lion.gd`)
- **Custom Spatial Shader**: Soft directional tawny feline fur (`_make_fur_material`).
- **Sculpted Feline Anatomy & Secondary Physics**:
  - Deep muscular ribcage, athletic lumbar waist, haunches, **22-tuft 2-tier windswept mane (`_mane_piv`) + twin braided mane locks with antique-gold beads**, blinking amber-gold eyes with slit pupils & twin catchlights, sculpted whiskers, twitching ears (`_ear_l/r`), articulated **fanged lower jaw (`_jaw`) with pink tongue**, 2-segment feline legs with **4-toe ivory-clawed paws**, and a **2-segment physics-swaying S-tail (`_tail_base` → `_tail_tip`)**.
- **2 Bespoke Couture Builds (`set_outfit`) + Real Combat Perks**:
  1. `lion_classic` (*Golden Mane* — `char_04_cowardly_lion.jpg`): Dark-leather harness + swinging 8-point Gold Courage Medal on crimson ribbon.
  2. `lion_primal` (*Primal Gold Harness* — `lion_primal.png`): Spiked gold crown gorget, embossed golden lion shoulder pauldrons, giant glowing faceted crimson ruby chest medallion, and golden-rimmed war-mane (`+1.2m` wider Roar Fear shockwave & `2.8s` fear duration).
- **Dexterity & Whimsy**: Fluid feline stride with spine flex, turn banking, airborne pounce pose, roaring mane-flare + fanged jaw wide-open shockwave (`play_roar`), curled sleeping pose, and automatic / `[V]` **Mane-Shake & Ear-Twitch** flourish (`play_flourish`).

---

## 4. Toto — *The Faithful Companion* (`actors/companions/toto_companion.gd`)
- **Custom Spatial Shader**: Shaggy brindle Cairn Terrier fur shader (`_make_brindle_material`, desaturates cleanly for Kansas L1/L7).
- **Sculpted Cairn Terrier Anatomy**:
  - Contoured terrier body, bushy eyebrow & cheek whisker ruffs, glossy obsidian nose, warm amber eyes with twin catchlights & **blinking eyelids**, **perking/twitching pointed ears (`ear_l/r`)**, feathered upright tail, and 3-toe sculpted paws.
- **2 Bespoke Couture Builds (`set_outfit` / `build_dog_visual`) + Real Perks**:
  1. `toto_classic` (*Cairn Terrier* — `char_06_toto.jpg`): Stitched dark-leather collar + 5-point sterling silver star charm.
  2. `toto_silver_collar` (*Silver-Spiked Collar* — `toto_spiked.png`): Burnished sterling-silver collar studded with **8 gleaming silver spikes** & oversized star pendant (`+1.4m` wider sonic bark aura).
- **Dexterity, Whimsy & Live Boutique Turntable**: Turn banking, happy sonic bark hop (`play_bark`), automatic / `[V]` **Playful Terrier Play-Bow & Head-Tilt** flourish (`play_flourish`), and live animated preview on *The Tailor of Vices* turntable (`shop_menu.gd`).
