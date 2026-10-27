---
title: Tech Stack Decision
type: technical
status: draft
tags:
  - oz
  - oz/technical
aliases:
  - Engine
  - Tech Stack
updated: 2026-10-26
---

# Tech Stack Decision

## Recommendation

**Godot 4.5** for the production game. Optional **React Three Fiber** prototype for the pitch/press kit.

## Comparison

| Criterion | Godot 4.5 | Unity 6 | Unreal 5 | R3F / Web |
| --- | --- | --- | --- | --- |
| Cost | Free, MIT | Free tier, paid tiers | 5% royalty >$1M | Free |
| 3D action tooling | Good, improving | Strong | Best-in-class | Weak for full games |
| Animation | Good | Strong | Best | Limited |
| Console export | Improving (publishing via porting partners) | Strong | Strong | No |
| Team fit (small, web-adjacent) | **High** | Medium | Low | High for prototype |
| Iteration speed | **Very fast** | Fast | Slow | Fast (web) |
| Asset pipeline | Standard glTF | Standard | FBX/UE native | glTF |
| Web export | Yes (limited) | Yes | No | Native |
| Accessibility tooling | Manual | Manual | Manual | Manual |

## Why Godot

- MIT license; no royalties or revenue clauses.
- Fast iteration for a small team; scenes are diff-friendly text.
- GDScript + C# both viable; state machines for companions are straightforward.
- Strong 2D/3D hybrid if we prototype any UI or minigames.
- Web export gives us a **playable pitch build** without a second codebase.

## Why not Unreal

- Overkill for a stylized, mid-scope action game.
- Longer iteration; heavier asset pipeline; royalty model.
- Team is web/JS-native; C++/Blueprint ramp is costly.

## Why not Unity

- Licensing uncertainty is reduced but still a consideration.
- Tooling is good, but Godot's iteration speed and license fit this team better.

## Optional Web Prototype (R3F)

Use only if we need a **shareable browser demo** in <4 weeks:

- Three.js + React Three Fiber + Rapier physics.
- 1 arena, Dorothy + 1 companion, 3 enemies.
- Purpose: pitch, playtest feel, marketing capture.
- **Not** the production codebase. Throwaway by design.

## Decision Log

| Date | Decision | Notes |
| --- | --- | --- |
| 2026-10-26 | Godot 4.5 recommended | Pending vertical-slice validation |
| 2026-10-26 | Web prototype optional | Only for pitch, not production |

## Related

- [[Architecture & Pipeline]]
- [[Prototype Plan]]
- [[Open Questions]]
