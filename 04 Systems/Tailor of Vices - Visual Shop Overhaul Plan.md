---
title: Tailor of Vices - Visual Shop Overhaul Plan
type: system
status: active
tags:
  - oz
  - oz/system
  - oz/ui
  - oz/shop
aliases:
  - Shop Visual Overhaul
updated: 2026-11-23
---

# The Tailor of Vices — Visual Shop Overhaul Plan (Beyond Skeleton)

The Phase P10 skeleton proved the **5-character tab structure, live Desire Fragment economy, and real-time 3D character application**. To elevate **The Tailor of Vices** to retail AAA/AA quality (matching *Alice: Madness Returns* dress-select theater + *Thrive* modular Godot 4 UI):

## 1. Live 3D Turntable Preview (`SubViewportContainer`)
- Replace flat color swatches with a **split-screen 3D Boutique Stage** on the left side of the Shop modal:
  - Embedded Godot 4 `SubViewport` lit with warm velvet-gold key light + crimson rim light.
  - Displays the **actual sculpted 3D character** (`Dorothy`, `Scarecrow`, `Tin Man`, `Lion`, or `Toto`) standing on a rotating gilded marble pedestal (`drag to spin` + smooth idle breathing).
  - Hovering over *any* outfit or weapon immediately **previews it live on the 3D turntable model** before purchase!

## 2. Custom Illustrated / Procedural Vector Item Icons (`art/icons/shop/`)
- Replace every color block with crisp, bespoke **64×64 SVG/PNG retail icons** framed in gilded-filigree cards:
  - **Outfits**: Silhouette dress/coat illustrations (Prairie Gingham Dress, Crimson Velvet Corset, Silver-Lace Sovereign Gown, Burlap & Leather Harness, Chrome & Velvet Plate, Primal Gold Mane Armor, Silver-Spiked Collar).
  - **Weapons & Armaments**: Coiled Crimson Lace Whip, Silk Ribbon Spool, Ornate Glass Perfume Atomizer, Interlocking Gilded Chain, Tempered Silver-Edge Axe.

## 3. Stat Delta & Comparison Strip
- Display clean green/gold **Stat Comparison Bars** (`Allure Multiplier`, `Blink Cooldown`, `Combat Damage`, `Intimidation Radius`) showing current vs. previewed item deltas.

## 4. Boutique Presentation Polish
- Velvet curtain-draw open transition, chime SFX on purchase/equip, and "Try On" vs "Buy & Equip" interaction flow.

---

## Related
- [[Outfit Shop]]
- [[Retail Completeness Audit & Phase P6-P12 Roadmap]]
- [[Reference Benchmarks - Thrive & Alice Madness Returns]]
