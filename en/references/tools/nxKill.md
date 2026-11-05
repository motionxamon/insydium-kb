# nxKill — tool card

Mentioned in **12** recipes · 2023-10-31 → 2026-10-21 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Clean strays: **nxKill**, Volume = Object (zombie), toggle the inside/outside icon so it kills particles **outside**. Keyframe **Enabled** off after the first frames (~frame 52) so released particles aren't killed later. [▶ 4:12](https://youtu.be/-QzOnmifveY?t=252) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- Tune proportions via the random thresholds. nxKill Outside Camera FOV keeps it light. — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- **nxKill → Outside Camera FOV** (link camera) → huge savings. [▶ 5:49](https://youtu.be/LPu79OH-yC0?t=349) — *[2026-01-27](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)*
- Animated emitter spraying onto a tube collider; **nxGravity 400**; **nxFluids SPH** substeps 6 (P-P interaction); **nxKill** bounds. [▶ 0:27](https://youtu.be/_7bYCGydqXo?t=27) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- **nxKill ▸ Object**: kill outside "fluid kill" volume → escaped particles stop costing time. [▶ 3:50](https://youtu.be/q8Crdpa1XUw?t=230) — *[2025-07-08](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)*
- **nxKill** with a box: **Volume ▸ Inside bounds** at the attractor so particles die on arrival. Hide kill and attractor. [▶ 2:07](https://youtu.be/K2Jb2lxzgSY?t=127) — *[2025-05-08](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)*
- **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Below it **nxKill**, Volume = Objects ▸ floor cube, Inside → kills grains pushed into the floor. [▶ 24:39](https://youtu.be/fxJI8py9BzU?t=1479) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Efficiency: **nxKill ▸ Outside Camera Field of View** with the render camera (optional extra degrees) — off-screen grains die and stop costing sim/cache time. [▶ 22:43](https://youtu.be/V4mwAf8tcLk?t=1363) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Break the hex grid: **disable the collider**, emission **Jitter X/Y/Z = 0.225** (≤ radius), then **nxPush** Particle Radius, full strength, thousands of iterations (≈3 min for frame 1) to undo overlaps; then **nxKill** box (size 100, Y −100 so its top sits on the floor, kill inside bounds) placed **after** the push to remove grains pushed below ground. [▶ 36:40](https://youtu.be/V4mwAf8tcLk?t=2200) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxKill**: Volume **Object** = container, kill **outside**, **Only Born** → removes particles spawned outside the cylinder. [▶ 6:25](https://youtu.be/_W2ivetBEPo?t=385) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Method A — **nxKill**: Volume **Outside Bounds**, Radius **0** (kills everything), then Fields ▸ drag in the collider, layer mode **Points → Volume**, Remapping ▸ **Invert** → only particles outside the capsule die. [▶ 3:52](https://youtu.be/MRrkMcNyU-w?t=232) — *[2023-10-31](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)*

## All recipes (12)
- 2026-10-21 · [Walking character crumbling to sand (nxBind + falloff release + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-05-05 · [Few big, many small: random sub-groups + nxScale mapped by group](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-01-27 · [Wispy particle trail behind a running mocap character (EFX advection)](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)
- 2025-09-16 · [Stretching and snapping fibres (nxConstraints Birth + constraint trails + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-07-08 · [Endless river / fluid stream (open-sided container + refill emitter + nxKill)](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)
- 2025-05-08 · [Wrapping a particle ribbon around a spline with C4D deformers (Spline Wrap + Twist on an xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-02 · [Beading water droplets (nxFluids SPH surface tension + age-mapped nxGravity)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-10-31 · [Kill stray foam outside an arbitrary container (nxKill + field Volume invert / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
