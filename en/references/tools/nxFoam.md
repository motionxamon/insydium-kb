# nxFoam — tool card

Mentioned in **7** recipes · 2023-06-23 → 2026-08-11 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- NeXus ▸ **Liquid Fill** → domain, nxGravity, and a folder with emitter, **nxFluids**, **nxMesher (off)**, group "foam" and **nxFoam (off)**. Plays as a tank out of the box. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Foam: enable **nxFoam**; solver type must match (**APIC**); Simulation Bounds = the sphere. Emitter display Points size 1 to see white water. [▶ 19:12](https://youtu.be/vglrHSL-uc4?t=1152) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- **nxFoam** → **Add Emitter** (Dots display); keep only **Crest** layer (remove Aerate/bubbles), lower crest rate, **After Age 7**, life ~70 → fine detail on the cached fluid. [▶ 7:38](https://youtu.be/C_fXmAUTb2Q?t=458) — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- Turn off nxFluids, nxVorticity and nxRotate (fluid is cached); **keep nxGravity** — nxFoam needs gravity for buoyancy/advection. Hide the fluid emitters. [▶ 27:07](https://youtu.be/_W2ivetBEPo?t=1627) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **nxFoam** + a new emitter for it ("emit foam"): **Crest rate 10**, **Air rate 10**; foam only from fluid particles at least **35 frames** old (with variation); Life **200** (with variation); Advection **Drag ~100** so foam sticks to the flow and traces the swirls. Foam emitter Display ▸ **Dots**. [▶ 29:47](https://youtu.be/_W2ivetBEPo?t=1787) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **nxFoam** on the cache ▸ **Add Emitter** (display Dots). Born after age **60 → 10**, **Crest 0**, **Aerated ~20**, **Min Impact 0 / Max Impact 10** → impact foam. [▶ 1:21](https://youtu.be/MRrkMcNyU-w?t=81) — *[2023-10-31](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)*

## All recipes (7)
- 2026-08-11 · [Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2025-10-28 · [Liquid countdown: fluid flowing along animated number splines (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2024-11-04 · [Rendering speed-colored foam as additive glow in Redshift, ACEScg into After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2023-10-31 · [Kill stray foam outside an arbitrary container (nxKill + field Volume invert / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-06-26 · [Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
