# nxConstraints — tool card

Mentioned in **37** recipes · 2023-02-21 → 2026-10-20 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Fake inter-particle collision cheaply: **nxConstraints ▸ Forces** layer — Attraction 0, Repulsion 20%, Radius 0.05, Falloff Flat, max ~5 neighbours. Map Repulsion strength to **Speed** (range 0–0.5) so the static core isn't pushed apart. Falling grains now roll over the outside instead of dropping through. [▶ 13:17](https://youtu.be/yOPa8oM_KXE?t=797) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- nxConstraints with a **Collisions** layer (≥3 iterations) → particles stop interpenetrating and roll. [▶ 1:12](https://youtu.be/OFx-ALGOlAU?t=72) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- **nxConstraints** ▸ one layer, **Birth** connections (springs). Visualise via emitter Display ▸ **Display Constraints**. [▶ 1:19](https://youtu.be/QDBN_Xu_l68?t=79) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*
- **nxConstraints → Connections Birth**: Connection Limit 8, Radius ~20. Show links: emitter Display ▸ **Display Constraints**. [▶ 1:21](https://youtu.be/_7bYCGydqXo?t=81) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- **nxConstraints Mapping ▸ Color Brightness → Viscosity layer Stiffness**: black = full stiffness, white ≈ 0 (sharp falloff). [▶ 7:59](https://youtu.be/_k0LatnQQJw?t=479) — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- Start from a NeXus scene; **disable nxGravity and nxConstraints** and the xpCollider on the box — C4D's solver takes over physics. [▶ 0:51](https://youtu.be/eBnMW0v43Ac?t=51) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- **nxConstraints ▸ Viscosity layer**: Connection Limit 8, Radius 20 cm, **Stiffness 40%**, **Iterations 2** (more iterations = stronger as well as more accurate). [▶ 2:36](https://youtu.be/14SqrdO1c6o?t=156) — *[2025-08-05](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)*
- nxConstraints ▸ Mapping ▸ **Group map**: Category Viscosity, Parameter Stiffness, range **1 → 3**. Curve: group 1 → ~0.06 (a touch of binding), group 2 → 0.5, group 3 → 1. [▶ 5:49](https://youtu.be/14SqrdO1c6o?t=349) — *[2025-08-05](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)*
- Hold them together: **nxConstraints ▸ Distance** connection (not Birth — the particles already exist), group 2 only, **Connection Limit 50**, **Radius 250**; stiffness/breaking default → stringy peeling sheets. [▶ 5:00](https://youtu.be/xGxf_IIIekY?t=300) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxConstraints "birth"**: birth springs, search **40 cm**, **Limit 6**, **Stiffness 90**, breaking **None**. Emitter ▸ Display ▸ **Display Constraints** to see them. [▶ 1:57](https://youtu.be/PIgXQtSgnMY?t=117) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- **nxConstraints "repel"** below birth: Forces layer radius **80/80**, ~**20% more repulsion**, Groups Affected **repulsion** → particles inflate as the field converts them. [▶ 5:27](https://youtu.be/PIgXQtSgnMY?t=327) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- **nxConstraints ▸ Collisions** layer. Default collapses → **Iterations 10**. [▶ 2:14](https://youtu.be/0JdFAE_dopk?t=134) — *[2025-05-13](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)*
- **nxConstraints** ▸ **Birth** connection → yellow springs appear one frame in. [▶ 1:32](https://youtu.be/fzMhJobCGR0?t=92) — *[2025-03-20](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)*
- nxConstraints: **Iterations 10** (more = stiffer) and add a **Collision** layer → bouncy soft body instead of a splat. [▶ 2:20](https://youtu.be/fzMhJobCGR0?t=140) — *[2025-03-20](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)*

## All recipes (37)
- 2026-10-20 · [Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-08-04 · [Fake rigid-body rolling with nxSpin "Roll" layer](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-14 · [Springy constraint web rendered as trails (nxConstraints Birth connections + nxTrail Constraints mode)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2025-09-16 · [Stretching and snapping fibres (nxConstraints Birth + constraint trails + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-09-09 · [Hot runny / cold gloopy fluid that re-melts on contact (groups + nxBlend + mapped viscosity)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-08-26 · [Particles → C4D rigid bodies, colored by nxColor (xpGenerator + Simulation tags + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-08-05 · [Three gloops with three viscosities (groups + nxConstraints Viscosity mapped to Group)](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)
- 2025-07-31 · [Skinning bat wings with a cloth membrane (C4D Bind heat map + Cloth + Cloth Belt)](../../recipes/2025-07-31_bat-wing-skinning-c4d-cloth-belt.md)
- 2025-05-22 · [Paint-style peeling off a surface (nxInfectio groups + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-05-20 · [Organic springy particle network (nxConstraints birth springs + Forces layers, nxQuestion group switch & pin)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-05-13 · [Particle-to-particle collisions with pulsed "light" blasts (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2025-03-20 · [Slicing a soft body with a collider knife (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-10-04 · [Organic wrinkle growth creeping over a statue (nxConstraints Forces repulsion + xpDeformer, vertex-map-driven nxQuestion groups)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-10-01 · [Rendering constraint springs + glassy skin underwater (xpTrail Algorithm Constraints, xpOpenVDBMesher, Redshift Environment fog)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-09-03 · [Springy ribbons vs loose grains by color (nxConstraints Birth connections, Break mapped to Color Brightness)](../../recipes/2024-09-03_nxconstraints-break-mapped-to-color.md)
- 2024-08-20 · [Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-02 · [Emitting from a spline projected onto a rippling surface (mtSplineSample + mtPointProject + Jiggle cache)](../../recipes/2024-07-02_projected-spline-emission-animated-surface.md)
- 2024-04-30 · [Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-04-23 · [Particle-driven laser rays inside a sphere (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-05 · [Mixing gloopy paint colors (nxFluids SPH + nxConstraints Viscosity + nxBlend)](../../recipes/2024-03-05_nxblend-paint-mix.md)
- 2024-02-27 · [Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-01-02 · [Melting blob from the outside in (nxDrag hold + nxQuestion Neighbors → group switch + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-12-12 · [Infection-driven peel-away (nxInfectio Use Groups + nxWind/nxTurbulence on infected group + nxConstraints Distance break)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-11-07 · [Floating / sinking object in a NeXus fluid (xpDynamics tag + per-emitter nxFluids tag density)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-10-10 · [Self-organising particle blob (nxConstraints Forces attraction/repulsion + radius-mapped repulsion + Collisions + Friction)](../../recipes/2023-10-10_nxconstraints-forces-organic-blob.md)
- 2023-09-27 · [Self-organising "breathing" sphere clusters (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-09-05 · [Gloopy fluid meshed with particle colors carried into the mesh (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-07-05 · [Hot/cold variable-viscosity pour over a head (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + colour-mapped nxSpeed clamp)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-06-12 · [Fast viscous chocolate/honey pour (xpFluidPBD + xpConstraints Viscosity, Hexagonal emission)](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Fake gloopy fluid crawling over a logo (xpConstraints Forces, xpCover, radius/age/temperature Data Mapping, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [High-tension paint tendrils floating on a fluid bed (nxFluids SPH, nxFluids tag density, per-emitter nxConstraints Forces, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-17 · [Exploding planet: surface detail particles that ride the spinning sphere (displaced texture emission, Global Transform, color-driven offset)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Exploding planet: spin-speed-driven texture emission with clumping debris (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-02-21 · [Three ways to make particles collide with each other (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
