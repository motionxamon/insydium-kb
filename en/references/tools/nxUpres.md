# nxUpres — tool card

Mentioned in **8** recipes · 2023-06-23 → 2025-08-14 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxUpres** (below the movement modifiers): Source = source emitter, Destination = dest; **Groups Affected group 2** so unreleased particles stay put. [▶ 5:14](https://youtu.be/rMKmeJ68yiE?t=314) — *[2025-05-27](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)*
- **nxUpres**: Source = surface emitter, Destination = volume emitter; untick Velocity, tick **Color**. Each volume particle blends its 3 nearest surface colours. Hide surface particles, step one frame. [▶ 4:12](https://youtu.be/N32nQXnqMLE?t=252) — *[2025-04-29](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)*
- Volume emitter ▸ **Initial State ▸ Set State**; Emission → **Controlled Only**. Disable the surface emitter and nxUpres. [▶ 5:35](https://youtu.be/N32nQXnqMLE?t=335) — *[2025-04-29](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)*
- Add **nxUpres**: Source = cached low-res emitter, Destination = live high-res emitter, transfer **Velocity only**. [▶ 3:51](https://youtu.be/GU37kEW507c?t=231) — *[2025-04-15](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)*
- **nxUpres**: Source = cached emitter, Destination = new emitter. Particles-to-blend default 3 nearest (velocity blend); raised to ~7 for smoother results. [▶ 4:39](https://youtu.be/kDZyYaCgHb8?t=279) — *[2024-04-30](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)*
- NeXus ▸ **nxUpres**: Source = cached base emitter, **Destination** = upres emitter. Defaults → green particles follow the pink cached ones (velocity blended in). [▶ 1:29](https://youtu.be/RfvvtXkG8Y0?t=89) — *[2023-07-11](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)*

## All recipes (8)
- 2025-08-14 · [Feature notes: nxFollowGeo spline modes, per-channel nxUpres, layered nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-05-27 · [Detailed field-triggered explosion via upres (nxUpres position + velocity, nxExplode, nxQuestion group switch)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-04-29 · [Volume particle cloud coloured by an object's UV texture (texture surface emitter + nxUpres Color + Initial State)](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)
- 2025-04-15 · [Upres a granular sim while keeping its shape (cached low-res + nxUpres velocity blend)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2024-04-30 · [Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2023-07-11 · [Upres a cached low-count sim into a dense one (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-06-26 · [Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
