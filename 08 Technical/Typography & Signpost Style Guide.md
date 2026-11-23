---
title: Typography & Signpost Style Guide
type: technical
status: active
tags:
  - oz
  - oz/technical
  - oz/ui
  - oz/art-direction
  - oz/style-guide
aliases:
  - Signpost Style Guide
  - Font Style Guide
  - In-World Typography
updated: 2026-11-23
---

# Typography & Signpost Style Guide

> Canonical style guide for all **in-world 3D typography, building plaques, directional signposts, and diegetic markers** across *Oz: The Road Home* (L1–L7).

## 1. Core Mandate

**Never render raw, unframed white floating text in 3D space.**
Every piece of text inside the 3D world must look **authored, diegetic, and physically anchored** to an architectural plaque, carved timber board, wrought-iron bracket, or cohesive dark-velvet storybook badge that matches the 2026 UI theme (`OzThemeFactory`).

## 2. Regional Color & Ink Palettes

| Mode / Region | Backplate Material | Primary Ink | Outline / Engraved Shadow | Trim / Accent |
| --- | --- | --- | --- | --- |
| **Oz Storybook (L2, L3, L5, L6)** | Dark aged walnut `#2E1C11` or velvet charcoal `#1A1320` | Warm gilded parchment `#FDF3D8` | Burnt umber `#22120A` | Hammered brass `#D8B24E` |
| **Winkie Dread (L4)** | Forged iron `#18141A` | Ember parchment `#F5D6B8` | Obsidian `#0B070C` | Tarnished bronze `#B85A2A` |
| **Kansas Prairie (L1, L7)** | Weathered silvered cedar `#36363A` | Silvered cream `#ECECF0` | Charcoal `#121215` | Pewter iron `#787880` |

## 3. The 3-Tier Signage System

### Tier 1 — Carved Directional Signposts (`WorldKit.make_wooden_signpost`)
- Used along the Yellow Brick Road and crossroads.
- **No floating text above the post.** Text is mounted **flush on both faces of the angled wooden arrow plank** (`BILLBOARD_DISABLED`), framed by brass corner rivets and a hanging colored glass finial lantern.
- Distance culling: `visibility_range_end = 14.0`, `fade_margin = 3.5`.

### Tier 2 — Architectural Crest Plaques (`WorldKit.make_building_crest_sign`)
- Used on cottages, Guild Hall, Farmhouse, Barn, and shops (`MINT HOME`, `CANDY HOME`, `DEBTS`, `FARMHOUSE`).
- Scrolled wrought-iron hanging bracket, chamfered dark-walnut backplate, hammered brass inner border, region-tinted enamel face, and embossed gold-leaf lettering (`BILLBOARD_DISABLED`).

### Tier 3 — Diegetic World Badges (`WorldKit.make_world_badge`)
- Used on interactive landmarks (Water Cistern, Mice Cart, Lion Sanctuary, Toto's Basket, Shutter, Cellar Doors).
- Compact dark-velvet/walnut 3D backing plate with thin brass border and warm parchment lettering—never raw unbacked neon white text.
- Tight proximity culling (`visibility_range_end = 9.0`, `fade_margin = 2.5`) so distant vistas stay photo-clean.

## 4. HUD & Menu Alignment Rules (Thrive-Inspired Polish)
- All modal overlays (`PauseMenu`, `SettingsMenu`) MUST be wrapped in full-viewport `CenterContainer` nodes (`PRESET_FULL_RECT`) so they remain mathematically centered at every window aspect ratio and UI Scale (80%–140%).
- Sub-modals (`SettingsMenu`) MUST expose both a `"← Back to Pause Menu"` button and `Esc` shortcut returning cleanly to the parent menu.
