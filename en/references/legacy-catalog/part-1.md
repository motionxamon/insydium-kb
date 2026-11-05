# Legacy video catalog — part 1 (2022-09-16 – 2022-12-16)

## INSYDIUM Official Training — Snow Peel
- **2022-12-16 — Snow Peel - Part 1** — https://www.youtube.com/watch?v=0dJbuWbVDRI
  - What: builds a snow shell around a lollipop by meshing particles, peels it away with keyframed Boolean spheres, and sheds snow particles where the shell disappears.
  - Tools: xpEmitter, xpOpenVDBMesher, C4D Boolean, xpQuestion/xpAction (inside-object test), xpTurbulence, xpWind.
  - Today: nxMesher + nxQuestion on nxEmitter; for physically crumbling snow use nxMPM / nxMaterial Snow presets with nxBind.
- **2022-12-16 — Snow Peel - Part 2** — https://www.youtube.com/watch?v=CDG448vmrm8
  - What: splits the effect into several emitters (surface vs volume, big chunks vs fine dust), fixes low volume-emission counts with Max Retries and adds variation through data mapping on modifiers.
  - Tools: multiple xpEmitters (Object volume/surface), Data Mapping tab, xpTurbulence, xpPainter (stuck particles), xpQuestion.
  - Today: nxEmitter per layer + NeXus Mapping tab and per-layer nxFalloff on layered nxTurbulence.
- **2022-12-16 — Snow Peel - Part 3** — https://www.youtube.com/watch?v=CqEkvYk4KMc
  - What: Cycles 4D lighting, a custom sticky-candy material built from gradient-remapped nodes, and custom geometry for render instances.
  - Tools: Cycles 4D (Principled shader, gradient remap), Cycles 4D Instance tag.
  - Today: same shading ideas in Redshift (Cycles 4D is legacy); instance geometry via nxGenerator.
- **2022-12-16 — Snow Peel - Part 4** — https://www.youtube.com/watch?v=mBsW0-e1DZA
  - What: trims particle counts per emitter, finalises the snow motion, caches it (disabling the Boolean for speed) and sets up separate render elements.
  - Tools: xpCache, xpQuestion, xpTurbulence, Cycles 4D.
  - Today: nxCache (Auto Frame Range, Disk Reserve) — workflow still current.
- **2022-12-16 — Snow Peel - Part 5** — https://www.youtube.com/watch?v=mCUOwczLRWE
  - What: final lighting fixes for colour vibrancy, material tweaks, render-time subdivision of the Boolean mesh and output settings.
  - Tools: Cycles 4D Object tag (displacement/subdivision), Cycles 4D lights and output.
  - Today: Redshift lights + render-time subdivision; no X-Particles change needed.

## INSYDIUM Official Training — Particle Tree
- **2022-12-16 — Particle Tree - Part 1** — https://www.youtube.com/watch?v=dryt88_zKnc
  - What: first of three particle Christmas-tree systems — particles emitted from helix spline edges swirl upward under a flow field and turbulence, then get render-time size control.
  - Tools: xpEmitter (Object, edges), xpFlowField, xpTurbulence, xpSpeed, Cycles 4D Instance tag.
  - Today: nxEmitter from splines + nxFlowField / nxWarp Helix (Guide mode) + nxTurbulence.
- **2022-12-16 — Particle Tree - Part 2** — https://www.youtube.com/watch?v=eGSVsEtIPM0
  - What: a flat ribbon of particles driven by a linear flow field, then deformed around a helix with a C4D Spline Wrap deformer, with snow and bauble emitters.
  - Tools: xpEmitter (cube), xpFlowField (To Spline layer), C4D Spline Wrap, xpTrail.
  - Today: nxWarp Helix or Path (Flow mode) does the wrap natively; nxFollowGeo as stable alternative.
- **2022-12-16 — Particle Tree - Part 3** — https://www.youtube.com/watch?v=p2Pc6TPpiQo
  - What: refines the spline-wrap sim, borrows render settings from the first system and builds procedural shiny and glass bauble materials in Cycles 4D, then a test render.
  - Tools: Cycles 4D (Principled shader, node soloing), xpCache.
  - Today: rebuild materials in Redshift; simulation part maps to nxWarp Helix.
- **2022-12-16 — Particle Tree - Part 4** — https://www.youtube.com/watch?v=e0GeVgSBOxo
  - What: wispy detail system — particles emitted from a noise-textured sweep around the helix, spiralled down along the spline with a flow field and played in reverse.
  - Tools: C4D Sweep, xpEmitter (shader/texture emission), xpFlowField (Along Spline layer), xpTurbulence, xpCache (reverse).
  - Today: nxEmitter shader emission + nxFlowField / nxWarp Helix; reverse via cache playback.
- **2022-12-16 — Particle Tree - Part 5** — https://www.youtube.com/watch?v=8VOG4fkZUMY
  - What: combines the three systems and re-times them by offsetting cache playback, then finalises render output.
  - Tools: xpCache (offset, hold), Cycles 4D output.
  - Today: nxCache frame range / offset — still current.

## INSYDIUM Official Training — NeXus 2022
- **2022-11-09 — nxConstraints Tutorial 2022** — https://www.youtube.com/watch?v=yTwVv5s8BGU
  - What: particles on an animated split cube are linked with spring constraints that break under stress for a tearing effect, finished with extra NeXus modifiers.
  - Tools: xpEmitter (orange/GPU), nxConstraints (search radius, max connections, stiffness, breaking), nxTurbulence.
  - Today: G3 nxConstraints (same layers) + nxPin for anchoring; nxDeformer adds mesh tearing in 2026.1.
- **2022-11-02 — nxPush Tutorial 2022** — https://www.youtube.com/watch?v=vG4zYLbhuMk
  - What: GPU particle-particle push for packed stylised sims, radius animation via nxScale and a noise field, scaled up to real-time sand.
  - Tools: xpEmitter (CPU→GPU colour switch), nxPush, nxScale (shader field), C4D Fields.
  - Today: nxPush still current; for physical sand use nxMPM / nxMaterial Sand presets.
- **2022-10-20 — nxFluids Tutorial 2022** — https://www.youtube.com/watch?v=JCd4i0xZDbo
  - What: logo splash — water bursts from an extruded cog, swirls around it and blasts outward, art-directed in real time on the GPU.
  - Tools: nxFluids (PBD), nxTurbulence, nxAttract, nxRotate, nxExplode, nxDrag.
  - Today: nxFluids FLIP/APIC + nxMesher for liquid look (PBD still available); nxWarp Helix for the swirl.

## Premium Training — Ivy Growth
- **2022-09-16 — Ivy Growth - 01 - Branching System** — https://www.youtube.com/watch?v=YbNQ7msv6-c
  - What: plant anatomy primer, then a main stem / lateral shoot / petiole branching hierarchy that creeps over surfaces.
  - Tools: xpBranch (sub-branches), xpFollowSurface, xpTrail, xpAvoid.
  - Today: nxDendrite (branches) + nxFollowGeo; xpBranch remains the CPU route.
- **2022-09-16 — Ivy Growth - 02 - Tropism** — https://www.youtube.com/watch?v=bAYTV6vpzB0
  - What: replaces random bending with controlled growth toward a light source and around obstacles.
  - Tools: xpBranch, xpDirection, xpAvoid, xpFollowSurface.
  - Today: nxDendrite + nxAttract / nxAvoid; nxBioLogic for differential growth.
- **2022-09-16 — Ivy Growth - 03 - Leaves** — https://www.youtube.com/watch?v=w3g0PjQk8Co
  - What: places simple leaf planes at branch tips with correct position, orientation, scale and unfurling, and builds branch geometry.
  - Tools: xpGenerator, C4D deformers on leaf planes, UVW tags, xpSplineMesher.
  - Today: nxGenerator (or Taiao toLeaf for botanical leaves).
- **2022-09-16 — Ivy Growth - 05 - Rendering** — https://www.youtube.com/watch?v=Q6Fs8GOHsjs
  - What: camera setup with safe frames and focus nulls, sun/environment lighting and a translucent leaf shader with per-leaf variation.
  - Tools: Cycles 4D (camera, translucency shader), C4D cameras.
  - Today: Redshift equivalents; no X-Particles change.
- **2022-09-16 — Ivy Growth - 06 - Compositing** — https://www.youtube.com/watch?v=ybC7vFu8VD0
  - What: After Effects grade, bloom and flares using Cryptomatte passes from Cycles 4D.
  - Tools: Cycles 4D Cryptomatte, After Effects.
  - Today: still current (Redshift Cryptomatte).

## Premium Training — Drawing with Particles
- **2022-09-16 — Drawing with Particles - 01 - Methods** — https://www.youtube.com/watch?v=wPDMjtNChWA
  - What: compares ways to draw a graffiti path with particles: spline emission, follow-spline and spline-flow, and their multi-segment limits.
  - Tools: xpEmitter (Emit from Object quick tool), xpFollowSpline, xpSplineFlow.
  - Today: nxFollowGeo (multi-spline) or nxWarp Path.
- **2022-09-16 — Drawing with Particles - 04 - Graffiti** — https://www.youtube.com/watch?v=ZOa2ZU6Ot6I
  - What: free-form spray-can graffiti on containers using particles that stick to surfaces and record wet maps, exported via Alembic.
  - Tools: xpEmitter on a spray can, xpCollider tag, xpWetMap tag (vertex maps), Alembic export, Xpresso.
  - Today: nxCollider adhesion + nxFalloff Wet mode → nxFalloffMap vertex maps (C4D).
- **2022-09-16 — Drawing with Particles - 05 - Rendering & Compositing** — https://www.youtube.com/watch?v=fMTz2EcSS04
  - What: renders the wet-map vertex maps and particle colour in Cycles 4D materials (with translucency) and composites in After Effects.
  - Tools: Cycles 4D (vertex map, particle data nodes), After Effects.
  - Today: Redshift reading nxFalloffMap vertex maps / vertex colour.

## Premium Training — Logo Form
- **2022-09-16 — Logo Form - 01 - xpCover & xpInherit** — https://www.youtube.com/watch?v=hbleYqDBiiA
  - What: reveals a logo by covering its geometry with particles or inheriting positions, including how point order affects the result.
  - Tools: xpCover, xpInherit, xpTurbulence.
  - Today: nxCover; xpInherit has no listed nx equivalent — keep on CPU or approximate with nxCover / nxAttract.
- **2022-09-16 — Logo Form - 03 - Streams** — https://www.youtube.com/watch?v=YXz1wTcyQf0
  - What: helical streaming trails rushing in to form the logo alongside a reversed collapsing-nebula cache.
  - Tools: xpTrail, xpFlowField, xpFollowSpline / xpSplineFlow, xpCover (nearest surface point), xpCache (offset, hold).
  - Today: nxTrail + nxWarp Helix + nxCover.
- **2022-09-16 — Logo Form - 04 - Tweaks & Rendering** — https://www.youtube.com/watch?v=tPZLKDkndEA
  - What: tightens the nebula spiral, re-caches, restores colour inheritance, then lights and shades the particles (metallic glints) in Cycles 4D.
  - Tools: xpFlowField (To Spline strength), xpInherit, xpTrail, xpCache, Cycles 4D.
  - Today: nxFlowField / nxWarp Helix; Redshift shading.
- **2022-09-16 — Logo Form - 05 - Compositing** — https://www.youtube.com/watch?v=jfYXZe2VS9Y
  - What: After Effects comp with pixel motion blur, tint and opacity tweaks on the glimmer pass.
  - Tools: After Effects.
  - Today: still current.

## Premium Training — Fireworks
- **2022-09-16 — Fireworks - 01 - Anatomy of a Firework** — https://www.youtube.com/watch?v=ruePL0LBHDo
  - What: studies real firework types, then builds a controllable lift shell following a trajectory spline.
  - Tools: xpEmitter, xpFollowSpline, xpTurbulence, xpTrail.
  - Today: nxFollowGeo / nxWarp Path + nxTrail.
- **2022-09-16 — Fireworks - 02 - Lift, Break & Shape** — https://www.youtube.com/watch?v=pPSUS_qYfuk
  - What: the break — stars spawned from the shell with radius-based offsets, shaped and isolated in their own system, with trails.
  - Tools: xpSpawn, xpQuestion, xpTurbulence, xpTrail, system isolation options.
  - Today: nxSpawn (On Death / At Age) + nxTrail.
- **2022-09-16 — Fireworks - 03 - The Display** — https://www.youtube.com/watch?v=bmGuzKj4vk8
  - What: builds a launch platform and a timed show of many fireworks controlled by Xpresso user data (ignition, travel time).
  - Tools: Xpresso, xpSpawn, xpQuestion, xpFollowSpline, xpTrail.
  - Today: Xpresso still works; per-shot timing via nxSpawn / nxQuestion.
- **2022-09-16 — Fireworks - 04 - Lighting & Materials** — https://www.youtube.com/watch?v=ZcgFQWPagqo
  - What: camera move, silhouetted trees and emissive firework materials using a range-mapping node group.
  - Tools: Cycles 4D (math-node range mapping group).
  - Today: Redshift (built-in range remap).

## Premium Training — Sci-Fi FUI
- **2022-09-16 — Sci-Fi FUI - 01 - The Leak** — https://www.youtube.com/watch?v=vsIISOBfuGU
  - What: infected goo leaking in a petri dish — regular-grid emission, a fluid solve and a smooth OpenVDB collision/mesh setup.
  - Tools: xpEmitter (regular/hexagonal), xpFluidFX, xpFlowField, xpKill, xpOpenVDBMesher (adaptivity).
  - Today: nxFluids FLIP with high viscosity / non-Newtonian + nxMesher.
- **2022-09-16 — Sci-Fi FUI - 02 - FUI** — https://www.youtube.com/watch?v=si9mAqLRfPg
  - What: trims and exports the goo cache to Alembic for displacers, then builds HUD graphics that track particles via Xpresso.
  - Tools: xpCache, Alembic export, xpFlowField, Xpresso.
  - Today: nxCache Alembic output; Xpresso tracking unchanged.

## Premium Training — Infectio
- **2022-09-16 — Infectio - 03 - Spores** — https://www.youtube.com/watch?v=OLeYN-Am5TY
  - What: grows hairy spores only from infected mould particles using probability-based spawning and trails.
  - Tools: xpInfectio, xpSpawn (action-controlled), xpQuestion, xpTrail, xpFlowField, xpTurbulence.
  - Today: nxInfectio + nxSpawn / nxQuestion Spawn + nxTrail.
- **2022-09-16 — Infectio - 04 - Rendering** — https://www.youtube.com/watch?v=QzACkgaJHhs
  - What: cameras, multi-GPU Cycles 4D rendering, random particle colour and trail-hair materials with a range-mapping group.
  - Tools: Cycles 4D (hair/trail rendering, camera tag).
  - Today: Redshift (hair from nxTrail splines).

## Maintenance Training — Fluids
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Cloth Interaction** — https://www.youtube.com/watch?v=to0ddsJ8QTA
  - What: water tearing one cloth and pooling in another; only FluidFX or PBD couple with cloth, and the cloth must solve before the fluid.
  - Tools: xpClothFX, xpFluidFX / xpFluidPBD.
  - Today: no GPU cloth yet — CPU xpClothFX; unified GPU cloth/coupling announced for the next NeXus beta.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Controlling Flows** — https://www.youtube.com/watch?v=V0kXecaPKhk
  - What: stylised product shot — PBD for a clean stream vs FLIP for splashy detail along a spline path.
  - Tools: xpFluidPBD, xpFluidFLIP, xpSplineFlow, xpTurbulence, xpSheeter, xpFoam.
  - Today: nxFluids FLIP + nxFollowGeo / nxWarp Flow, nxFoam, nxSheeter.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Mid to Large Scale** — https://www.youtube.com/watch?v=SlAvrz-mI6U
  - What: compares all three CPU solvers on a splash tank and waterfall, including accuracy vs sim time.
  - Tools: xpFluidFX, xpFluidPBD, xpFluidFLIP, xpCollider.
  - Today: nxFluids FLIP/APIC.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Glass Fill** — https://www.youtube.com/watch?v=OkigcUDam4I
  - What: real-world-scale pour into a glass; fixes emission banding and gravity at small scale by raising subframes.
  - Tools: xpFluidFX, xpEmitter (hexagonal), X-Particles project subframes.
  - Today: nxFluids FLIP/APIC with Liquid Fill; substeps in NeXus Project Settings.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Macro Splashes** — https://www.youtube.com/watch?v=OEmGpUKXScQ
  - What: high-speed-photo crown splash and product splashes, comparing FluidFX and FLIP collision behaviour.
  - Tools: xpSplash, xpSheeter, xpFluidFX, xpFluidFLIP.
  - Today: nxSplash (crown) + nxFluids FLIP + nxSheeter.
- **2022-09-16 — Fluids - Series 2 - Intro to FluidPBD** — https://www.youtube.com/watch?v=w647Eqzx38g
  - What: PBD solver and fluid property settings — domain-free solve inside a glass.
  - Tools: xpFluidPBD, xpGravity, xpCollider.
  - Today: nxFluids PBD (strengths no longer scale with particle size since 2026.1 Beta 2).
- **2022-09-16 — Fluids - Series 2 - Intro to FluidFX: Solver Settings** — https://www.youtube.com/watch?v=jmMXWgtp4ys
  - What: FluidFX accuracy presets, density control, internal/external pressure and damping on a drop tank.
  - Tools: xpFluidFX, xpEmitter (hexagonal box).
  - Today: nxFluids SPH (or FLIP for large volumes).
- **2022-09-16 — Fluids - Series 2 - Intro to FluidFX: Emitter Settings** — https://www.youtube.com/watch?v=_-gpqcjuA5c
  - What: per-emitter fluid data — surface tension beads, viscous fluids and granular sims in a vibrating vessel.
  - Tools: xpEmitter Extended Data → Fluid, xpFluidFX.
  - Today: per-emitter nxFluids tag / Mixer; granular → nxMPM sand.
- **2022-09-16 — Fluids - Series 3 - Intro to Sheeter** — https://www.youtube.com/watch?v=l6k_stWo0_0
  - What: turns a coarse splash on a lemon into thin fluid sheets, tuning size, density, speed and age thresholds.
  - Tools: xpSheeter, xpFluidFX, xpCollider.
  - Today: nxSheeter (2026) / FLIP sheeting in nxFluids.
- **2022-09-16 — Fluids - Series 3 - Intro to Wave and Foam** — https://www.youtube.com/watch?v=dEsr4yqXHEM
  - What: rolling surf on a beach mesh with whitewater foam and spray particles.
  - Tools: xpWave, xpFoam, xpFluidFX, xpKill.
  - Today: nxOcean beach (swash/surf) or nxWave + nxFoam with FLIP.
- **2022-09-16 — Fluids - Series 4 - Teacup Splash Build** — https://www.youtube.com/watch?v=pMrAb9P7Wpk
  - What: crown splash in a teacup, limiting the fluid body to a shallow band for ripples.
  - Tools: xpSplash, xpSheeter, xpFluidFX, xpCollider.
  - Today: nxSplash + nxFluids FLIP.

## Maintenance Training — ExplosiaFX
- **2022-09-16 — ExplosiaFX - The Basics - Intro to the EFX Solver** — https://www.youtube.com/watch?v=bpTUYD_Hkf8
  - What: voxel solver basics — source tag, channels (fuel, heat, smoke), advection and adaptive bounds.
  - Tools: xpExplosiaFX, xpExplosiaFX Source tag.
  - Today: nxExplosiaFX (sources in its Sources tab).
- **2022-09-16 — ExplosiaFX - The Basics - Particle Advection** — https://www.youtube.com/watch?v=f7_u0G28cAw
  - What: particles carried by the smoke velocity, coloured by temperature and cleaned up by fuel via questions.
  - Tools: xpExplosiaFX, xpEmitter, xpQuestion/xpAction.
  - Today: nxExplosiaFX; verify particle advection in 2026.1, else keep CPU EFX.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Object Sources** — https://www.youtube.com/watch?v=vWqea_xAu-o
  - What: object sources masked by textures, selections and vertex maps, transferring velocity/colour, spline sources and contact-only emission.
  - Tools: xpExplosiaFX Source tag.
  - Today: nxExplosiaFX emitting from objects, splines, vertex maps and shaders.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Particle Sources** — https://www.youtube.com/watch?v=ocB802N_bKk
  - What: particles as smoke sources passing velocity, colour and pressure to make explosions.
  - Tools: xpExplosiaFX Source tag on xpEmitter.
  - Today: nxExplosiaFX particle sources.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Colliders** — https://www.youtube.com/watch?v=mJ919p6x2gE
  - What: colliders that redirect smoke, filling objects, velocity transfer from animated colliders and a high-pressure scenario.
  - Tools: xpExplosiaFX Collider tag.
  - Today: nxExplosiaFX collisions.
- **2022-09-16 — ExplosiaFX - Simulation Settings - Simulation Scale & Speed** — https://www.youtube.com/watch?v=NR9IfLLhX64
  - What: changes apparent sim size without touching voxels, and animates sim speed to slow a shockwave.
  - Tools: xpExplosiaFX (Sim Scale, Sim Speed).
  - Today: nxExplosiaFX (check its scale/speed settings).
- **2022-09-16 — xpExplosiaFX - Candle & Whispy Smoke** — https://www.youtube.com/watch?v=V8Y7nH2b5Zc
  - What: candle flame and wispy smoke from a wick on a moving holder, with a burning effect and a looping extinguish.
  - Tools: xpExplosiaFX + Source tag, xpVertexMap, xpTrail.
  - Today: nxExplosiaFX + nxWarp on smoke; C4D 2025.3+ Pyro link.
- **2022-09-16 — ExplosiaFX - Simulation Tutorials - Explosions** — https://www.youtube.com/watch?v=R35x1j1AIa8
  - What: high-pressure fast particle sources for a timed blast against a wall, scene-wide colliders and a tearing cloth sign.
  - Tools: xpExplosiaFX, xpEmitter, xpTrail, xpCollider, xpClothFX (tearing).
  - Today: nxExplosiaFX (+ nxShatter for debris); cloth still CPU xpClothFX.
- **2022-09-16 — ExplosiaFX - Rendering Colorful Explosions** — https://www.youtube.com/watch?v=Mj23NfHIDhY
  - What: reads the EFX colour channel into a Cycles 4D volume material via point density, tweaks it with HSV and builds a mask.
  - Tools: xpExplosiaFX (Color channel), Cycles 4D Point Density node.
  - Today: nxExplosiaFX VDB in Redshift (default smoke material) using the colour grid.

## Other (no technique)
- INSYDIUM Fused - Release Update OUT NOW! - Sept '22 — https://www.youtube.com/watch?v=D3_Cr2oWWW8
- Premium Training - Ivy Growth - Introduction — https://www.youtube.com/watch?v=n9Nrp8qRCns
- Premium Training - Logo Form - Introduction — https://www.youtube.com/watch?v=lgQrcXsk9y0
- Premium Training - Drawing with Particles - Introduction — https://www.youtube.com/watch?v=awBukPjcgkE
