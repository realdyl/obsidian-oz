---
title: Basket & Toto Wayfinding
type: system
status: draft
tags:
  - oz
  - oz/system
  - oz/ui
aliases:
  - Basket
  - Inventory
  - Toto Wayfinding
updated: 2026-10-26
---

# Basket & Toto Wayfinding

Two diegetic systems that keep the player in the world instead of in menus.

## The Basket (Inventory)

**Fantasy:** Dorothy's basket is her bag. Items physically sit in it.

### Presentation

- Opens as a close-up of the basket; items are arranged inside.
- Categories are spatial regions, not tabs:
  - **Gifts** (quest items, tokens, letters)
  - **Provisions** (healing, buffs)
  - **Keys** (oil can, axe shards, seeds)
  - **Curios** (collectibles, lore pages)
- Hovering an item shows a short, characterful description in Dorothy's voice.

### Rules

| Rule | Detail |
| --- | --- |
| Capacity | 12 slots at start; upgrades via basket weaves |
| Stacking | Provisions stack to 5 |
| Quest items | Never consume inventory space (shown pinned) |
| Pause | Opening the basket pauses in single-player |
| Quick use | Hold a direction to bind a provision to a quick slot |

### Design Intent

Avoid spreadsheet inventory. If an item doesn't tell a story or change a fight, it doesn't go in the basket.

---

## Toto Wayfinding

**Fantasy:** When you're lost, the dog knows.

### Triggers

- Player presses **Call Toto**.
- Player is idle/lost for 10 s near an objective.
- After a failed traversal attempt (e.g., wrong path at a fork).

### Behavior

1. Toto barks, runs 3–5 m ahead, and looks back.
2. A faint **scent trail** appears along the ground toward the objective.
3. Trail fades after ~8 s; re-triggerable freely.
4. At a hidden path or interactable, Toto digs/scratches.

### Rules

| Rule | Detail |
| --- | --- |
| Never blocks combat | Toto flees during fights |
| Never spoils secrets | Only hints current *known* objective |
| No minimap arrow | Trail is the only default guidance |
| Optional marker | Accessibility toggle adds a standard waypoint |

### “Lost” Detection

- No objective progress for 90 s + no forward movement along the critical path → Toto offers a hint.
- Hints escalate: bark → trail → explicit line of dialogue.

### Design Intent

Toto is the emotional throughline (home) *and* the navigation system. Following a dog through Oz is more thematic than following an arrow.

## Related

- [[Dorothy & Toto]]
- [[Core Loop]]
- [[Accessibility & Difficulty]]
