# Legacy video catalog — part 2 (2020-06-18 – 2022-09-16)

## Maintenance Training — ExplosiaFX

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Settings - Buoyancy & Vorticity** — https://www.youtube.com/watch?v=M1unG8LWO_U
  - What: per-channel buoyancy (positive vs negative flips the vertical motion of heat/fuel/smoke), vorticity for small curling detail and turbulence for natural random motion on a torus source.
  - Tools: xpExplosiaFX (Simulation tab), xpExplosiaFX Source tag.
  - Today: nxExplosiaFX (sources listed in the Sources tab); same buoyancy/vorticity concepts, plus nxVorticity/nxTurbulence on GPU.

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Settings - Substeps** — https://www.youtube.com/watch?v=Km9pfAIw2tM
  - What: when high pressure or high velocity sims need more substeps; CFL, min/max substeps, accuracy and max pressure iterations, tested on a 5000-pressure keyframed source.
  - Tools: xpExplosiaFX (Simulation ▸ Substeps), xpExplosiaFX Source tag.
  - Today: nxExplosiaFX; substeps also set globally in NeXus Project Settings (C4D 2026.1).

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Burn Model, Dissipation & Diffusion** — https://www.youtube.com/watch?v=FkCLZQGD95o
  - What: chemical vs custom burn model on a burning oil patch and a Bunsen burner, separate fuel and heat objects for ignition, then dissipation and diffusion to shape flame and smoke.
  - Tools: xpExplosiaFX, xpExplosiaFX Source tag (noise shaders in heat/fuel channels).
  - Today: nxExplosiaFX (burn settings on the object, sources in the Sources tab); C4D 2025.3+ can also exchange with Pyro.

- **2022-09-16 — MNT Training - Dynamics - ExplosiaFX - The Basics - Controlling EFX with xpModifiers** — https://www.youtube.com/watch?v=CdnHYfeOHFc
  - What: steering a smoke/fire volume with an attractor, turbulence and a spline-driven flow field, then bending it with Bend, Twist and Spline Wrap deformers.
  - Tools: xpExplosiaFX, xpAttractor, xpTurbulence, xpFlowField, C4D deformers.
  - Today: nxExplosiaFX + nxAttract/nxTurbulence/nxFlowField; nxWarp (Path, Bend, Twist, Helix) now deforms smoke directly.

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Tutorials - Flame & Embers** — https://www.youtube.com/watch?v=BDoW0Qc5KCQ
  - What: a sconce fire where a painted vertex map limits which coal polygons burn, flame look-dev in the Simulation tab, a watertight collider made from the high-res mesh, and ember particles advected by the flame.
  - Tools: xpExplosiaFX, Source tag with vertex map, xpVertexMap, xpEmitter (advection), xpScale, xpCache.
  - Today: nxExplosiaFX + nxEmitter advected by the smoke; use nxFalloff (Object/Attribute) instead of the vertex-map trick where possible.

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - The Basics - Display Options** — https://www.youtube.com/watch?v=91p9Vu5Zs0s
  - What: showing each channel (fuel, smoke, temperature, velocity) in the viewport, slice count, trail display of the flow, and colour/opacity controls for analysing a sim.
  - Tools: xpExplosiaFX (Display tab).
  - Today: nxExplosiaFX in the new shared NeXus viewport renderer (better voxel drawing, 2026.1).

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Rendering Fire & Smoke** — https://www.youtube.com/watch?v=0ia33svoTX0
  - What: a Cycles 4D volume material where temperature drives emission through a Blackbody node and map-range nodes, then scattering/absorption for smoke, plus thick hydrocarbon smoke from a flamethrower.
  - Tools: xpExplosiaFX (cached), Cycles 4D volume, Blackbody, Map Range and Wavelength nodes.
  - Today: render nxExplosiaFX in Redshift (C4D 2026.1 adds a default Redshift smoke material); the temperature-to-blackbody logic is the same.

## Maintenance Training — Fluids

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 4 - Teacup Splash Mesh & Render** — https://www.youtube.com/watch?v=LYd96W-nRUY
  - What: bringing cached splash and ripple particles into a second artist's teacup scene (fixing offset position), meshing them with filters for a smooth surface, then HDRI lighting and a Cycles 4D render.
  - Tools: xpSystem copy/paste with xpCache, xpOpenVDBMesher (filters), Cycles 4D.
  - Today: nxMesher (Zhu-Bridson, Detail Aware smoothing) on an nxCache; render in Redshift.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 3 - Intro to Splash** — https://www.youtube.com/watch?v=L0b8IaypNqo
  - What: filling a tank with a one-frame Shot emission, then crown splashes from xpSplash combined with xpSheeter, and tuning their look.
  - Tools: xpEmitter (Shot), xpCollider (Normals Inside), xpFluidFX, xpSplash, xpSheeter.
  - Today: nxFluids + nxSplash; nxSheeter in NeXus 2026.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 2 - Intro to FluidFlip** — https://www.youtube.com/watch?v=8ly9TMUbBAY
  - What: a domain-based river/pool sim with static and animated colliders; APIC vs FLIP, weak spring, liquid level and viscosity.
  - Tools: xpFluidFLIP (Domain tab, solver settings, fluid properties).
  - Today: nxFluids FLIP/APIC + nxMesher; 2026.1 adds non-Newtonian, Wall Friction and Mixer.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 1 - Solver Choice: Introduction** — https://www.youtube.com/watch?v=3e6J5kMV0o8
  - What: the same emitter/gravity/collider box run through the three CPU fluid solvers to show how to pick one.
  - Tools: xpFluidPBD, xpFluidFX, xpFluidFLIP, xpGravity, xpCollider.
  - Today: one nxFluids object with PBD / SPH / FLIP-APIC modes; nxMPM for granular and solid-like materials.

## Premium Training — Drawing with Particles

- **2022-09-16 — Premium Training - Drawing with Particles - 03 - Wet Maps** — https://www.youtube.com/watch?v=Jj814YfqMzY
  - What: turning particles that touch a surface into a vertex-map wet map (shown with a material shader) to paint a logo onto a shipping container, then exporting to Alembic.
  - Tools: xpWetMap tag, xpEmitter, wet map shader, Alembic export.
  - Today: nxFalloff Wet mode + nxFalloffMap (falloffs → vertex map / vertex colour tags, C4D 2026.1).

- **2022-09-16 — Premium Training - Drawing with Particles - 02 - Stencils** — https://www.youtube.com/watch?v=KvpS0GGSCUg
  - What: spraying particles through an extruded stencil spline so only the cut-out reaches the container wall, using a Collision-deformer collider mesh and Freeze Particles actions per system.
  - Tools: xpEmitter, xpCollider, C4D Collision deformer, xpQuestion + xpAction (Freeze Particles).
  - Today: nxCollider + nxSticky or an nxQuestion action on GPU; the CPU setup still works.

## Premium Training — Sci-Fi FUI

- **2022-09-16 — Premium Training - Sci-Fi FUI - 04 - Compositing** — https://www.youtube.com/watch?v=EDI4asV0UlQ
  - What: compositing the Cycles 4D beauty and FUI passes in After Effects, using the imported 3D camera to track a masked wipe-on to the moving screen.
  - Tools: After Effects (3D camera data, masks).
  - Today: still current (compositing workflow).

- **2022-09-16 — Premium Training - Sci-Fi FUI - 03 - Rendering** — https://www.youtube.com/watch?v=HYAjqXrexzk
  - What: layering the scene and using Takes to render a beauty pass and a separate FUI pass in Cycles 4D, refining line thickness and colour.
  - Tools: C4D Layers and Takes, Cycles 4D, xpTrail/xpGenerator-based FUI elements.
  - Today: same Takes approach, rendered in Redshift.

- **2022-09-16 — Premium Training - Sci-Fi FUI - Introduction** — https://www.youtube.com/watch?v=FCmTfd31EKE
  - What: course overview of a contaminated-lab shot: oozing goo with a fluid solver, colliders and a flow field, plus an FUI built from emitters and generators, rendered in passes and comped.
  - Tools: xpFluidFX, xpCollider, xpFlowField, xpEmitter, xpGenerator, Cycles 4D.
  - Today: nxFluids SPH (viscous) + nxFlowField, render in Redshift.

## Premium Training — Bonus Videos

- **2022-09-16 — Premium Training - Bonus Videos - Cycles 4D Range Mapping Node** — https://www.youtube.com/watch?v=FwpvsvZ0Cvs
  - What: building a reusable range-mapping node group in Cycles 4D to remap particle colour/radius data for shading.
  - Tools: xpEmitter, Cycles 4D node groups (particle data inputs).
  - Today: Redshift's own range/remap nodes; on the sim side, NeXus Mapping or nxFalloff Modifier Remap.

- **2022-09-16 — Premium Training - Bonus Videos - Falloff Positioning Without Fields** — https://www.youtube.com/watch?v=AV1PQynoC5o
  - What: decoupling and animating a modifier falloff before C4D R20 by driving it from a null via XPresso.
  - Tools: xpSpeed, xpFlowField (Surface Normal), XPresso.
  - Today: not needed any more: C4D Fields (R20+) or nxFalloff objects move freely.

## Premium Training — Fireworks

- **2022-09-16 — Premium Training - Fireworks - 05 - Compositing** — https://www.youtube.com/watch?v=CEW7ZMVsmjc
  - What: After Effects comp of the Cycles 4D fireworks render, using the emission pass, blurred additive layers and contrast for bloom, plus sharpening.
  - Tools: After Effects (emission pass, blur, blend modes).
  - Today: still current (or Redshift bloom in-render).

- **2022-09-16 — Premium Training - Fireworks - Introduction** — https://www.youtube.com/watch?v=FoWnGY5mC1w
  - What: course overview of a custom fireworks rig with control over lift, break and shape, several firework styles, emissive materials and compositing.
  - Tools: xpEmitter, spawning-based rig, Cycles 4D.
  - Today: nxSpawn (On Death / At Age sub-layers) for the break stages.

## Premium Training — Infectio

- **2022-09-16 — Premium Training - Infectio - 05 - Compositing** — https://www.youtube.com/watch?v=6-d380gH6Rc
  - What: simple After Effects comp of the slime-mould shots with colour correction and alpha handling.
  - Tools: After Effects.
  - Today: still current.

- **2022-09-16 — Premium Training - Infectio - 02 - Skull Scene** — https://www.youtube.com/watch?v=FWFiCHoK0AA
  - What: applying the infection set-up to a sculpted skull scene: tidying with System Sort, combining and remeshing the geometry with a VDB mesher and adding UVs so particles can emit and spread.
  - Tools: xpInfectio, xpColor, xpSystem (System Sort), xpOpenVDBMesher (remesh).
  - Today: nxInfectio; remesh with mtRemesh or C4D Volume Builder/Mesher.

- **2022-09-16 — Premium Training - Infectio - 01 - The Spread** — https://www.youtube.com/watch?v=D9K6UGwlc8s
  - What: infection basics on a texture-emitted plane: groups by colour, incubation and how many neighbours are needed to propagate.
  - Tools: xpEmitter (emit from texture), xpInfectio, xpGroup, Data Mapping.
  - Today: nxInfectio (+ NeXus Mapping).

- **2022-09-16 — Premium Training - Infectio - Introduction** — https://www.youtube.com/watch?v=CX9MB32S3rI
  - What: course overview: slime mould spreading over a skull scene with spores growing from it, SSS mould material and trail-rendered spores.
  - Tools: xpInfectio, xpOpenVDBMesher, xpTrail.
  - Today: nxInfectio + nxTrail; nxBioLogic (Physarum) for slime-mould-like growth.

## Premium Training — Logo Form

- **2022-09-16 — Premium Training - Logo Form - 02 - Something from Nothing** — https://www.youtube.com/watch?v=8zUthpInoyI
  - What: blowing particles off a logo (flow field, reversed attractor, shader-mapped speed) and reversing the sim so the logo appears to form from a cloud.
  - Tools: xpEmitter (from a Connect of the logo), xpFlowField, xpAttractor, xpSpeed, xpColor, xpHistory.
  - Today: nxFlowField / nxExplode with nxFalloff; play the nxCache backwards for the forming effect.

## Premium Training — Ivy Growth

- **2022-09-16 — Premium Training - Ivy Growth - 04 - Ruins** — https://www.youtube.com/watch?v=8T1qJMhTCIw
  - What: growing the ivy rig up a sculpted church-window ruin after combining and remeshing the separate pieces so branches do not slip into gaps, then tuning branch seeds and speeds.
  - Tools: particle ivy rig (branch emitters, xpTrail), xpOpenVDBMesher (remesh), xpCache.
  - Today: Taiao (growth points, growth animation) or nxDendrite branches (NeXus 2026).

## Maintenance Training — XP Countdown

- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Granular & Advection Render** — https://www.youtube.com/watch?v=fM2RNmLJsYQ
  - What: rendering the "3 to 2" granular crumble and smoke-advection shot, reusing camera/lights and matching colours across numbers in Cycles 4D materials.
  - Tools: xpFluidFX granular, xpExplosiaFX advection, Cycles 4D principled/volume.
  - Today: nxMPM (sand) or nxFluids SPH Granular + nxExplosiaFX; render in Redshift.

- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Cameras, Lights, & Rendering** — https://www.youtube.com/watch?v=pIzIfG6Jpxc
  - What: one fixed camera and a light rig tested on a combined scene (splash, cloth tearing, liquids, EFX wipe), plus Cycles 4D render settings and firefly clamping.
  - Tools: Cycles 4D (integrator, clamping), xpClothFX tearing, xpExplosiaFX.
  - Today: Redshift; cloth tearing via nxDeformer + nxConstraints (2026.1) or CPU xpClothFX.

## Release updates and sneak peeks (2022)

- **2022-09-15 — NeXus Sneak Peek - GPU - Release Update - Sept '22** — https://www.youtube.com/watch?v=BYajB1dbupw
  - What: first NeXus wave: GPU vs CPU speed for SPH, PBD and granular fluids, live foam, spring constraints and the reworked turbulence (persistence, lacunarity).
  - Tools: early nxFluids, nxFoam, nxConstraints, nxTurbulence, nxRotate, nxWind.
  - Today: G3 nxSystem / nxEmitter objects in NeXus 2026, with FLIP and nxMPM added.

- **2022-09-13 — Taiao Sneak Peek - Growth Tab - Release Update - Sept '22** — https://www.youtube.com/watch?v=oq1QIo9qZP8
  - What: per-layer growth controls (trunk, branch, leaf, flower, custom) with variation and Fields-driven offset growth.
  - Tools: Taiao toPlant (Growth tab), Linear Field.
  - Today: still current (growth expanded in 2023.3).

- **2022-09-13 — MeshTools Sneak Peek - mtFractal - Release Update - Sept '22** — https://www.youtube.com/watch?v=2KCkHZMs73s
  - What: procedural 3D fractal copies of any object (Tree, Fern, Koch, Dragon) with per-level controls, then particles and trails from the result.
  - Tools: mtFractal, xpEmitter, xpTrail.
  - Today: still current (nxTrail for the GPU trails).

- **2022-05-11 — INSYDIUM nxFluids Tech Preview** — https://www.youtube.com/watch?v=dmKulhMfDbg
  - What: GPU tech demo of the combined nxFluids object (PBD and SPH, including granular) against xpFluidFX, cross-platform on AMD, NVIDIA and Apple.
  - Tools: nxFluids (PBD / SPH), xpFluidFX.
  - Today: nxFluids (+ FLIP, Mixer) and nxMPM for granular.

- **2022-03-16 — Taiao Sneak Peek – Coming Soon to INSYDIUM Fused** — https://www.youtube.com/watch?v=5E4Fp9Q0L84
  - What: first look at the layered plant builder: trunk/branch/leaf/custom-object layers, leaf shaping curves, an orange tree, a fern and a flower.
  - Tools: Taiao toPlant (trunk, branch, leaf, flower, custom object layers).
  - Today: still current.

- **2022-03-10 — TerraformFX Sneak Peek - Coming Soon to INSYDIUM Fused.** — https://www.youtube.com/watch?v=VPJbYtZaTPg
  - What: the grid operator with a brush tool for sculpting, hydraulic erosion, and roads/rivers from splines with clone-along-road.
  - Tools: tfGrid (Grid brush), tfPath, tfRoad, erosion filter.
  - Today: still current (+ Advanced Terrain Shader, tfDistribute in 2024).

- **2022-03-03 — MeshTools Sneak Peek – Coming Soon to INSYDIUM Fused** — https://www.youtube.com/watch?v=OONMWPXQoj8
  - What: inset with extrude divisions, shape curve and twist; uniform/adaptive remeshing; spline resampling with growth animation.
  - Tools: mtInset, mtRemesh, mtSplineSample.
  - Today: still current.

- **2022-02-17 — INSYDIUM xpFluidGPU - Tech Preview** — https://www.youtube.com/watch?v=leeZ8I5Ied8
  - What: first GPU tech demo: a PBD waterfall switched to GPU on the emitter's GPU tab, still mixing in CPU modifiers.
  - Tools: xpFluidGPU, xpFluidPBD, xpGravity, xpRotator.
  - Today: superseded by nxFluids PBD (orange emitter in G2, nxEmitter in G3).

## MeshTools / Taiao / TerraformFX tutorials

- **2022-06-01 — INSYDIUM MeshTools - Crystal Smash Tutorial** — https://www.youtube.com/watch?v=9a95U9NtJ8g
  - What: a tetrahedron sphere remeshed and inset, with field-driven poly scaling and edge/shortest-path splines for glowing crystal shards breaking out.
  - Tools: mtRemesh, mtInset, mtPolyScale, mtEdgeSpline, mtShortestPath, mtSubdivider, C4D Fields.
  - Today: still current.

- **2022-04-21 — TerraformFX Tutorial - Guilin Landscape** — https://www.youtube.com/watch?v=JaWxygtVlY4
  - What: matching a Guilin reference with grid-operator mountains, a 3D winding road drawn in top/front views, and erosion ordered after the path; high-res foreground and low-res background terrains.
  - Tools: tfTerrain, tfGrid, tfPath, tfRoad, erosion operator.
  - Today: still current.

- **2022-03-31 — Taiao Tutorial - Palm Tree Build** — https://www.youtube.com/watch?v=TUs1-T0I2o0
  - What: a leaning palm tree built from a trunk layer, crown branches, leaves and a custom coconut object on a TerraformFX sand terrain.
  - Tools: Taiao toPlant (trunk, branch, leaf, custom object), tfTerrain.
  - Today: still current.

- **2021-08-19 — MeshTools Tutorial - Crystal Growth** — https://www.youtube.com/watch?v=iNildRnEGAM
  - What: a low-poly TerraformFX terrain with stacked subdivide/inset animation for growing crystal shapes, rendered with subsurface scattering in Cycles 4D.
  - Tools: tfTerrain, mtSubdivider, mtInset, Cycles 4D SSS.
  - Today: still current for MeshTools; render in Redshift.

- **2021-08-12 — MeshTools Tutorial - Shortest Path Geometry Ripple** — https://www.youtube.com/watch?v=3TlsRpyG7n8
  - What: a cube that ripples on through subdivision and inset, with stylised splines growing along shortest paths across the mesh; Alembic export.
  - Tools: mtSubdivider, mtInset, mtShortestPath, mtShell, Alembic.
  - Today: still current.

- **2021-08-09 — MeshTools Tutorial - Organic Geometry** — https://www.youtube.com/watch?v=GfxbCce61n0
  - What: layering insets on a torus and animating them non-destructively with fields, shaders and noises for organic growth.
  - Tools: mtInset (stacked), mtSubdivider, mtEdgeSpline, C4D Fields/noise.
  - Today: still current.

- **2021-07-26 — TerraformFX - Mountain Landscape Tutorial** — https://www.youtube.com/watch?v=ifwFEGPMgyM
  - What: how operators build a terrain (black-and-white analysis display, spline and noise generators), then a mountain range with erosion.
  - Tools: tfTerrain, generator operators (spline, noise), erosion filters.
  - Today: still current (+ Advanced Terrain Shader).

## X-Particles — xpBullet Tutorials

- **2021-08-04 — X-Particles - xpBullet Tutorial - Domino Rig** — https://www.youtube.com/watch?v=wz-3egYgShI
  - What: a procedural domino rig: spawned particles spaced along a trail path, scaled up, generated as dominoes and toppled with Bullet rigid bodies.
  - Tools: xpBullet Collider / Rigid Body tags, xpSpawn, xpTrail, xpFlowField, xpGenerator, xpScale.
  - Today: still current on CPU (Bullet has no nx equivalent; GPU rigid bodies announced Nov 2026, not shipped).

- **2021-07-29 — X-Particles - xpBullet Tutorial - Destruction Scene** — https://www.youtube.com/watch?v=X74ARe24Bes
  - What: shattering a wall into fragments and smashing it with Bullet rigid bodies, including Bullet tags placed directly on an emitter.
  - Tools: xpShatter, xpBullet Collider / Rigid Body tags, xpGenerator.
  - Today: nxShatter (2026.1, can be driven by nxMPM damage); xpShatter + Bullet still works.

## Sneak Peeks (2020–2021)

- **2021-07-14 — xpBullet - Sneak Peek** — https://www.youtube.com/watch?v=LaVQgqpIZQ0
  - What: Bullet collisions for particles: a disintegrating running man, accurate collisions per display shape, collision questions that trigger spawning, and trails used with avoid.
  - Tools: xpBullet Rigid Body tag, xpQuestion (Bullet collision) + xpAction (Unstick, Spawn), xpTrail, xpAvoid, xpColor.
  - Today: CPU Bullet still current; nxMPM for soft/brittle behaviour on GPU.

- **2021-06-29 — INSYDIUM TerraformFX - Coming Soon!** — https://www.youtube.com/watch?v=3A9ZFvSGKd4
  - What: first TerraformFX preview: layered noise/gradient generators, fold, 2D/3D hydraulic, thermal and coastal erosion, exported altitude/slope/erosion maps, a volcano build and field-masked groups.
  - Tools: tfTerrain, generators and filters, erosion filter, terrain operator shader, Cycles 4D.
  - Today: still current.

- **2021-06-08 — INSYDIUM MeshTools - Coming Soon!** — https://www.youtube.com/watch?v=G1IPg2FZGDA
  - What: first MeshTools preview: edge splines (outline, curvature, contour, intersection, texture-driven), noise-driven insets with a box-field wipe, and subdivider city growth.
  - Tools: mtEdgeSpline, mtInset, mtSubdivider, C4D Fields.
  - Today: still current.

- **2021-05-18 — xpOpenVDBImporter - Sneak Peek** — https://www.youtube.com/watch?v=W6vcdGdhXjA
  - What: loading VDB files/sequences with channel display and time controls, then instancing volumes per particle or with MoGraph Matrix.
  - Tools: xpOpenVDBImporter, Cycles 4D instance tag, MoGraph Matrix/effectors.
  - Today: no direct nx equivalent; xpOpenVDBImporter or Redshift volumes.

- **2021-04-27 — xpOpenVDBMesher - Transfer Foam - Sneak Peek** — https://www.youtube.com/watch?v=djUHxGykGdg
  - What: mesher option that writes an animated vertex map from foam data for texturing fluid meshes, with smoothing and a remap curve.
  - Tools: xpOpenVDBMesher (Transfer Foam), xpFoam, xpFluidFX.
  - Today: nxFoam + nxMesher; the CPU Transfer Foam route still works.

- **2021-04-13 — xpOpenVDBMesher - UV Advection - Sneak Peek** — https://www.youtube.com/watch?v=x8aQxHLFkoc
  - What: UV advection so a texture projected on a fluid mesh moves with the particles, with a reference frame.
  - Tools: xpOpenVDBMesher (UV Advection), xpFluidFX.
  - Today: nxMesher UV advection (2026.1).

- **2020-06-29 — xpExplosiaFX - Sneak Peek** — https://www.youtube.com/watch?v=RTO8aeq97ao
  - What: the 2020 EFX update: OpenGL volume display, deformer support (Bend, Twist, Spline Wrap), new burn models, separate vorticity/turbulence and an Up-Res tab.
  - Tools: xpExplosiaFX (display, Up-Res), C4D deformers.
  - Today: nxExplosiaFX + nxWarp on smoke; nxUpres.

- **2020-06-24 — xpFluidFLIP - Sneak Peek** — https://www.youtube.com/watch?v=-7eA4jDPPWk
  - What: the rewritten domain solver with APIC vs FLIP comparison and new collisions with static, fast-moving and rotating objects.
  - Tools: xpFluidFLIP (APIC / FLIP).
  - Today: nxFluids FLIP/APIC.

- **2020-06-22 — xpFlowField - Sneak Peek** — https://www.youtube.com/watch?v=pUgnMvQluts
  - What: the new layer system: along-spline, random and curl layers with blend modes, strength and falloff, flow trail display, surface tangent flow on a hand.
  - Tools: xpFlowField (layers).
  - Today: nxFlowField (Cyclic layer in 2026.1) or nxWarp Flow / nxFollowGeo.

## Vertex talks

- **2021-02-25 — Vertex 2021 - ExplosiaFX Tutorial - Rendering Fire & Smoke** — https://www.youtube.com/watch?v=fN7emTrvW_M
  - What: free public release of the same Cycles 4D fire-and-smoke rendering lesson as the Maintenance Training video above.
  - Tools: xpExplosiaFX, Cycles 4D Blackbody/Map Range/volume nodes.
  - Today: nxExplosiaFX rendered in Redshift.

## Other (no technique)

- INSYDIUM Fused - Out Now! (2021-07-22) — https://www.youtube.com/watch?v=2WL2Xziq-Fo
- X-Particles Fluids - Additional Content - OUT NOW! (2021-03-30) — https://www.youtube.com/watch?v=cV37Hv1YrbE
