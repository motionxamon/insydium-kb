# nxCollider — tool card

Mentioned in **23** recipes · 2023-03-16 → 2026-10-30 · hosts: Blender, C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Ctrl-drag a copy, rotate 180° and 90° → S-bend. Add a cube + **nxCollider** (scatter) after the exit: collisions work in Guide mode, not in Deform (particles aren't really there). [▶ 17:44](https://youtu.be/WJwIek6M8z8?t=1064) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- - Plane + **nxCollider** (some bounce, high friction, a little scatter); hide the plane. — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- **Wake Speed** 10.5 (just above Sleep Speed), Wake Spread 0. A sphere + **nxCollider** (bounce/friction 0) pushes grains awake; they re-settle and sleep again. [▶ 14:21](https://youtu.be/UT9_Aht5waE?t=861) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **Use Bounds** off → sparse solve, but then add a cube + **nxCollider** (friction) as the floor. Demo keeps the domain. [▶ 4:57](https://youtu.be/jItRyLgdjPg?t=297) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- Big plane + **nxCollider**: Bounce 0, decent Friction. **nxGravity** default. [▶ 3:18](https://youtu.be/M2yxZlZQBec?t=198) — *[2026-10-06](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)*
- **nxGravity**; **nxCollider** on plane, Bounce 0, some Friction. [▶ 1:49](https://youtu.be/yp5579on6J8?t=109) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- Fill another shape: swap the emitter object for a UV sphere; add **nxCollider** on it with **Inside normals**, Bounce 0, Friction 0 to contain it. [▶ 7:02](https://youtu.be/vglrHSL-uc4?t=422) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Big hidden plane + **nxCollider**: Bounce 0, Friction high (**80%**, up to 100 for clumping). **nxGravity** default. [▶ 0:57](https://youtu.be/rkuNbceXolQ?t=57) — *[2026-07-28](../../recipes/2026-07-28_sph-granular-clumping-sand.md)*
- Three Suzannes (Shift+D); **nxGravity**; **nxCollider** picking all three, Friction full (particles stick). Emitter Speed **8**, widen to ~12 to cover them. [▶ 3:58](https://youtu.be/QDBN_Xu_l68?t=238) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*
- - UV sphere just past the jet; **nxCollider** layer for it, bounce 0, friction 0. — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- - Floor cube (scaled past frame, hidden) as second nxCollider layer: bounce 0, small friction (~3) — a little goes a long way with FLIP/APIC. — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- - Big hidden plane as **nxCollider** (bounce 0, a little friction); **nxGravity** (default 9.8). — *[2026-06-29](../../recipes/2026-06-29_blender-data-mapping-basics.md)*
- **nxCollider**: Suzanne layer (bounce 0, a little friction, later less); plus a **cube** floor inside the bounds as its own layer (bounce 0, friction) — voxel solvers want volumetric colliders, not planes. [▶ 7:19](https://youtu.be/pz6LDGGeD5A?t=439) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*

## All recipes (23)
- 2026-10-30 · [Shaping particles, smoke and FLIP with warps (nxWarp Scroll / Bend / Helix / Twist — Deform, Guide, Flow modes)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-20 · [Outside-in disintegration of a particle volume (nxQuestion Neighbors → Set Group, speed-mapped forces)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-10-11 · [Tall sand piles with auto-sleep, wake-on-collision and a brittle block (nxMPM Materials + Auto Sleep + display channels)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Water, rubber gummies and sand in one solve, meshed and rendered (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Break up the hex-grid look of a cached granular sim (Create Point Cloud + Geometry Nodes jitter)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-08 · [Water jet eroding clumpy sand (nxFluids SPH Granular + Mixer liquid, nxBlend color → mapped granular settings)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-11 · [Liquid Fill preset with FLIP/APIC, mesh and separate foam emitter (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-28 · [Clumping sand / snow with SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-07-14 · [Springy constraint web rendered as trails (nxConstraints Birth connections + nxTrail Constraints mode)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2026-07-02 · [Macro water splash with thin sheets (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-29 · [Data Mapping basics: gravity by age/radius/brightness, cycling EFX fuel/smoke pulses (Mapping tab, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-22 · [Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-12 · [Viscous slime coiling over a head (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2025-05-13 · [Particle-to-particle collisions with pulsed "light" blasts (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-25 · [Feature notes: NeXus 2024.2 core rebuild — faster GPU solve and animated-geometry collisions](../../recipes/2024-04-25_feature-notes-nexus-2024-2-speed-collisions.md)
- 2024-04-02 · [Beading water droplets (nxFluids SPH surface tension + age-mapped nxGravity)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-08-22 · [Splashing rain rig (xpCollider Spawn on collision, xpJoin for many colliders)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-16 · [Volcanic crater terrain + low-poly collider (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)](../../recipes/2023-03-16_terraformfx-volcano-crater-lowpoly-collider-part-a.md)
