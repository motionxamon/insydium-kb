# xpCache — tool card

Mentioned in **33** recipes · 2023-03-29 → 2026-09-29 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpCache** (INSYDIUM ▸ Cache): **EFX Format → OpenVDB**; enable **Density, Temperature, Velocity** (velocity is required for blur); Fuel can be skipped. Build (≈15 min for 200 frames in the demo). [▶ 2:14](https://youtu.be/qZyBMJaN6ak?t=134) — *[2026-09-29](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)*
- **xpCache** → EFX Format **OpenVDB**; channels **Smoke (density) + Temperature** only. Velocity only if you need motion blur or advection (≈3× file size). [▶ 1:18](https://youtu.be/gfcEhBMSgkI?t=78) — *[2026-05-12](../../recipes/2026-05-12_octane-explosiafx-vdb.md)*
- Cache meshes: xpCache ▸ Build ▸ **Continue** (not Overwrite) reads cached particles and adds meshes (~1 h 20 min); then hide both emitters. [▶ 53:45](https://youtu.be/Siw3tkJepaU?t=3225) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- Production: Radius **0.4** → just under 3 M particles (presenter suggests ~6 M for sand at this framing). xpCache (compress on build): ~27 min / 100 F. Same settings now blast too hard and fragment too fine. [▶ 18:45](https://youtu.be/fxJI8py9BzU?t=1125) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- **xpCache** with **Compress Cache on Build**: 500 F took ~20 min (estimate starts at hours but most grains are dead by ~F200). Viewport: Dots, Level of Detail **1%**. [▶ 43:57](https://youtu.be/V4mwAf8tcLk?t=2637) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Simply dropping radius to 1 gives detail but a completely different sim — so instead **cache the radius-2 sim** (xpCache ▸ Build Cache). [▶ 2:28](https://youtu.be/GU37kEW507c?t=148) — *[2025-04-15](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)*
- Fly-out groups: tear off the INSYDIUM menu (click its top bar) and drag a whole submenu — e.g. **MeshTools**, or X-Particles ▸ **NeXus** — into the palette; the small arrow shows it holds sub-commands. Add frequent single items too (**xpEmitter**, **xpCache**). [▶ 4:09](https://youtu.be/jzFk-veno5U?t=249) — *[2025-02-27](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)*
- **xpCache**: external files, compress on build → Build (2000 F ≈ 1.5 min here). [▶ 0:40](https://youtu.be/dA4cn2wx47A?t=40) — *[2024-12-03](../../recipes/2024-12-03_duplicate-particle-caches.md)*
- Moving a cached emitter does nothing → xpCache ▸ **Playback ▸ Local Coordinates** → cache follows the emitter; in Object mode you can **scale** (even non-uniformly) and rotate it. [▶ 1:40](https://youtu.be/dA4cn2wx47A?t=100) — *[2024-12-03](../../recipes/2024-12-03_duplicate-particle-caches.md)*
- Timeline **800** frames; **xpCache** to external files, compressed (~5 min). [▶ 25:04](https://youtu.be/_W2ivetBEPo?t=1504) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **xpCache ▸ Build Cache ▸ Continue** (NOT Overwrite) → only the uncached foam emitter is simulated; existing fluid cache is untouched (~35 min, 3M+ foam particles at peak). [▶ 35:05](https://youtu.be/_W2ivetBEPo?t=2105) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- xpCache ▸ Playback ▸ Retiming **Time (seconds)**: key 0 s at frame 0 and 500/30 = **16.6 s** at the last frame; curve **Linear**. [▶ 0:52](https://youtu.be/SiDN-95Yk88?t=52) — *[2024-10-29](../../recipes/2024-10-29_retime-cached-meshes.md)*
- **xpCache ▸ Build Cache** (default, 200 F). [▶ 3:49](https://youtu.be/c-JysAVC__w?t=229) — *[2024-10-15](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)*
- xpCache ▸ Playback ▸ **Custom**: tick only **Velocity** and **Color** — leave **Radius** off. [▶ 4:22](https://youtu.be/c-JysAVC__w?t=262) — *[2024-10-15](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)*

## All recipes (33)
- 2026-09-29 · [nxExplosiaFX → OpenVDB → Redshift with vector motion blur](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)
- 2026-05-26 · [Underwater splash bubbles (EFX advection + nxMesher + particle haze)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-05-12 · [Render nxExplosiaFX in Octane via OpenVDB](../../recipes/2026-05-12_octane-explosiafx-vdb.md)
- 2026-02-17 · [Recolor cached particles with nxColor (and speed-clamp by color)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-05-14 · [Water collapsing a snow sculpture (nxFluids SPH granular + liquid tag, age-mapped nxGravity, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-15 · [Upres a granular sim while keeping its shape (cached low-res + nxUpres velocity blend)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2025-03-18 · [Particle motion blur in Redshift (custom shutter, Frame Position for dying particles)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2025-02-27 · [Docked custom palettes for INSYDIUM tools (C4D Command Manager, tear-off submenus, Lock Icon)](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)
- 2024-12-03 · [Populate a scene from one particle cache (xpCache local coordinates, Copy Tag Data, per-tag offset)](../../recipes/2024-12-03_duplicate-particle-caches.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-10-29 · [Slow-motion ramp on a meshed fluid (retime particle cache, then cache the mesher from retimed particles)](../../recipes/2024-10-29_retime-cached-meshes.md)
- 2024-10-15 · [Uniform render size from a radius-driven sim (xpCache Custom Playback channels, Redshift particle spheres)](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)
- 2024-09-24 · [Smooth slow-motion speed ramps on cached particles (xpCache Playback Scale / Offset / Retiming Time in seconds)](../../recipes/2024-09-24_xpcache-retime-speed-ramp.md)
- 2024-09-10 · [Multi-layer grayscale color → remapped additive flames (nxColor Age × Heading × Pitch, Redshift Color User Data)](../../recipes/2024-09-10_nxcolor-blended-layers-redshift-additive.md)
- 2024-04-30 · [Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-13 · [Densify a cached advected sim by spawning (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-30 · [Bullet-dented metal sign (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-07-11 · [Upres a cached low-count sim into a dense one (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-19 · [Logo shatters on time, re-shatters on impact, spawns debris and dust (xpShatter layers + xpDynamics Push + collider Spawn + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-19 · [High-tension paint tendrils floating on a fluid bed (nxFluids SPH, nxFluids tag density, per-emitter nxConstraints Forces, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Swapping in a high-detail smoke sim, final retime and Cycles 4D render setup (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Combining cached sub-scenes into one master build (xpCache Hold/Offset, Alembic speed, PolyFX + layered fields)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
