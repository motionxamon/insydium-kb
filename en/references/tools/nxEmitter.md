# nxEmitter — tool card

Mentioned in **44** recipes · 2023-03-14 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **2D sim → 3D wave (C4D):** nxEmitter flattened (height near 0), placed at the back of the warp; Birth Rate 50,000 (later 150,000); Display size 2; Full Lifespan off, Life 100, variation 20. [▶ 4:32](https://youtu.be/WJwIek6M8z8?t=272) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **FLIP spiral (Blender):** tall nxFluids FLIP domain; sphere nxEmitter at the bottom, **Match Solver Resolution** → FLIP, direction +Z, speed 2.5; nxColor by Speed; nxTurbulence strength 16. [▶ 30:13](https://youtu.be/WJwIek6M8z8?t=1813) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxEmitter**: Shape Object (the zombie), emit from **Volume**, grid mode **Hexagonal**, Shot, speed 0. In hexagonal mode the radius sets the count (0.01 → ~13k particles for testing). [▶ 1:40](https://youtu.be/-QzOnmifveY?t=100) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- - **nxEmitter** sphere radius 1.7, lifted up; Shot, random, **250,000** particles, speed 0, radius **0.01**. Born color black. — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- Use the new GPU **nxEmitter** from the NeXus menu — the old xpEmitter won't work with the new tools. [▶ 1:57](https://youtu.be/UT9_Aht5waE?t=117) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- nxEmitter: Sphere, radius ~14–17, direction −Y, Rate, speed 30 cm; **Match Solver Resolution** → nxMPM. Add **nxGravity**; long timeline (8000 F). [▶ 3:36](https://youtu.be/UT9_Aht5waE?t=216) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- Second **nxEmitter** "brittle": Box 50×50×50, −Y, speed 30, Shot at ~F220, Match Solver Resolution → same MPM. Stop the sand emitter (Emit All Frames off, ~200 frames). [▶ 15:15](https://youtu.be/UT9_Aht5waE?t=915) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (auto radius + grid packing). Emission **Shot** for one blob. [▶ 2:35](https://youtu.be/jItRyLgdjPg?t=155) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxEmitter**: Shape **Disc**, direction **+Z**, Birth Rate **10,000**; display point size 2 (display only). [▶ 1:21](https://youtu.be/I9Fq5NPENdc?t=81) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- Floor plane + torus (both hidden). **Sand nxEmitter**: Object ▸ torus, **Volume**, **Shot**, **Hexagonal**, Speed 0; Display Spheres, Gradient by **Granular**, Auto Scale off 0–20. [▶ 0:52](https://youtu.be/yp5579on6J8?t=52) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **Water nxEmitter**: Sphere, radius 0.2, placed along Y; **Rate** + Hex mode; direction **−Y**, speed **3.5**. **Radius 0.015 — must match the sand**; mixed radii make SPH explode. [▶ 4:20](https://youtu.be/yp5579on6J8?t=260) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **nxEmitter**: **Disc**, Edges only, Angle **90°**, **Shot** of 200 (2,000 for the final), Speed **2.5**, variation **1** (range 1.5–3.5 m/s). [▶ 0:34](https://youtu.be/I2ERiN8Vk2Q?t=34) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Suzanne (Subdivision 2, applied), raised and rotated. **nxEmitter**: Object, **Volume**, **Shot**, **Hexagonal**, Speed 0. Display Spheres shows the true packing; radius **0.01 m** for more grains (production: 3–4 M+). [▶ 2:14](https://youtu.be/rkuNbceXolQ?t=134) — *[2026-07-28](../../recipes/2026-07-28_sph-granular-clumping-sand.md)*
- **nxEmitter**: wide/tall rectangle, **Shot** ~700, Speed 0; Display **Circle Filled**. [▶ 0:33](https://youtu.be/QDBN_Xu_l68?t=33) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*

## All recipes (44)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-21 · [Walking character crumbling to sand (nxBind + falloff release + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-10-20 · [Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-10-11 · [Tall sand piles with auto-sleep, wake-on-collision and a brittle block (nxMPM Materials + Auto Sleep + display channels)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Break up the hex-grid look of a cached granular sim (Create Point Cloud + Geometry Nodes jitter)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-22 · [Liquid stream steered along a helix spline (nxFlowField Along/To Spline + Turbulence, PBD, nxQuestion escape kill)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-09-08 · [Water jet eroding clumpy sand (nxFluids SPH Granular + Mixer liquid, nxBlend color → mapped granular settings)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-25 · [Flower-burst trails with speed-mapped thickness and per-vertex color (nxTrail, nxScale + nxTurbulence speed mapping)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-08-11 · [Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-28 · [Clumping sand / snow with SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-07-14 · [Springy constraint web rendered as trails (nxConstraints Birth connections + nxTrail Constraints mode)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2026-07-09 · [Wispy explosion-advected point cloud (nxExplosiaFX Particle Advect, Fast velocity advection, time-mapped forces, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-07-02 · [Macro water splash with thin sheets (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-29 · [Data Mapping basics: gravity by age/radius/brightness, cycling EFX fuel/smoke pulses (Mapping tab, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-22 · [Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-18 · [Liquid stream looping round a curve, meshed with motion blur (nxFollowGeo spline + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-15 · [Particle color at render time in Cycles and Eevee (nxEmitter Point Cloud export + Geometry Nodes attributes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-12 · [Viscous slime coiling over a head (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-06-08 · [Animating particle size with the Range layer and its ease curve (nxScale Range)](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)
- 2026-06-05 · [Additive particle vortex rendered as a point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, Point Cloud export)](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)
- 2025-08-12 · [Clean particle emission from a mocap character (xpJoin → Alembic → PLA bake)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-08-07 · [Procedural plasma ball (nxFollowGeo + nxTurbulence on particles, mtSplineFX arcs, mtEdgeSpline intersection forks)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-07-22 · [Hide a hard emission ring with a noisy opacity mask (nxColor layers + birth-rate spline)](../../recipes/2025-07-22_nxcolor-noise-opacity-emission-fade.md)
- 2025-04-29 · [Volume particle cloud coloured by an object's UV texture (texture surface emitter + nxUpres Color + Initial State)](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)
- 2025-04-01 · [Hide the hexagonal grid in granular sims (emitter Jitter + one-frame nxPush + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2024-12-31 · [Firework sparks off hand-drawn text (nxScale + nxQuestion kill + nxSpeed clamp mapped to Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-08-20 · [Stylised microscopic cells in a dish (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-06-04 · [Per-vertex colored trails rendered additively in Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-05-02 · [Feature notes: mtPointProject and new mtSubdivider modes (MeshTools 2024.2)](../../recipes/2024-05-02_feature-notes-mtpointproject-mtsubdivider-modes.md)
- 2024-04-30 · [Organic particle-trail swarm from a low-res cache (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-04-23 · [Particle-driven laser rays inside a sphere (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-12-26 · [Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-09-12 · [Activate a fluid sim by moving particles into a new group (nxQuestion Field + Random math, Set Group)](../../recipes/2023-09-12_nxquestion-field-group-switch-random.md)
- 2023-05-09 · [Viewport particle display types and rendering them (emitter Display tab + Display Render generator)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-04-17 · [Exploding planet: surface detail particles that ride the spinning sphere (displaced texture emission, Global Transform, color-driven offset)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Exploding planet: spin-speed-driven texture emission with clumping debris (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-03-28 · [Emit only from the fastest-moving parts of a mesh (xpVertexMap Vertex Speed layer + texture emission)](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)
- 2023-03-16 · [Sand logo reveal with only the hero grains simulated (nxFluids SPH Granular + static scatter from a vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-14 · [Particles that carry their emitter object's motion (Motion Inheritance linear + rotational, xpTurbulence)](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)
