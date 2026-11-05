# xpGenerator — tool card

Mentioned in **13** recipes · 2023-02-21 → 2026-08-04 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Instance non-spherical shapes with **xpGenerator** (random children, **Multi-Instance** = fastest). Problem: instances keep orientation and slide. [▶ 4:58](https://youtu.be/OFx-ALGOlAU?t=298) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- Per-particle color (e.g. nxColor gradient by Speed, 0–300 cm/s) does **not** show with **Multi-Instance** (treated as one object) → switch xpGenerator to **Render Instances** (slower). [▶ 5:49](https://youtu.be/OFx-ALGOlAU?t=349) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- xpGenerator **Render Instances** of a Platonic; Extended Data **Use Rotation → Random**. [▶ 8:50](https://youtu.be/PTamR793O-k?t=530) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- XP System ▸ Generators ▸ **xpGenerator** per emitter (rename "generator main", "generator lights"); the geometry to copy is a **child** of the generator. [▶ 1:30](https://youtu.be/eBnMW0v43Ac?t=90) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- Fork targets: **xpGenerator** with an editable Sphere (**12 segments**) linked to the emitter → a sphere per particle (hide them). [▶ 4:57](https://youtu.be/UXqS-dqsHiM?t=297) — *[2025-08-07](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)*
- For render, instance leaf geometry with your renderer's tag or an **xpGenerator**. [▶ 0:54](https://youtu.be/zG0XcLByiG4?t=54) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- **xpGenerator** from the emitter, children = 4 single-polygon planes with alpha-cut leaf materials; **Multiple children ▸ Random**, clone type **Multi-Instance**. [▶ 5:02](https://youtu.be/RRKxOyJVrO8?t=302) — *[2024-05-07](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)*
- Flakes: three Flower splines in **Extrude** objects as children of **xpGenerator** (emitter linked), multiple-children mode Random, Clone type **Multi-Instances** for viewport speed. (With Redshift/Octane/Cycles 4D you would instance at render time instead.) [▶ 5:35](https://youtu.be/RnIGtMwTpLg?t=335) — *[2023-12-26](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)*

## All recipes (13)
- 2026-08-04 · [Fake rigid-body rolling with nxSpin "Roll" layer](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-06-09 · [Random birth orientation + repeatable 360° spins (nxSpin + age reset)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-01-20 · [Rippling field of clones: nxTurbulence "Direction" mode + nxSpin Tangential + nxLimit](../../recipes/2026-01-20_nxturbulence-direction-mode-clones.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-26 · [Particles → C4D rigid bodies, colored by nxColor (xpGenerator + Simulation tags + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-08-07 · [Procedural plasma ball (nxFollowGeo + nxTurbulence on particles, mtSplineFX arcs, mtEdgeSpline intersection forks)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-07-24 · [Feature notes: nxSpin layers, nxColor Noise/Neighbor gradient, nxDirection Direction Force (Fused 2025 preview, part 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-03-04 · [Leaves blown off a Taiao tree (Taiao emitter leaves + nxWind Von Karman + nxQuestion Field/Random + xpSpin mapped to Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2024-05-07 · [Realistic gusting leaves (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-07-05 · [Electric arcs, cables and laser burn sparks (mtSplineFX + mtRayline + nxQuestion Spawn)](../../recipes/2023-07-05_mtsplinefx-arcs-rayline-laser-sparks-part-c.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-02-21 · [Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
