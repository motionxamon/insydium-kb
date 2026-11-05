# xpColor — tool card

Mentioned in **6** recipes · 2023-03-29 → 2026-06-02 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpColor** (CPU) with a Maxon **Noise shader: Cell Voronoi**, global scale ~330, strong low/high clip → patchy black/white per particle. (CPU modifier used because it samples Maxon shaders in full 3D; nxColor has GPU noises.) [▶ 1:18](https://youtu.be/zyN7ERz7yuw?t=78) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- Make the pattern jump occasionally: keyframe the noise **Seed** (+1 every 2 frames, linear, Track After: Continue) and keyframe xpColor **Enabled** on/off pulses (frames 0–2, 50, 100, 150) → recolor only at chosen moments. [▶ 2:42](https://youtu.be/zyN7ERz7yuw?t=162) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **xpColor** with a Maxon **Noise (Voronoi)** shader, huge scale, clipped, animation speed ~7 → moving black/white patches. [▶ 1:04](https://youtu.be/PTamR793O-k?t=64) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **xpColor**, mode **Immediate**, Shader **Gradient** (Spherical) with a preset, **Turbulence 20%**. [▶ 5:24](https://youtu.be/M4z3kOU4YEw?t=324) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- Main system: **xpColor** (CPU) Set Color white (not Immediate). Infecting emitters ▸ Editing ▸ **Editable** so they appear as points to Fields; drag them into xpColor Fields, mode **Max**, radius 3 → 5 (bigger = faster spread; more infectors also speeds it). [▶ 49:05](https://youtu.be/qaso-gPGBnI?t=2945) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*
- **xpColor** ▸ Shader = **Noise**, type **Blistered Turbulence**, Global Scale **500%**, Animation Speed **0.3**; push Brightness/Contrast so only bright patches stay white — white particles will grow, dark ones stay small. [▶ 20:03](https://youtu.be/uS_zr-Jf178?t=1203) — *[2023-09-27](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)*
- Color for render: **xpColor** ▸ Gradient by Parameter ▸ **3D Linear**, axis Z, Min −12.5 / Max 12.5, **Change on Birth Only**; gradient black → white so color can be remapped at render time and cracks show the lighter inner grains. [▶ 18:08](https://youtu.be/SMO0CZcHa3k?t=1088) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*

## All recipes (6)
- 2026-06-02 · [Granular text blown apart by gusts mapped to animated Voronoi color](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2023-12-19 · [Swaying glass tendrils with particles on the tips (xpTendril + xpTrail Tendrils + xpSplineMesher + xpTrailTip tag)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-09-27 · [Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
