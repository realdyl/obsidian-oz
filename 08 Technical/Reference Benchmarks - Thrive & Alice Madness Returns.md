---
title: Reference Benchmarks - Thrive & Alice Madness Returns
type: technical
status: active
tags:
  - oz
  - oz/technical
  - oz/style-guide
  - oz/benchmarks
aliases:
  - Thrive & Alice Benchmarks
  - Retail Quality Reference
updated: 2026-11-23
---

# Reference Benchmarks: *Thrive* & *Alice: Madness Returns*

To elevate *Oz: The Road Home* from a playable prototype into a **retail-grade, shelf-worthy (Steam / GameStop / Walmart) Rated-M 3D action-adventure**, every GUI, system, and art decision is anchored to two complementary reference pillars (strictly **craft & architecture only** — zero imported proprietary assets).

---

## 1. *Thrive* (Revolutionary Games Studio — Open-Source Godot 4 Benchmark)

**Local Reference Path:** `/Users/dylanroberts/Documents/non-music/Dev/+ Gaming/Revolutionary Games`

| Dimension | What *Thrive* Does at Retail Grade | Concrete Application to *Oz: The Road Home* |
| --- | --- | --- |
| **UI Decoupling** | Strict separation between simulation state and UI presentation; UI listens to signals/events rather than polling or mutating gameplay nodes directly. | Refactor `PlayHUD`, `PauseMenu`, `SettingsMenu`, and `OutfitShopUI` into signal-driven Godot 4 scenes with a centralized `UIState` / `GameEvents` bus. |
| **Menu & Shell Completeness** | Full-featured Main Menu, Save/Load slot browser with thumbnails & timestamps, Graphics/Audio/Controls/Accessibility tabs, and in-game Encyclopedia (Thriveopedia). | Build an **Oz Grimoire / Codex** (Bestiary, Characters, Memories, Regions, Armaments), real Save/Load slots, and a 3D live-diorama Main Menu. |
| **Modular Stage HUDs** | Clean, stage-specific HUD layouts that adapt cleanly as the player moves from Microbe → Multicellular → Society without clutter. | Adaptive HUD modes: **Kansas Monochrome Minimal**, **Oz Exploration (fade-away chrome)**, **Combat Active (Allure/Health/Lock-On)**, and **Boss Theater**. |
| **Theme & Layout Discipline** | Consistent `Theme` resource, responsive `Container` layouts across aspect ratios (16:9, 16:10 Steam Deck, ultrawide), and crisp typography hierarchy. | Lock a single master `oz_retail_theme.tres` with ornate gilded-storybook + dark-velvet styling, scalable DPI fonts, and zero hardcoded pixel overlap. |

---

## 2. *Alice: Madness Returns* (Dark Fairytale & Rated-M Retail Benchmark)

| Dimension | What *Alice: Madness Returns* Does at Retail Grade | Concrete Application to *Oz: The Road Home* |
| --- | --- | --- |
| **Diegetic Minimalist HUD** | HUD fades out when exploring; health is an organic cluster of **crimson rose petals** that wither and scatter on hit. | **Silver-Rose Vitality Cluster** + **Desire / Allure Filigree Gauge** that fades during quiet exploration and blooms sharply when combat or Hysteria triggers. |
| **Hysteria / Desperation State** | Near-death triggers monochrome desaturation + crimson highlights, invincibility, and brutal damage spike — mechanically expressing psychological snap. | **Rapture / Hysteria Mode**: When Dorothy hits critical health or fills her Desire Meter, the world shifts to stark Kansas-grey with neon-crimson/silver highlights, empowering Silver-Shoe blinks and Whip/Kick finishers. |
| **Subverted Arsenal & Utility** | Domestic objects turned visceral (Vorpal Blade, Pepper Grinder, Hobby Horse) + Butterfly Dodge + Umbrella deflect. | Implement `[[Kinky Armaments]]`: **Lace Whip** (bind & pull into Silver-Shoe Kick), **Silk Bindings** (cocoon), **Velvet Blindfold** (sensory deprivation), **Gilded Chain** (damage tether), and **Hypnotic Perfume** (Enamored AI state). |
| **Visceral Currency & Dress Perks** | **Teeth** as upgrade currency; unlockable **Dresses** that change silhouette AND grant real gameplay perks. | Implement `[[Outfit Shop]]` (**The Tailor of Vices**) using **Desire Fragments**: Gingham, Burlap & Leather, Chrome & Velvet, and Primal Gold collections altering **Allure Multiplier** and **Enemy Intimidation**. |
| **Beautiful Corruption (M-Rating)** | Earned M-rating through psychological dread, body-horror contrast (porcelain cracking to reveal rot/gears), survivor's guilt, and opulent decadence — never cheap shock. | Contrast candy-coated Munchkinland, narcotic Poppy canyons, industrial Winkie ironworks, and gilded Emerald excess with unsettling rot, broken minds, and mature themes of desire, control, and exploitation. |
| **Memories & Secret Rooms** | Hidden **Memories** (narrative audio/text fragments) and **Radula Rooms** (bite-sized challenge arenas) reward deep exploration. | Hide **Shattered Memories** (backstories of Scarecrow's lobotomy-dread, Tin Man's hollow chest, Lion's cowardice) and **Velvet Sanctums** (optional combat/puzzle challenge arenas) in every region. |

---

## Related
- [[Retail Completeness Audit & Phase P6-P12 Roadmap]]
- [[GUI & UX Roadmap]]
- [[Art & Audio Direction]]
- [[Vision & Pillars]]
- [[Kinky Armaments]]
- [[Outfit Shop]]
