---
title: Oz Tailored GUI & Visual Style Guide
type: spec
status: active
tags:
  - oz
  - oz/gui
  - oz/art
  - oz/style-guide
updated: 2026-11-23
---

# Oz: The Road Home — Tailored GUI & Visual Style Guide

Derived directly from the 7 approved Master Art & GUI Style References in `10 Prompt Libraries/Image Generation/Generated References/`. Every Godot 4 UI component (`OzThemeFactory`, `PlayHUD`, `OzGrimoire`, `ShopMenu`, `TitleScreen`, `PauseMenu`) must conform to these tokens and layout rules.

---

## 1. Canonical Color Palette (Sampled from Approved References)

| Token | Hex | RGB (Godot `Color`) | Usage |
|---|---|---|---|
| **Obsidian Plum (Backdrop)** | `#120914` | `Color(0.071, 0.035, 0.078)` | Main menu backdrop, modal overlays, deep vignette |
| **Velvet Parchment (Panels)** | `#281830` | `Color(0.157, 0.094, 0.188)` | Grimoire pages, boutique cards, objective plaques |
| **Smoked Glass (HUD Fill)** | `#160D1A` (88% α) | `Color(0.086, 0.051, 0.102, 0.88)` | Top-left objective card, bottom-left wheel base |
| **Hammered Antique Brass** | `#C49E5A` | `Color(0.769, 0.620, 0.353)` | Primary double-borders, filigree corners, gold medallions |
| **Burnished Gold Highlight** | `#E8C67A` | `Color(0.910, 0.776, 0.478)` | Active tab glow, selected item ring, `BUY & EQUIP` CTA |
| **Warm Ivory Serif** | `#EFE0C2` | `Color(0.937, 0.878, 0.761)` | Headings, button text, lore body copy |
| **Muted Parchment Subtext** | `#B8A89A` | `Color(0.722, 0.659, 0.604)` | Subtitles, key-hint footers (`[A] SELECT · [ESC] CLOSE`) |
| **Crimson Silver-Rose** | `#D93860` | `Color(0.851, 0.220, 0.376)` | Vitality rose buds, Allure gradient start, Rapture glow |
| **Silver-Mist Accent** | `#C8D4E6` | `Color(0.784, 0.831, 0.902)` | Silver Rose crest, active cursor bloom, Silver Shoes aura |
| **Kansas Sepia-Ash** | `#3A3530` / `#C4BDB2` | Monochrome override | Act 0 & L7 Kansas HUD/modal desaturation |

---

## 2. Signature Visual Motifs (Target Implementation Across P2.1–P6.1)

1. **Double-Bordered Antique Brass Frames**:
   - Every panel (`Objective`, `Grimoire`, `Boutique`, `Buttons`) uses a **1.5–2px outer `#C49E5A` frame** with a subtle inner inset hairline and corner filigree accents (never plain flat boxes).
2. **In-Game HUD (`ref_03_gameplay_hud.jpg`)**:
   - **Top-Left**: `CURRENT OBJECTIVE` smoked-glass plaque with gilded border & bulleted active goals.
   - **Top-Right**: **5 Crimson-Silver Rose Buds** on a horizontal thorny silver vine (Vitality), followed by an ornate **Magenta-to-Gold `ALLURE` bar** and a **Faceted Desire Fragment Diamond** counter.
   - **Bottom-Left**: **Circular 5-Portrait Party Medallion Wheel** — active Lead in the larger center gold ring, 4 companions orbiting in brass portrait rings with subtle key icons.
   - **Bottom-Right**: **3 Circular Brass Armament/Curio Slots (`1`, `2`, `3`)** for quick-cast visibility.
3. **The Oz Grimoire (`ref_01_grimoire_ui.jpg`)**:
   - **Open Two-Page Antique Book Spread** (`Quests`, `Companions`, `Armaments`, `Bestiary`, `Shattered Memories` as left-edge leather bookmark tabs, active tab lit with a silver-rose icon; left page = selectable portrait list; right page = ornate framed portrait + structured lore sections + gold bookmark ribbon).
4. **The Tailor of Vices Boutique (`ref_05_boutique_ui.jpg`)**:
   - **Left 42%**: Live 3D spotlight turntable on a dark obsidian-marble pedestal inlaid with concentric golden rings (`◄ ROTATE ►`), character title plaque at bottom.
   - **Right 58%**: Ornate boutique header + top category/character tabs + **2×3 Grid of Gilded Square Medallion Cards** + bottom **Selected Item Detail Box** with **segmented gold pip stat bars** (`VITALITY`, `ALLURE`, `RESISTANCE`) and a prominent hammered-gold **`BUY & EQUIP`** button.
5. **Main Menu (`ref_02_main_menu_ui.jpg`)**:
   - Full-screen ornate filigree & clockwork border frame, centered **Silver-Rose & Winged-Gear `OZ: THE ROAD HOME` Crest**, and 5 double-bordered stacked buttons with a floating silver-rose selection indicator.

---

## 3. Archived Reference Gallery
- ![[ref_01_grimoire_ui.jpg]]
- ![[ref_02_main_menu_ui.jpg]]
- ![[ref_03_gameplay_hud.jpg]]
- ![[ref_04_kansas_trio.jpg]]
- ![[ref_05_boutique_ui.jpg]]
- ![[ref_06_party_ensemble.jpg]]
- ![[ref_07_gothic_palace_couture.jpg]]
