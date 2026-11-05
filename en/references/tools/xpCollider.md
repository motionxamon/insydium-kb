# xpCollider — tool card

Mentioned in **42** recipes · 2023-02-21 → 2026-08-04 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Logo: **xpCollider tag**, Bounce 0, Friction 0. FLIP Solver Accuracy: substeps **Min 2 / Max 4**. [▶ 2:08](https://youtu.be/brhdU9ibnow?t=128) — *[2026-01-06](../../recipes/2026-01-06_sticky-flip-object-rising.md)*
- Container cube with **xpCollider Normals: Inside**. Box emitter same footprint, **Shot – Regular**, radius 3, full life. nxGravity; **nxFluids SPH** substeps 4, viscosity 4. [▶ 0:56](https://youtu.be/C_fXmAUTb2Q?t=56) — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- Torus **xpCollider tag**: Bounce 0, some Friction (with variation for sliding variety) → particles bounce off when pushed… [▶ 7:04](https://youtu.be/PTamR793O-k?t=424) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- Start from a NeXus scene; **disable nxGravity and nxConstraints** and the xpCollider on the box — C4D's solver takes over physics. [▶ 0:51](https://youtu.be/eBnMW0v43Ac?t=51) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- Container: **xpCollider** bounce/friction 0, Normals **Inside**; make editable and **delete the exit face**. [▶ 1:31](https://youtu.be/q8Crdpa1XUw?t=91) — *[2025-07-08](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)*
- X geometry: xpCollider Outside, bounce 0. [▶ 7:16](https://youtu.be/u2MiqeckNaQ?t=436) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **xpEmitter ▸ Object**: the tube, **Polygon Area**; Emission **Shot** in **Simulate** mode (particles exist on frame 0), speed 0, **100,000** particles. xpCollider tag on the tube. [▶ 0:44](https://youtu.be/xGxf_IIIekY?t=44) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- - Floor **xpCollider**: Bounce 0, Friction 100% (later 20%). — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- Ground: **xpCollider** tag, bounce 0, a little friction. [▶ 16:12](https://youtu.be/V4mwAf8tcLk?t=972) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Container: X-ray on; **xpCollider** tag with normals **inside**, Bounce 0. [▶ 4:37](https://youtu.be/_W2ivetBEPo?t=277) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Cheap rock colliders: Ctrl-drag a copy of the tfRock null into Utilities, hide the high-res set, drop the copy's tfRock **Subdivisions to 1** (same shape, far fewer polys). Put the copy in an **xpJoin** and give the join one xpCollider tag (Bounce 0). [▶ 7:26](https://youtu.be/_W2ivetBEPo?t=446) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Anti-collapse: copy the bust (no deformer/tags), make it invisible, add **xpCollider** tag with Bounce and Friction off. [▶ 25:00](https://youtu.be/eJXaD9gVMsE?t=1500) — *[2024-10-04](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)*
- Parent particles emitted from a primitive sphere (sphere has an xpCollider tag). [▶ 0:10](https://youtu.be/LB-aA-N-2b0?t=10) — *[2024-08-27](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)*
- - Dish: cylinder with top cap removed, **xpCollider** tag, Normals **Inside**, Friction **41 %**; black material. — *[2024-08-20](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)*

## All recipes (42)
- 2026-08-04 · [Fake rigid-body rolling with nxSpin "Roll" layer](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-01-06 · [Water clinging to an object rising out of a FLIP pool (nxSticky)](../../recipes/2026-01-06_sticky-flip-object-rising.md)
- 2025-10-28 · [Liquid countdown: fluid flowing along animated number splines (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-10-07 · [Pulsing particles pushing each other while hugging a surface (collider attraction)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-26 · [Particles → C4D rigid bodies, colored by nxColor (xpGenerator + Simulation tags + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-07-15 · [Sand that piles into a spline shape (granular SPH + xpFlowField To-Spline layer)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-07-08 · [Endless river / fluid stream (open-sided container + refill emitter + nxKill)](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)
- 2025-06-10 · [Fluid sphere: settle → boil → explode → slosh (initial state + age-mapped nxVorticity / nxWind)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-22 · [Paint-style peeling off a surface (nxInfectio groups + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-05-13 · [Particle-to-particle collisions with pulsed "light" blasts (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2025-05-07 · [Exploding granular bust rendered as sand and as snow (nxFluids SPH Granular, nxExplode, stability mapped to Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-25 · [Sand + water in one sim (nxFluids SPH Granular + per-emitter nxFluids tag, stability mapped to age)](../../recipes/2025-03-25_sand-and-water-granular-liquid-mix.md)
- 2025-03-20 · [Slicing a soft body with a collider knife (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-10-04 · [Organic wrinkle growth creeping over a statue (nxConstraints Forces repulsion + xpDeformer, vertex-map-driven nxQuestion groups)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-09-03 · [Springy ribbons vs loose grains by color (nxConstraints Birth connections, Break mapped to Color Brightness)](../../recipes/2024-09-03_nxconstraints-break-mapped-to-color.md)
- 2024-08-27 · [Field-triggered self-growing tendrils (nxQuestion Variable + Spawn + Set Age/Life, nxPush by radius)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-08-20 · [Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Lava that freezes and re-melts (animated Random field color → mapped nxWind strength + nxSpeed max speed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-07-02 · [Emitting from a spline projected onto a rippling surface (mtSplineSample + mtPointProject + Jiggle cache)](../../recipes/2024-07-02_projected-spline-emission-animated-surface.md)
- 2024-05-07 · [Realistic gusting leaves (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-03-19 · [Choppy, swirling water body (nxVorticity on PBD vs SPH)](../../recipes/2024-03-19_nxvorticity-choppy-water.md)
- 2024-02-27 · [Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-02-20 · [Layered liquids of different density (nxFluids tag density in SPH / radius in PBD)](../../recipes/2024-02-20_nxfluids-mixed-density.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-07 · [Floating / sinking object in a NeXus fluid (xpDynamics tag + per-emitter nxFluids tag density)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-08-22 · [Splashing rain rig (xpCollider Spawn on collision, xpJoin for many colliders)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-06-20 · [Polygon-by-polygon disintegration driven by particles (xpFragmenter Faces Polys, xpWind with linear field, xpTurbulence mapped to distance travelled)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Logo shatters on time, re-shatters on impact, spawns debris and dust (xpShatter layers + xpDynamics Push + collider Spawn + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-19 · [High-tension paint tendrils floating on a fluid bed (nxFluids SPH, nxFluids tag density, per-emitter nxConstraints Forces, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-19 · [Feature notes: mtRayline sneak peek (MeshTools raycast spline generator)](../../recipes/2023-04-19_feature-notes-mtrayline-sneak-peek-part-a.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-16 · [Volcanic crater terrain + low-poly collider (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)](../../recipes/2023-03-16_terraformfx-volcano-crater-lowpoly-collider-part-a.md)
- 2023-03-16 · [Sand logo reveal with only the hero grains simulated (nxFluids SPH Granular + static scatter from a vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-07 · [Snow sculpture that crumbles (Shot-mode hex packing + nxFluids SPH Granular: friction, substeps, stability, cohesion)](../../recipes/2023-03-07_nexus-sph-granular-snow-sculpture.md)
- 2023-02-21 · [Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
