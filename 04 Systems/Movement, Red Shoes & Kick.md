---
title: Movement, Red Shoes & Kick
type: system
status: draft
tags:
  - oz
  - oz/system
  - oz/combat
aliases:
  - Red Shoes
  - Shoes
  - Movement
updated: 2026-10-26
---

# Movement, Red Shoes & Kick

> [!warning] Naming
> Internally: **“the Shoes.”** In-world: **Silver Shoes** (book canon). “Red shoes” is a cosmetic/legal decision — see [[IP & Legal]].

## Camera

- **Default:** third-person action camera, slightly high, over-the-shoulder offset.
- **Combat:** soft lock-on with target switching; no hard lock to keep mobility fluid.
- **Optional:** isometric/wide mode for accessibility and puzzle clarity.
- Camera must never lose Dorothy in tall grass or crowd fights — silhouette outlines for Dorothy and companions.

## Core Verbs

| Verb | Input | Effect | Feel target |
| --- | --- | --- | --- |
| Walk / run | Left stick | Free movement | Responsive, grounded |
| **Blink** | Dodge (tap) | Short teleport ~4 m, i-frames | Snappy, 0.15 s activation, 6-frame i-frame window |
| **Long teleport** | Hold dodge + aim | Charge 0.6 s, travel 12–25 m to reticle/valid ground | Weighty wind-up, satisfying arrival |
| **Kick** | Attack | Shove; stagger; launch light enemies; break props | Strong hit-stop, readable arc |
| **Heel click** | Context / hold | Fast travel to discovered shrines; story triggers | Ceremonial, rare |
| **Summon** | Companion button | Bring in / dismiss companion | Dramatic entrance |

## Blink Design

Blink is the heart of the game. Rules:

1. **Directional, not teleport-to-cursor** (short blink). Long teleport uses aim.
2. **i-frames** on activation; no i-frames on arrival (avoids cheese).
3. **Charges:** 2 at start, up to 4 upgraded; recharge 1.2 s each.
4. **Through hazards, not through walls.** Destructible/soft barriers can be bypassed with upgrades.
5. **Kick-cancel:** kick → blink is a core combo; blink → kick is the punish.

### Shoe Tiers

| Tier | Unlock | Effect |
| --- | --- | --- |
| 1 · Silver | Act 1 | Blink + short teleport |
| 2 · Polished | Act 2 | +1 charge, longer teleport |
| 3 · Moonlit | Act 3 | Blink leaves a decoy afterimage; teleport through hazard zones |
| 4 · Homeward | Act 4 | Chain blink (2 in a row); teleport to Toto's trail |

## Kick Design

- **No combo tree.** One excellent kick with context-sensitive outcomes.
- Light enemy → launched (can be juggled with blink-kick).
- Armored enemy → stagger, chip armor with Tin Man axe.
- Prop/barrier → destroyed, reveals paths.
- Ledge → environmental kill setup.

## Long Teleport as World Design

Traversal gates use the Shoes:

- **Gaps** too wide to jump → teleport.
- **Hazard fields** (fire, static rot) → blink across.
- **Vertical shafts** → teleport to ledges.
- **Secrets** → optional long-teleport challenges.

## Feel Checklist (prototype exit criteria)

- [ ] Blink dodges a telegraphed attack 9/10 times when timed.
- [ ] Kick has audible/visible impact and 80–120 ms hit-stop.
- [ ] Long teleport feels like aiming a spell, not a loading screen.
- [ ] Camera never obscures the player in a 6-enemy fight.
- [ ] Input buffering works for blink→kick→blink.

## Related

- [[Core Loop]]
- [[Summon System]]
- [[Progression & Upgrades]]
- [[Prototype Plan]]
