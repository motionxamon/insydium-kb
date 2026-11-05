# nxCache — tool card

Mentioned in **13** recipes · 2023-03-29 → 2026-10-07 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxCache** at res 120 (~2 min in the demo). — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxCache** ▸ Build Cache (~40 s here), then disable solvers/modifiers. [▶ 5:29](https://youtu.be/M2yxZlZQBec?t=329) — *[2026-10-06](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)*
- **Render tab ▸ VDB Output: Live** → temporary VDB sequence, auto Blender Volume object hooked to all channels, preset fire/smoke material; sim stays live (no cache needed). Alternatives: nxCache or VDB export + Blender volume import. [▶ 22:11](https://youtu.be/RH6ukNvt-No?t=1331) — *[2026-06-25](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)*
- Timeline 300 F, **nxCache** defaults ▸ Build Cache (~20–30 s), then disable the live objects. [▶ 15:28](https://youtu.be/na6NGPw4XWM?t=928) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*

## All recipes (13)
- 2026-10-07 · [Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Break up the hex-grid look of a cached granular sim (Create Point Cloud + Geometry Nodes jitter)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-06-25 · [Fuel-burning fire and smoke rendered live in Cycles (nxExplosiaFX sources, forces, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2025-03-18 · [Particle motion blur in Redshift (custom shutter, Frame Position for dying particles)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-30 · [Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-07-11 · [Upres a cached low-count sim into a dense one (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-03-29 · [Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
