# nxMPM — tool card

Mentioned in **32** recipes · 2023-03-07 → 2026-10-21 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxMPM** with a domain (optional — sparse — but a domain gives tighter control and a faster solve). Display ▸ Draw Grid (Back) to see voxels. [▶ 10:23](https://youtu.be/-QzOnmifveY?t=623) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- Emitter ▸ **Match Solver Resolution** → nxMPM; the radius is now driven by the solver. Resolution 40 → ~600 particles; **150** → ~30k (demo, not production). [▶ 11:50](https://youtu.be/-QzOnmifveY?t=710) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- **nxMPM** (brings a domain); raise it +200 in Y to sit on the floor. Bounds are optional (MPM object ▸ **Use Bounds** off = sparse) but a domain is easier and lighter. [▶ 2:39](https://youtu.be/UT9_Aht5waE?t=159) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- nxEmitter: Sphere, radius ~14–17, direction −Y, Rate, speed 30 cm; **Match Solver Resolution** → nxMPM. Add **nxGravity**; long timeline (8000 F). [▶ 3:36](https://youtu.be/UT9_Aht5waE?t=216) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (auto radius + grid packing). Emission **Shot** for one blob. [▶ 2:35](https://youtu.be/jItRyLgdjPg?t=155) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*

## All recipes (32)
- 2026-10-21 · [Walking character crumbling to sand (nxBind + falloff release + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-10-11 · [Tall sand piles with auto-sleep, wake-on-collision and a brittle block (nxMPM Materials + Auto Sleep + display channels)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Break up the hex-grid look of a cached granular sim (Create Point Cloud + Geometry Nodes jitter)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-08 · [Water jet eroding clumpy sand (nxFluids SPH Granular + Mixer liquid, nxBlend color → mapped granular settings)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-04 · [Fake rigid-body rolling with nxSpin "Roll" layer](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-28 · [Clumping sand / snow with SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-06-12 · [Viscous slime coiling over a head (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-06-02 · [Granular text blown apart by gusts mapped to animated Voronoi color](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2025-07-15 · [Sand that piles into a spline shape (granular SPH + xpFlowField To-Spline layer)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-05-14 · [Water collapsing a snow sculpture (nxFluids SPH granular + liquid tag, age-mapped nxGravity, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-15 · [Upres a granular sim while keeping its shape (cached low-res + nxUpres velocity blend)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2025-04-01 · [Hide the hexagonal grid in granular sims (emitter Jitter + one-frame nxPush + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2025-03-25 · [Sand + water in one sim (nxFluids SPH Granular + per-emitter nxFluids tag, stability mapped to age)](../../recipes/2025-03-25_sand-and-water-granular-liquid-mix.md)
- 2025-03-20 · [Slicing a soft body with a collider knife (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-06-11 · [Statue crumbling into sand as an infection spreads (nxInfectio groups + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-06 · [Organic wobbling spiky ball (mtSubdivider + mtInset on an xpDynamics soft body)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2024-01-30 · [Bullet-dented metal sign (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2024-01-02 · [Melting blob from the outside in (nxDrag hold + nxQuestion Neighbors → group switch + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-07 · [Floating / sinking object in a NeXus fluid (xpDynamics tag + per-emitter nxFluids tag density)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-07-25 · [Recursive shattering on impact (xpShatter Voronoi layers with Collision trigger, Bullet rigid bodies)](../../recipes/2023-07-25_xpshatter-recursive-bullet.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-04-19 · [Interactive melt / re-harden rig driven by particle color (nxSpeed Clamp Max Speed mapping + nxQuestion fields + nxBlend + mapped SPH viscosity)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-16 · [Exploding planet: spin-speed-driven texture emission with clumping debris (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-16 · [Sand logo reveal with only the hero grains simulated (nxFluids SPH Granular + static scatter from a vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-07 · [Snow sculpture that crumbles (Shot-mode hex packing + nxFluids SPH Granular: friction, substeps, stability, cohesion)](../../recipes/2023-03-07_nexus-sph-granular-snow-sculpture.md)
