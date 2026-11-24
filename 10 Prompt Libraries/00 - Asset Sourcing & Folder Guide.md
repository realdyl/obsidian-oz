---
title: Asset Sourcing & Local Folder Guide
type: guide
status: active
tags:
  - oz
  - oz/prompts
  - oz/audio
  - oz/art
updated: 2026-11-23
---

# Asset Sourcing & Local Folder Guide (`Oz: The Road Home`)

This folder (`10 Prompt Libraries/`) contains production-ready prompts for generating **Music (Suno)**, **Sound FX (ElevenLabs SFX / Suno / Free CC0 Packs)**, **Character Voices (ElevenLabs / Local Open-Source TTS)**, and **2D/3D Concept Art, Icons & PBR Textures**.

---

## 1. Best Free & Open-Source Audio Resources (Commercial-Safe)

| Resource | Best For | License | Notes |
|---|---|---|---|
| **[Freesound.org](https://freesound.org)** | Foley, wind, footsteps, glass/ceramic shatter, animal sounds, doors | Filter by **CC0 (Public Domain)** | Always filter `License: Creative Commons 0` so no attribution clutter is required. |
| **[Kenney.nl Audio](https://kenney.nl/assets/category:Audio)** | Crisp UI clicks, RPG chimes, inventory, impacts | **CC0 (100% Free)** | Download *RPG Audio*, *Interface Sounds*, *Impact Sounds*, and *Foley Sounds*. |
| **[Sonniss GDC Game Audio Bundles](https://sonniss.com/gameaudiogdc)** | AAA-grade ambiences, weather, weapons, magic swells | **Royalty-Free Commercial** | Massive multi-GB annual GDC giveaways — goldmine for tornado wind, storms, and stone footsteps. |
| **[OpenGameArt.org](https://opengameart.org/art-search-advanced?field_art_type_tid[]=13)** | Fantasy chimes, retro/orchestral loops, combat hits | **CC0 / CC-BY** | Check per-file license tag. |
| **[Pixabay Sound Effects](https://pixabay.com/sound-effects/)** | Quick atmospheric beds, thunder, crowd murmurs, chimes | **Pixabay Content License (Free)** | Great for fast prototyping; verify no ContentID claims on music tracks. |
| **ElevenLabs SFX v2** | Bespoke magical/combat SFX (lace whip snap, silver-shoe chime, porcelain shatter) | Commercial (paid tier) | Unmatched for hyper-specific fantasy/dark-storybook foley. |
| **Suno** | Full biome themes, combat stems, dark-storybook waltzes | Commercial (Pro/Premier tier) | Use `Instrumental` toggle + prompts in [[Suno Music Prompts]]. |
| **Local Free Open-Source TTS** | Unlimited offline character voice prototyping | Open Source (Apache/MIT) | **Kokoro-82M** (ultra-fast, natural), **Chatterbox TTS** (expressive emotion control), or **F5-TTS** (zero-shot voice cloning on Apple Silicon M2 Max!). |

---

## 2. Drop-In Local Folder Convention (Auto-Loaded by Godot)

Place your generated or downloaded files inside the Godot project under `oz/assets/audio/`. `AudioFx` (`systems/audio_manager.gd`) automatically prefers your custom files over procedural fallbacks:

```text
oz/assets/audio/
├── music/
│   ├── kansas_prairie.ogg
│   ├── kansas_storm.ogg
│   ├── munchkinland_explore.ogg
│   ├── oz_combat.ogg
│   ├── poppy_field.ogg
│   ├── winkie_castle.ogg
│   ├── boss_witch.ogg
│   ├── emerald_city.ogg
│   ├── glinda_court.ogg
│   ├── kansas_homecoming.ogg
│   ├── tailor_boutique.ogg
│   └── rapture_mode.ogg
├── sfx/
│   ├── kick.wav
│   ├── whip.wav
│   ├── urn.wav
│   ├── chime.wav
│   ├── chest.wav
│   ├── buy.wav
│   ├── ui_click.wav
│   ├── rapture.wav
│   ├── tin_axe.wav
│   ├── lion_roar.wav
│   ├── scarecrow_caw.wav
│   ├── toto_bark.wav
│   ├── curtain_draw.wav
│   └── water_splash.wav
└── voices/
    ├── dorothy/
    ├── aunt_em/
    ├── uncle_henry/
    ├── locasta/
    ├── scarecrow/
    ├── tinman/
    ├── lion/
    ├── wicked_witch/
    ├── wizard/
    ├── glinda/
    └── narrator/
```

### Recommended Export Specs
- **Music & Ambience**: `.ogg` (Ogg Vorbis, 44.1 kHz stereo, quality 6–7, loop-ready).
- **Short SFX**: `.wav` (16-bit PCM, 44.1 kHz mono or stereo, trimmed tight with 0ms leading silence!).
- **Voice Lines**: `.ogg` or `.wav` (44.1 kHz mono, normalized to `-16 LUFS`).

---

## 3. Prompt Libraries in This Folder
- [[Suno Music Prompts]]
- [[SFX Generation Prompts]]
- [[Voice Profiles & Line Scripts]]
- [[01 - Master Art & GUI Style Reference Prompts]]
- [[02 - Characters, Subcharacters & Enemies Prompts]]
- [[03 - Buildings, Architecture & Interiors Prompts]]
- [[04 - Key Objects, Artifacts & Interactive Props Prompts]]
- [[05 - Environments, Scenes & Textures Prompts]]
- [[Concept Art, Couture & Texture Prompts]] (Tailor of Vices 64×64 Shop Icons)
