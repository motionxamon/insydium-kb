# xpSystem — tool card

Mentioned in **13** recipes · 2023-03-16 → 2024-11-01 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- - xpSystem stripped to the NeXus, Emitters and Utilities folders (no CPU modifiers/questions needed). — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- - Bust model with existing wrinkles/hair detail (smooth meshes look less interesting). xpSystem with the CPU folders (Dynamics, Generators, Modifiers, Questions) deleted. — *[2024-10-04](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)*
- Display single color **black**. xpSystem ▸ only modifiers in the same system; Ctrl-drag to duplicate → "infecting" system, emitters 15 particles. [▶ 46:19](https://youtu.be/qaso-gPGBnI?t=2779) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*
- xpSystem; square emitter at the terrain side, wide and flat. Emission **Shot, 30** particles; **No Intersection radius ~16 cm**; Speed 150, Variation 60. Display Arrows filled; Extended Data ▸ Rotation **Tangential**. [▶ 5:08](https://youtu.be/yqfkRKgW1Mo?t=308) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- **xpSystem**, delete the default emitter. Generators ▸ **xpShatter**, logo as child. Display: edge color near black. [▶ 21:34](https://youtu.be/U8zISIlBq90?t=1294) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*
- New **xpSystem** "system detail" ▸ Object: **Only Modifiers in Same System** (ignores Part 1's nxDrag/nxConstraints). [▶ 5:59](https://youtu.be/3Qd2e6ZCN6M?t=359) — *[2023-04-17](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)*
- **xpSystem** ("system motion") with its **xpEmitter**: Emitter Shape **Object** = sphere, Emission Source **Texture** → Texture tab: link the sphere's texture tag (emit from bright parts of the Color channel, color particles from it). Speed **0**. [▶ 31:41](https://youtu.be/6sdlTZsi9kQ?t=1901) — *[2023-04-16](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)*
- xpSystem; delete the default emitter. Generators ▸ **xpShatter**; Inset as child. Voronoi layer + Point Generator (40 points by default; Display ▸ Draw Shatter Points shows them). [▶ 2:38](https://youtu.be/75GHeuPO3rU?t=158) — *[2023-04-13](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)*
- - xpSystem ▸ xpEmitter "emitter grains": Display Circles Filled + viewport **Ambient Occlusion** (to read clumps), HUD on. — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- New **xpSystem** ("System EFX", own icon color); emitter shape **Object** → source mesh, Emit From **Polygon Area**, **Invert** normal direction (MoText normals point inward). [▶ 7:45](https://youtu.be/OKRG2FUtXjc?t=465) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- **xpSystem** emitter: shape **Cylinder**, Pitch **90°**, about **60 × 7**, speed 0; sits just above the crater collider. [▶ 24:19](https://youtu.be/OVUcKWkhUFY?t=1459) — *[2023-03-16](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)*
- Static set: new xpSystem with **Only Modifiers in Same System** (ignores the NeXus modifiers), Mode Simulate, speed 0, **Shot**; shape **Object** → high-res terrain, **Polygon Area**, count **100,000**; drop the **snow vertex map** into the object **Selection** field → grains only in the grooves. [▶ 34:07](https://youtu.be/OVUcKWkhUFY?t=2047) — *[2023-03-16](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)*

## All recipes (13)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-10-04 · [Organic wrinkle growth creeping over a statue (nxConstraints Forces repulsion + xpDeformer, vertex-map-driven nxQuestion groups)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-04-19 · [Logo shatters on time, re-shatters on impact, spawns debris and dust (xpShatter layers + xpDynamics Push + collider Spawn + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-17 · [Exploding planet: surface detail particles that ride the spinning sphere (displaced texture emission, Global Transform, color-driven offset)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Exploding planet: spin-speed-driven texture emission with clumping debris (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-04-13 · [Crystal that crumbles shard by shard (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Reveal a mesh only where smoke passes through it (Cycles 4D Point Density on the mesh, staggered xpExplosiaFX emitters)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-16 · [Sand logo reveal with only the hero grains simulated (nxFluids SPH Granular + static scatter from a vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
