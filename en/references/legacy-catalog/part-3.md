# Legacy video catalog — part 3 (2019-03-27 – 2020-06-18)

## Maintenance Training — XP Countdown, Series 3 (rendering & compositing)
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Compositing In After Effects** — https://www.youtube.com/watch?v=bzDVMDJVm4g
  - What: imports the five rendered countdown image sequences (plus beauty and emission passes) into After Effects and re-times, freeze-frames and joins them into one countdown edit.
  - Tools: After Effects (Import Multiple Files, image sequences, duplicate layers / freeze frames); renders from the X-Particles countdown scenes.
  - Today: still current (compositing workflow, independent of the particle tools).
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Six Fill Render** — https://www.youtube.com/watch?v=PjaJxtJ735k
  - What: lights and renders the "6" fill scene — a cached OpenVDB-meshed liquid inside a Boolean with the MoText plus cached foam particles — reusing lights, cameras and materials from earlier render builds and shrinking the bubble radius at render time.
  - Tools: xpOpenVDBMesher, xpFoam (cached), xpCache, Cycles 4D materials, C4D Boole + MoText.
  - Today: nxMesher + nxFoam (Fused 2025.4 GPU) rendered in the host renderer (e.g. Redshift).
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Four Shatter Render** — https://www.youtube.com/watch?v=GVRrMENF-p4
  - What: adds extra crack animation to the crumbling "4" so the shot isn't static, re-caches, then shades the shards with a mix shader driven by xpShatter's selection output and renders EXR passes.
  - Tools: xpShatter (Selection tab), xpExplosiaFX dust, xpCache, Cycles 4D mix shader, OpenEXR output.
  - Today: nxShatter (NeXus 2026.1) + nxExplosiaFX; stable C4D: xpShatter still current.
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Point Density Render** — https://www.youtube.com/watch?v=DLWa30MwOZw
  - What: renders xpExplosiaFX smoke only where it passes through the "1" geometry, using a point-density texture that reads the EFX smoke channel in world space, then remaps density through a colour ramp into a principled volume.
  - Tools: xpExplosiaFX, Cycles 4D Point Density texture, Principled Volume, colour ramp.
  - Today: nxExplosiaFX VDB output rendered in the host renderer; the volume-masking trick itself has no direct NeXus equivalent.

## Sneak Peeks
- **2020-06-17 — xpScatter - Sneak Peek** — https://www.youtube.com/watch?v=nG79HnArIss
  - What: previews the xpScatter generator — scattering objects by polygons, vertices, area, textures or illumination, with height/slope/curvature topology rules, kill/push spacing and variation, on animated surfaces, xpOcean, splines and trails.
  - Tools: xpScatter, xpOcean, MoGraph effectors, X-Particles modifiers.
  - Today: nxScatter (NeXus 2026.1 Beta 3, points on meshes → nxGenerator); xpScatter still current in Fused.
- **2020-06-15 — Intersections - Sneak Peek** — https://www.youtube.com/watch?v=Cr9uzVLjjLg
  - What: previews the new Intersections tab that detects trail crossings and makes particles change direction, trigger a spawn or freeze, giving non-intersecting grid networks and organic branches.
  - Tools: xpNetwork, xpBranch (Intersection tab), xpTrail, xpSpawn via trigger action.
  - Today: nxDendrite (branches/network/lattice) is the NeXus route; xpNetwork/xpBranch intersections still current on CPU.

## Maintenance Training — Constraints
- **2020-06-11 — Maintenance Training - Dynamics - Constraints - Simple Cloth Tutorial** — https://www.youtube.com/watch?v=whjVGe3DuQo
  - What: emits one particle per vertex of a plane, links them with polygon-edge and diagonal birth connections for a fast cloth that drapes over a sphere, then deforms a low-poly plane with the particles and smooths it with a Subdivision Surface.
  - Tools: xpConstraints (Connections — polygon edges / diagonals), xpGravity, xpCollider tag, xpDeformer, C4D Subdivision Surface.
  - Today: nxConstraints + nxPin with nxDeformer (NeXus 2026.1); stable C4D: xpClothFX or the same CPU setup.

## XP Countdown tutorials
- **2020-06-11 — Break scene objects, animate shattered pieces & create dust effects using X-Part…** — https://www.youtube.com/watch?v=EoDeHKiCB7k
  - What: shatters the "4" so it crumbles away to reveal a "3", pushing shards along the 3's spline with an explode and collider, and adds xpExplosiaFX dust.
  - Tools: xpShatter, xpDynamics, xpExplode, xpCollider tag, xpExplosiaFX, xpCache, MoText.
  - Today: nxShatter + nxExplosiaFX (NeXus 2026.1), or nxBind → nxMPM brittle for crumbling; stable C4D: xpShatter + CPU dynamics.

## INSYDIUM Training
- **2020-06-09 — INSYDIUM Training - Dynamic Water - xpOcean & xpFluidFX** — https://www.youtube.com/watch?v=pl1aX6iT3so
  - What: builds a boxed xpFluidFX water body with foam colliding with an object, then layers xpOcean wave deformation (wave height, choppiness, detail) on top.
  - Tools: xpFluidFX, xpFoam, xpCollider tag (normals inside), xpOcean, box emitter.
  - Today: nxOcean with FLIP coupling (NeXus 2026.1); stable C4D: nxFluids FLIP + nxWave + nxFoam.

## XP Countdown tutorials
- **2020-06-04 — Create a smoke and fire simulation, add organic cloth motion and build a cloth d…** — https://www.youtube.com/watch?v=C-7JxBDJ-S0
  - What: burns away the shrink-wrapped plastic bag around the "5" with xpExplosiaFX fire while an infection spreads through the cloth particles, timing the melt/tear per particle from when it is infected.
  - Tools: xpExplosiaFX, xpInfectio (incubation groups), xpClothFX (tearing), Data Mapping to time in modifier, xpCache.
  - Today: nxExplosiaFX + nxInfectio, cloth via nxConstraints/nxPin with nxDeformer tearing (NeXus 2026.1); stable C4D: xpClothFX.

## INSYDIUM Training
- **2020-05-30 — INSYDIUM Training - xpCache Retiming 02** — https://www.youtube.com/watch?v=OamxZDVUiVY
  - What: Water Spin part 5 — uses the Xpresso/user-data rig to draw smooth speed-ramp curves and copies the retime track so all caches retime identically.
  - Tools: xpCache (retime), Xpresso, user data, animation tracks.
  - Today: still current for xpCache; no documented nxCache retime rig.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-05-28 — Maintenance Training - Dynamics - FlowField - Planetary Weather Tutorial** — https://www.youtube.com/watch?v=uDq_2RqjjBg
  - What: creates stylised swirling weather on a planet with an xpFlowField in surface mode, steered by a rig of rotated cloner polygons, then tests it on other geometry.
  - Tools: xpFlowField (Surface flow), Emit from Object quick tool, MoGraph Cloner, xpFollowSurface.
  - Today: nxFlowField (NeXus 2026.1) or nxFollowGeo surface mode (Fused 2025.4).
- **2020-05-28 — Maintenance Training - Constraints - Chain Reaction Tutorial** — https://www.youtube.com/watch?v=9x4cG4Ihej0
  - What: particles linked by birth connections grow in scale based on their movement, so a collider pushing into them sets off an organic chain-reaction growth.
  - Tools: xpConstraints (connect at birth), xpScale mapped to speed, xpCollider tag, shot emission from a plane.
  - Today: nxConstraints + nxScale with Mapping by Speed (Fused 2025.4 GPU).

## INSYDIUM Training
- **2020-05-22 — INSYDIUM Training - xpCache Retiming 01** — https://www.youtube.com/watch?v=wrbSZcv-yf4
  - What: Water Spin part 4 — gathers the three cached systems into a clean scene and builds a user-data/Xpresso rig to retime them together for fast/slow-motion speed ramps.
  - Tools: xpCache (retime), Xpresso, user data.
  - Today: still current for xpCache; no documented nxCache retime rig.

## XP Countdown tutorials
- **2020-05-21 — Use X-Particles in C4D to simulate viscous liquid object fill (Density Sep) ｜ xp…** — https://www.youtube.com/watch?v=qQCLXXnSoxo
  - What: fills the "5" with gloopy liquids of different densities that separate and mix, staggering emitter start frames with formula input, and meshes one of the liquids.
  - Tools: xpFluidFX (density, viscosity), multiple emitters, xpOpenVDBMesher, MoText collider.
  - Today: nxFluids FLIP with Mixer (per-emitter density/viscosity) + nxMesher (NeXus 2026.1).

## INSYDIUM Training
- **2020-05-18 — INSYDIUM Training - xpFluidFX Hero Splash** — https://www.youtube.com/watch?v=qRJDmKFO-oY
  - What: Water Spin part 3 — builds an art-directed hero splash that wraps around the base spheres, using new emitters, collider exclusions per group and a cache to be retimed later.
  - Tools: xpFluidFX, xpFoam, xpCollider tag (collision exclusions), xpCache.
  - Today: nxFluids FLIP/APIC + nxSplash + nxMesher (Fused 2025.4).
- **2020-05-15 — INSYDIUM Training - xpFluidFX Splash** — https://www.youtube.com/watch?v=GrGnRSPQYT0
  - What: Water Spin part 2 — a swirling water splash with foam around cached spheres, meshed with the OpenVDB mesher (point radius vs voxel size explained).
  - Tools: xpFluidFX, xpFoam, xpGravity (Newton), xpOpenVDBMesher, xpCache.
  - Today: nxFluids FLIP/APIC + nxFoam + nxMesher (Fused 2025.4).

## Maintenance Training — FlowField
- **2020-05-14 — Maintenance Training - Dynamics - FlowField - Bar Magnets Tutorial** — https://www.youtube.com/watch?v=J9PHTpT_Jzk
  - What: models a bar magnet's field lines with splines and cloners, feeds them into an xpFlowField, exports/imports the field to duplicate it and recreates the iron-filings experiment.
  - Tools: xpFlowField (spline flow, export/import), MoGraph Cloner, splines.
  - Today: nxFlowField (NeXus 2026.1); for stream shaping, nxWarp / nxFollowGeo.

## INSYDIUM Training
- **2020-05-12 — INSYDIUM Training - xpFlowField Spline Control** — https://www.youtube.com/watch?v=YbKzbvh29QA
  - What: Water Spin part 1 — sets up the project/cache folders and steers dynamic spheres with an xpFlowField in spline mode, using data mapping on the particles.
  - Tools: xpFlowField (spline mode), xpEmitter, Data Mapping, xpCache.
  - Today: nxFollowGeo spline mode or nxWarp Path (NeXus 2026.1); nxFlowField for field-based control.
- **2020-05-11 — INSYDIUM Training - xpVertexMap** — https://www.youtube.com/watch?v=jttdFsnXmg0
  - What: tours the rewritten xpVertexMap — one object driving live vertex maps on several (even parametric) objects, with layer modes (polygons, textures, seed), per-layer smoothing, brightness and contrast.
  - Tools: xpVertexMap.
  - Today: nxFalloff modes + nxFalloffMap to bake falloffs into vertex maps (C4D, NeXus 2026.1); xpVertexMap still current.

## Maintenance Training — Constraints
- **2020-05-07 — Maintenance Training - Constraints - Fluids Explained** — https://www.youtube.com/watch?v=1j9GJBzut94
  - What: explains the constraint-based surface tension, viscosity and friction settings for droplets, stiff gloopy liquids and wet sand.
  - Tools: xpConstraints (Surface Tension, Viscosity, Friction), hexagonal shot emitter, xpCollider tag.
  - Today: nxFluids PBD/SPH (surface tension, viscosity) or nxConstraints; for wet sand nxMPM Sand.

## INSYDIUM Training
- **2020-05-06 — INSYDIUM Training - Trail Display** — https://www.youtube.com/watch?v=EOSe3xbJRQg
  - What: shows the new Trails display mode in xpFlowField and xpExplosiaFX and how to render it with xpDisplayRender in Cycles 4D, Standard and Physical.
  - Tools: xpFlowField, xpExplosiaFX (Trails display), xpDisplayRender, Cycles 4D emission material.
  - Today: still current on CPU (Fused); no direct NeXus equivalent.
- **2020-05-04 — INSYDIUM Training - xpOcean** — https://www.youtube.com/watch?v=KFI08viXs2w
  - What: walks through xpOcean (Tessendorf waves) as primitive or deformer — size, segments, wave height, time scale, noise types, resolution — and tiles several planes seamlessly with xpJoin.
  - Tools: xpOcean, xpJoin.
  - Today: nxOcean (NeXus 2026.1); stable C4D: xpOcean still current.

## XP Countdown tutorials
- **2020-04-30 — Create an exploding splash simulation using X-Particles in Cinema 4D： Integrate…** — https://www.youtube.com/watch?v=SOHvUX6L-QM
  - What: makes a custom splash out of the "6" with xpFluidFX and keyframed xpSheeter, then meshes it, reusing the cached plastic bag and setting the cache tag to hold.
  - Tools: xpFluidFX, xpSheeter, xpOpenVDBMesher, xpCache (cache tag, copy tag data).
  - Today: nxFluids FLIP + nxSplash + nxMesher (Fused 2025.4); nxSheeter for thin sheets (NeXus 2026).

## INSYDIUM Training
- **2020-04-29 — INSYDIUM Training - xpFlock** — https://www.youtube.com/watch?v=q14LkWwesLA
  - What: builds a school of fish with xpFlock — tangential rotation with +Y up vector, behaviours (separation, chaos…), then reactions and avoidance.
  - Tools: xpFlock (Behaviors, Reactions, Avoidance), xpEmitter (Extended rotation).
  - Today: nxFlock with nxFlock Reactor children (Fused 2025.4 GPU).

## Sneak Peeks (Beta Access)
- **2020-04-28 — INSYDIUM Beta Access - Sneak peek - xpPushApart** — https://www.youtube.com/watch?v=IexdLfCMElo
  - What: previews xpPushApart separating overlapping particles by distance or radius, also combined with a growing scale modifier.
  - Tools: xpPushApart, xpScale.
  - Today: nxPush (GPU, much faster).
- **2020-04-27 — INSYDIUM Beta Access - Sneak Peek - xpOcean** — https://www.youtube.com/watch?v=9pQOO6faWTw
  - What: previews xpOcean — loopable waves, choppiness, depth, wind direction, foam vertex map and deformer modes (local/world/surface).
  - Tools: xpOcean.
  - Today: nxOcean (NeXus 2026.1, foam/spray built in).
- **2020-04-26 — INSYDIUM Beta Access - Sneak Peek - Trail Display** — https://www.youtube.com/watch?v=vExeD3XMzc0
  - What: previews the renderable Trails, plane and voxel display modes for xpFlowField, including driving a flow field from an xpExplosiaFX sim.
  - Tools: xpFlowField (Trail display), xpExplosiaFX, xpDisplayRender.
  - Today: still current on CPU; no direct NeXus equivalent.
- **2020-04-25 — INSYDIUM Beta Access - Sneak Peek - xpEmitter** — https://www.youtube.com/watch?v=FuqDknGFUtM
  - What: previews the emitter's simulate mode that shows emission changes (topology slope, texture, vertex-map threshold) live on frame 0, plus a unified modifiers/questions list.
  - Tools: xpEmitter (Simulate mode, topology, texture emission, vertex map threshold).
  - Today: nxEmitter (NeXus 2026) for GPU; xpEmitter still current.
- **2020-04-24 — INSYDIUM Beta Access - Sneak Peek - xpVertexMap** — https://www.youtube.com/watch?v=z8rPNIcd1HY
  - What: previews the layered xpVertexMap — animated maps on primitives/generators, blend modes, AO and curvature modes, seed spread, driving emission and dynamics.
  - Tools: xpVertexMap, xpDynamics.
  - Today: nxFalloff (Curvature, AO, Wet) + nxFalloffMap (NeXus 2026.1); xpVertexMap still current.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-04-23 — Maintenance Training - Dynamics - FlowField - Cell Size Explained** — https://www.youtube.com/watch?v=XBDGF8VDcvk
  - What: explains cell size as the flow field's resolution, comparing detail side by side and its importance for spline inputs.
  - Tools: xpFlowField (Random flow, Velocity field mode, Cell Size).
  - Today: same concept in nxFlowField (NeXus 2026.1); xpFlowField still current.
- **2020-04-23 — Maintenance Training - Dynamics - Constraints - Forces Explained** — https://www.youtube.com/watch?v=8Y5a8_dRgK0
  - What: covers the constraints Forces collision type — attraction and repulsion, combining with connections and mapping strength by radius.
  - Tools: xpConstraints (Forces), defined-grid emitter.
  - Today: nxConstraints (same layers) / nxAttract on GPU.

## Sneak Peeks (Beta Access)
- **2020-04-23 — INSYDIUM Beta Access - Sneak Peek - xpBlend** — https://www.youtube.com/watch?v=T5XnNOHEiho
  - What: previews xpBlend averaging colour, radius or physical values such as fuel between nearby particles, e.g. mixed-paint fluid.
  - Tools: xpBlend, xpFluidFX.
  - Today: nxBlend (GPU).
- **2020-04-22 — INSYDIUM Beta Access - Sneak Peek - xpBranch** — https://www.youtube.com/watch?v=ZizmR8dAqDo
  - What: previews the updated xpBranch — curl bending, sub-branches with their own groups, spline-controlled distribution, symmetry — for foliage growth rigs.
  - Tools: xpBranch, xpTrail.
  - Today: nxDendrite (NeXus 2026) / nxBioLogic; stable C4D: xpBranch.
- **2020-04-21 — INSYDIUM Beta Access - Sneak Peek - xpFlock** — https://www.youtube.com/watch?v=r38YJ5plcAg
  - What: previews xpFlock layered behaviours and reactions, with a blue flock fleeing red "shark" particles.
  - Tools: xpFlock.
  - Today: nxFlock + nxFlock Reactor.

## VERTEX talks
- **2020-04-20 — Bringing Visual Effects to Motion Graphics - VERTEX 2020 Presentation** — https://www.youtube.com/watch?v=QrtjqCTVh7E
  - What: breaks down a neon-city shot live — fluid splash, rippling MoGraph cube floor, spline dynamics, explosion advection and organic growth of lights — rendered in Cycles 4D.
  - Tools: xpFluidFX, xpOpenVDBMesher, xpExplosiaFX, xpDynamics (splines), MoGraph, Cycles 4D.
  - Today: nxFluids FLIP + nxMesher + nxExplosiaFX (Fused 2025.4); growth via nxInfectio / nxBioLogic.

## XP Countdown tutorials
- **2020-04-16 — X-Particles shrink-wrap cloth animation, art direct motion & retime the simulati…** — https://www.youtube.com/watch?v=id7ad16ig6k
  - What: turns a cube into an xpClothFX plastic bag that shrink-wraps around the "5", art-directed with flow fields, and retimed in the emitter and xpCache.
  - Tools: xpClothFX, xpFlowField, xpCollider tag, xpCache (retime), MoText.
  - Today: nxConstraints cloth + nxPin / nxDeformer (NeXus 2026.1); stable C4D: xpClothFX.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-04-16 — Maintenance Training - Dynamics - FlowField - Field Modes Explained** — https://www.youtube.com/watch?v=54h5SnIjsnc
  - What: explains direction vs velocity vs acceleration field modes using a helix spline flow and the XP console to read particle speed.
  - Tools: xpFlowField (Along Spline flow; Direction/Velocity/Acceleration), XP Console.
  - Today: same modes in nxFlowField (NeXus 2026.1); xpFlowField still current.
- **2020-04-09 — Maintenance Training - Constraints - Connections Explained** — https://www.youtube.com/watch?v=QqFEH8CkB44
  - What: explains spring connections — birth-connection radius and limits, soft bodies, distance constraints and custom springs.
  - Tools: xpConstraints (Connections, birth/distance), defined emission, Display Constraints.
  - Today: nxConstraints (same layers); soft bodies via nxMPM Elastic (NeXus 2026.1).

## XP Countdown tutorials
- **2020-04-02 — How to fill objects with water, generate bubbles and mesh fluid sims using X-Par…** — https://www.youtube.com/watch?v=QNsJZhnTzPI
  - What: first countdown scene — sets the folder/naming structure, fills the "6" with xpFluidFX water using a proxy kill object, adds xpFoam bubbles and meshes with OpenVDB plus a Boole.
  - Tools: xpFluidFX, xpFoam, xpKill, xpOpenVDBMesher, xpCollider tag, C4D Boole, MoText.
  - Today: nxFluids FLIP (Liquid Fill) + nxFoam + nxMesher.

## Maintenance Training — FlowField
- **2020-03-26 — Maintenance Training - Dynamics - FlowField - Flow Modes Explained** — https://www.youtube.com/watch?v=44pjAgy2nB4
  - What: explains cells and vectors, then each flow mode — default, random, target, shader, spline and surface — and falloff behaviour.
  - Tools: xpFlowField (flow modes, falloff).
  - Today: nxFlowField (NeXus 2026.1); xpFlowField still current.

## Sneak Peeks — VERTEX 2020
- **2020-02-28 — VERTEX 2020 - Sneak Peek - xpExplosiaFX** — https://www.youtube.com/watch?v=lhE0y-N9Mq8
  - What: shows the renderable Trails display of EFX velocity and the new Upres for turning a low-res look-dev sim into high detail with the same motion.
  - Tools: xpExplosiaFX (Trails display, Upres).
  - Today: nxExplosiaFX + nxUpres (GPU).
- **2020-02-28 — VERTEX 2020 - Sneak Peek - xpFlock** — https://www.youtube.com/watch?v=1ffSoa_1auo
  - What: brief demo of fish flocking with layered behaviours and fleeing from shark particles.
  - Tools: xpFlock.
  - Today: nxFlock + nxFlock Reactor.

## Content Repository Tutorials 2019
- **2019-09-27 — Dynamic Web - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=CFEZtK0DmUg
  - What: builds stretchy, sticky spider webs between cloned cubes with constraints and renders the trails in Cycles 4D (trails aren't dynamic themselves, so some intersection).
  - Tools: xpConstraints, xpTrail, MoGraph Cloner, Cycles 4D.
  - Today: nxConstraints + nxTrail (GPU).
- **2019-07-26 — UV Emission Data - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=hycQlFrHFRU
  - What: emits from a textured plane by polygon area and maps an animated texture onto the particles via UV emission data, then advects them and keyframes a slowdown.
  - Tools: xpEmitter (UV emission data), xpExplosiaFX advection, Cycles 4D.
  - Today: CPU route still current; NeXus: nxEmitter + nxExplosiaFX advection, no direct UV-data equivalent documented.

## X-Particles Public Release 2019
- **2019-07-01 — New Features - X-Particles Public Release 2019** — https://www.youtube.com/watch?v=HbVKC-ldyUM
  - What: tours the smaller 2019 features — xpSplineGrowth animating trail length/variation (also on text splines) and the xpDisplayRender generator rendered with C4D materials via the MoGraph Color shader.
  - Tools: xpSplineGrowth, xpTrail, xpDisplayRender.
  - Today: still current on CPU; GPU trails via nxTrail.
- **2019-06-25 — xpShatter & xpDynamics - X-Particles Public Release 2019** — https://www.youtube.com/watch?v=oY_VKN7D7Yc
  - What: shows xpShatter with time- and collision-triggered recursive Voronoi layers and cut points from objects or particles, plus particle-based dynamics for soft bodies, dynamic splines and grains.
  - Tools: xpShatter, xpDynamics, xpExplosiaFX.
  - Today: nxShatter + nxMPM (NeXus 2026.1); stable C4D: xpShatter + xpDynamics.
- **2019-06-19 — xpSplash & xpSheeter – X-Particles Public Release 2019** — https://www.youtube.com/watch?v=alvv1XIZGMQ
  - What: introduces xpSplash (cone velocity splash) and xpSheeter (fills gaps with thin sheets, hole size controls) on an xpFluidFX sim.
  - Tools: xpSplash, xpSheeter, xpFluidFX.
  - Today: nxSplash (Fused 2025.4) + nxSheeter (NeXus 2026) on nxFluids FLIP.

## Content Repository Tutorials 2019
- **2019-06-01 — FluidFX Snow - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=15SS_bITbyg
  - What: a hexagonal snowball rolls down a slope as an xpFluidFX grain sim, meshed with OpenVDB filters and rendered in Cycles 4D with subsurface scattering.
  - Tools: xpFluidFX (granular), xpOpenVDBMesher (filters), Cycles 4D SSS.
  - Today: nxMPM / nxMaterial Snow preset (NeXus 2026.1); stable C4D: nxFluids SPH Granular.

## VERTEX talks
- **2019-05-22 — VERTEX 2019 - Beyond Expectations by Bob Walmsley** — https://www.youtube.com/watch?v=F3ZXGxqugpk
  - What: showreel plus live basics — system, emitter, gravity and collider, then a dynamics-tagged cube with initial movement and rotation.
  - Tools: xpSystem, xpEmitter, xpGravity, xpCollider tag, xpDynamics.
  - Today: rigid bodies: C4D Rigid Body tags on xpGenerator or nxMPM; unified GPU rigid bodies announced but not shipped (Nov 2026).

## Content Repository Tutorials 2019
- **2019-05-01 — Sand Advection - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=AANHiU-UfDU
  - What: fills the X-Particles logo with hexagonal granular sand and blows it apart with an xpExplosiaFX explosion via advection.
  - Tools: xpFluidFX (granular), xpExplosiaFX (advection), hexagonal emission.
  - Today: nxMPM Sand + nxExplosiaFX (NeXus 2026.1); stable C4D: nxFluids SPH Granular.

## Cycles 4D
- **2019-04-04 — Cycles 4D Build 321 Public Release is out now!** — https://www.youtube.com/watch?v=hqfi4ZNJ8Y4
  - What: walks through the Cycles 4D release — real-time preview, rebuilt node editor, Cryptomatte, random-walk SSS, vector/micro-poly displacement and HDR browser.
  - Tools: Cycles 4D (displacement node, image textures, HDR browser).
  - Today: no direct equivalent (renderer, outside NeXus scope).

## Content Repository Tutorials 2019
- **2019-04-01 — Under Water Splash - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=dJNH4LBxF34
  - What: an extruded "X" plunges into water and the bubbles disperse then rise — faked with particles advected by a low-res xpExplosiaFX sim rather than a fluid solver.
  - Tools: xpExplosiaFX (advection, voxel size), xpEmitter, extruded text.
  - Today: nxExplosiaFX advection, or nxFluids FLIP + nxFoam bubbles.

## X-Particles Early Access 2019
- **2019-03-27 — X-Particles Early Access Update - xpShatter** — https://www.youtube.com/watch?v=bIvR0R2_Xw8
  - What: introduces xpShatter — shards from a point generator (count, seed, manual points), display/colour/explode/offset options, animating shards with modifiers, then real particle dynamics.
  - Tools: xpShatter, xpSpin, xpDynamics.
  - Today: nxShatter (NeXus 2026.1; Voronoi/Glass/Wood/Bricks); stable C4D: xpShatter.

## Other (no technique)
- 2020-04-17 — VERTEX 2020 - INSYDIUM Vox Pop with Bob Walmsley — https://www.youtube.com/watch?v=Oc9ABSORpa0
- 2019-07-11 — User Accounts – Maintenance Benefits — https://www.youtube.com/watch?v=2h3OpwWUrmI
- 2019-05-20 — VERTEX 2019 - INSYDIUM Vox Pop with Bob Walmsley — https://www.youtube.com/watch?v=YxpLw_m6F7U
