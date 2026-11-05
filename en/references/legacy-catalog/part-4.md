# Legacy video catalog — part 4 (2017-07-21 – 2019-03-22)

## X-Particles Early Access Updates (2019)
- **2019-03-22 — X-Particles Early Access Update - xpDynamics** — https://www.youtube.com/watch?v=in5Mig-Rvnc
  - What: the xpDynamics tag puts a particle on every vertex of an object so gravity, colliders, turbulence or any other XP modifier move it as a rigid body; also works on xpGenerator/xpSprite output, and the driving particles can emit xpExplosiaFX fuel.
  - Tools: xpDynamics tag, xpGenerator, xpSprite, xpTurbulence, xpCollider tag, xpExplosiaFX Source tag, Data Mapping.
  - Today: no GPU rigid bodies yet (announced for the next NeXus beta) — use C4D Rigid Body tags on xpGenerator/nxGenerator geometry or nxMPM (elastic/brittle); xpDynamics still works on CPU in Fused 2025.4.
- **2019-03-15 — X-Particles Early Access Update - Quick Tools** — https://www.youtube.com/watch?v=G93LDHb9YZw
  - What: tour of the Quick Tools panel — 25 one-click scene/simulation presets (particles, fluids & grains, smoke/fire/advection, trails) plus helpers such as emit from object/selection/texture/vertex map, interactive fluid body and caching.
  - Tools: X-Particles Quick Tools, xpEmitter, xpFluidFX, xpExplosiaFX, xpTrail, xpCache.
  - Today: CPU-only helpers; on GPU the NeXus 2026.1 Add menu Presets section, nxSystem folders and nxMaterial one-click setups cover the same ground.

## Content Repository Tutorials 2019
- **2019-03-01 — Surface Advection** — https://www.youtube.com/watch?v=amjgSU-1uE8
  - What: particles held on a surface have their rotation (not position) advected by a coarse xpExplosiaFX shockwave, then xpGenerator clones geometry onto them for a flowing, fluid-like surface pattern.
  - Tools: xpExplosiaFX (advection, large voxel size), xpEmitter, xpGenerator.
  - Today: nxExplosiaFX or nxFlowField velocities driving nxRotate/nxSpin on surface-locked particles (nxSticky) → nxGenerator.

## Cycles 4D Updates
- **2019-02-06 — Cycles 4D - Early Access Update - Build 294** — https://www.youtube.com/watch?v=vzN9wOSnFsk
  - What: Cycles 4D release notes — rewritten real-time preview (with DOF), Cryptomatte, rebuilt node editor, micropolygon displacement driven by a noise height map.
  - Tools: Cycles 4D.
  - Today: Cycles 4D is no longer developed — use Redshift (Cryptomatte, displacement) in C4D, or Blender Cycles with NeXus.

## X-Particles 3.5 Tutorials
- **2019-02-05 — X-Particles 3.5 Tutorial - Data Mapping - Melt Rig** — https://www.youtube.com/watch?v=yG8i10D3Crk
  - What: a volume-filled cube of two particle groups melts as particles heat up — Data Mapping on temperature lowers variable viscosity and raises gravity strength.
  - Tools: xpEmitter (Volume, two xpGroups), xpFluidFX variable viscosity, Data Mapping (temperature), xpGravity, xpCollider tag.
  - Today: nxMPM with material change by age/speed (Mixer) or nxFluids FLIP Mixer viscosity; Data Mapping → NeXus Mapping tab.
- **2019-02-05 — X Particles 3 5 Tutorial - xpWind Twister** — https://www.youtube.com/watch?v=w73CsjSgYQA
  - What: re-upload of the 2017 tornado tutorial — xpWind "fans" arranged in a MoGraph Cloner push particles up in a spiral; variants with xpSkinner liquid, lava/snow and an xpGenerator fish school.
  - Tools: xpWind, MoGraph Cloner, xpSkinner, xpGenerator.
  - Today: nxWarp Helix/Twist (Flow mode) + nxTurbulence, or nxWind layers; nxMesher for the liquid look, nxGenerator for fish.
- **2019-02-05 — X-Particles 3.5 Tutorial - Spiral Growth** — https://www.youtube.com/watch?v=uu-iIprExFk
  - What: an Xpresso-driven spinning plane rig carries surface-attached particles so xpTrail draws twisting spiral trails (Gyuki88-style), with an extra inner trail.
  - Tools: Xpresso rig, xpEmitter, xpTrail, Connect object.
  - Today: nxWarp Helix or Path in Flow mode with nxTrail — no rig needed.
- **2019-02-05 — X-Particles 3.5 Tutorial - GeoBoil** — https://www.youtube.com/watch?v=uj-EpRy1qM4
  - What: rebuild of Simon Fiedler's Houdini GeoBoil — static particles born on a surface scale up and die, meshed by xpSkinner into boiling bubbles, packaged as a reusable Xpresso rig.
  - Tools: xpEmitter (Speed 0, short lifespan), xpScale, xpSkinner, Xpresso.
  - Today: nxEmitter + nxScale mapped by Age → nxMesher.
- **2019-02-05 — X-Particles 3.5 Tutorials - xpSound** — https://www.youtube.com/watch?v=oPu_1BE6n_0
  - What: xpSound reads an audio file's frequency bands and maps them (Map Sound tab) to emission, color and speed of particles from a cylinder ring emitter.
  - Tools: xpSound, xpEmitter (Cylinder shape).
  - Today: no direct equivalent — xpSound stays CPU-only.
- **2019-02-05 — X-Particle 3.5 Tutorial - Crystal Geodes** — https://www.youtube.com/watch?v=lK1rT3huWLI
  - What: an animated noise texture drives emission on a dense sphere, xpGenerator grows crystal cylinders along normals, and an xpWetMap vertex map pushes the base mesh outward.
  - Tools: xpEmitter (texture emission), xpGenerator, xpWetMap tag, vertex map, Displacer.
  - Today: nxEmitter + nxGenerator; nxFalloff Wet mode / nxFalloffMap (C4D 2026.1) for the vertex map.
- **2019-02-05 — X-Particles 3.5 Tutorial - Particle Driven Effects - Colour Scale** — https://www.youtube.com/watch?v=aD6xl-HMKJw
  - What: follow-up to Noisy Extruder — particles from a second emitter act as an X-Particles Falloff to ripple scale and color across extruded tiles in concentric rings.
  - Tools: xpEmitter, xpGenerator, xpScale, xpColor, X-Particles Falloff, Displacer.
  - Today: nxFalloff Points mode with layered nxScale/nxColor; nxFalloff Modifier Decay/Grow for trailing rings.
- **2019-02-05 — X-Particles 3.5 Tutorial - Noisy Extruder** — https://www.youtube.com/watch?v=YGivDm0iKv0
  - What: one particle per polygon centre with tangential rotation, hex cylinders generated on them, and a noise falloff controlling their scale.
  - Tools: xpEmitter (Shot, one per element), xpGenerator, xpScale, noise falloff.
  - Today: nxEmitter + nxScale layer with nxFalloff Noise → nxGenerator (or plain MoGraph Cloner + Fields).
- **2019-02-05 — X-Particles 3.5 Tutorial - Flynit** — https://www.youtube.com/watch?v=Sypzoyqk25A
  - What: Flyknit-style weave — an animated gradient (re-UV'd across the whole honeycomb mesh) drives emission, and xpConstraints with connected birth knit strands that split and build the mesh.
  - Tools: MoGraph Cloner (Honeycomb), xpEmitter (texture), xpConstraints, Display Constraints.
  - Today: nxConstraints (+ nxPin), emission limited by nxFalloff.
- **2019-02-05 — X-Particles 3.5 Tutorial - Fireworks** — https://www.youtube.com/watch?v=SyOcIw1ZLYU
  - What: three firework rigs — fountain, Catherine wheel and skyrocket — built from cone emitters, trails and question-triggered spawn bursts.
  - Tools: xpEmitter, xpGravity, xpTrail, xpQuestion/xpAction, xpSpawn.
  - Today: nxSpawn (At Age / On Death bursts) + nxTrail + nxGravity.
- **2019-02-05 — X-Particles 3.5 Tutorial - Controlled Fluids** — https://www.youtube.com/watch?v=McB6SzrzS8s
  - What: art-directing a FLIP liquid inside the domain — it follows a circle spline, then is pulled into a logo; xpSkinner mesh plus secondary particles emitted from the skin.
  - Tools: xpFluidFLIP domain, xpFollowSpline, xpCover, xpQuestion, xpSkinner, xpCache.
  - Today: nxFluids FLIP + nxFollowGeo or nxWarp Path, nxCover, nxMesher.
- **2019-02-05 — X-Particles 3.5 Tutorial - Plexus Geo** — https://www.youtube.com/watch?v=GLupjRXx3Ec
  - What: plexus-style connecting lines between surface particles (an XP take on a Python/VEX effect), applied to simple and scanned models.
  - Tools: xpEmitter (Shot, Polygon Area), xpTrail (Connect, joins off).
  - Today: still current on CPU (xpTrail Algorithm menu); GPU alternative: nxConstraints with Display Constraints.
- **2019-02-05 — X-Particles 3.5 Tutorial - Abstract Everyday** — https://www.youtube.com/watch?v=Er-Rx153CPE
  - What: building a still "everyday" abstract artwork with xpSkinner meshing points of geometry, splines and clones, plus surface cuts and trail tubes.
  - Tools: xpSkinner, xpGenerator, xpTrail.
  - Today: nxMesher for particle meshing; C4D Volume Builder for geometry blends; xpSkinner still on CPU.
- **2019-02-05 — X-Particles 3.5 Tutorial - Scale Modifier** — https://www.youtube.com/watch?v=CN0GmjPRiWc
  - What: xpScale 3.5 additions — Clamp Within Range for size variation and the Set Value operation for per-axis stretch.
  - Tools: xpScale.
  - Today: nxScale (layered, per-layer falloff and blend modes).
- **2019-02-05 — X-Particles 3.5 Tutorial - Spin Modifier** — https://www.youtube.com/watch?v=46Ye_s3HfxM
  - What: xpSpin Rotate operation — Absolute, Face Camera and Face Object (aim particles at a target null).
  - Tools: xpSpin, xpScale.
  - Today: nxSpin / nxRotate.
- **2019-02-05 — X-Particles 3.5 Tutorial - Depth of Field Techniques** — https://www.youtube.com/watch?v=3j7KsRyK3xA
  - What: fast noise-free DOF by mapping camera distance in the X-Particles material to blur/transparency and rendering with the Standard renderer instead of Physical; applied to constraint trails colored by speed.
  - Tools: X-Particles Material (depth mapping), xpTurbulence, xpConstraints, xpTrail.
  - Today: renderer DOF (Redshift) on nxGenerator / point-cloud output; the material trick remains CPU-only.

## Content Repository Tutorials 2019
- **2019-02-04 — Cloth Matrix** — https://www.youtube.com/watch?v=gW-26xx41Ik
  - What: an xpClothFX sheet is used only as a motion driver for a MoGraph Matrix (offset by a Random effector), instanced at render time into thousands of metallic boolean shapes.
  - Tools: xpClothFX, MoGraph Matrix, Random Effector, Cycles 4D Instance tag.
  - Today: nxConstraints cloth (+ nxPin) driving a Matrix or nxGenerator; Redshift instancing.

## Public Release 2018
- **2018-10-25 — New Features - Public Release 2018** — https://www.youtube.com/watch?v=vlBxJB-IPvg
  - What: R20 release highlights — C4D Fields as modifier falloffs, adaptive collisions, shader-space sampling, xpInfection with incubating/infected groups, xpSystemSort, xpWave, OpenVDB Mesher color/velocity tags, Alembic export, vector rotation, xpNetwork Constrain Axis.
  - Tools: C4D Fields, xpInfection, xpWave, xpOpenVDBMesher, xpVertexMap, xpNetwork, xpCache.
  - Today: nxFalloff, nxInfectio, nxWave / nxOcean, nxMesher outputs, nxCache Alembic.
- **2018-10-15 — FluidFX Speed Improvements - Public Release 2018** — https://www.youtube.com/watch?v=n8f4eFlABw4
  - What: rebuilt xpFluidFX SPH solver tweaked live with xpTurbulence, xpWind and an xpFlowField whirlpool, plus stable animated colliders.
  - Tools: xpFluidFX, xpTurbulence, xpWind, xpFlowField, xpCollider tag.
  - Today: nxFluids SPH/FLIP with nxTurbulence, nxWind, nxFlowField.

## Early Access 2018
- **2018-07-13 — xpFluidFX - X-Particles Early Access Speed Improvements** — https://www.youtube.com/watch?v=phYowXy4BX0
  - What: earlier cut of the same SPH demo — live modifier and flow-field interaction and fast, stable collisions.
  - Tools: xpFluidFX, xpTurbulence, xpWind, xpFlowField.
  - Today: nxFluids SPH/FLIP.

## xpReel Tutorials (2018)
- **2018-06-28 — xpReel Tutorials, Strange Cloth, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=fHDNLCeYfGQ
  - What: rendering the strange-cloth scene — custom cloth material, Cycles instance tag putting spheres on dust particles, DOF camera and clean render settings.
  - Tools: Cycles 4D, Cycles Instance tag, xpClothFX output.
  - Today: Redshift (or Blender Cycles via NeXus point cloud) for render; nxGenerator for instances.
- **2018-06-26 — xpReel Tutorials, Strange Cloth - X-Particles - Part 1** — https://www.youtube.com/watch?v=Ypi_fWn79EY
  - What: many planes simulated as cloth by one cloth setup, pulled away from camera by a Lorenz strange attractor, with dust particles stirred by the cloth.
  - Tools: xpClothFX (cloth emitter, modifier, deformer), Connect object, xpStrangeAttractors, xpTurbulence.
  - Today: nxConstraints cloth + nxPin; strange attractors have no GPU equivalent (keep the CPU modifier).
- **2018-06-20 — xpReel Tutorials, Water Helix, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=brUKYFSP_zI
  - What: rendering the water-helix mesh using speed-based particle color baked into a vertex map, plus lighting and shallow DOF.
  - Tools: Cycles 4D (Attribute point color node), xpOpenVDBMesher vertex maps.
  - Today: nxMesher color output read in Redshift / Blender attributes.
- **2018-06-18 — xpReel Tutorials, Water Helix -X-Particles - Part 1** — https://www.youtube.com/watch?v=c_DVzU5h5Kw
  - What: an xpFlowField along a helix spline steers an xpExplosiaFX sim that advects particles (colored blue→white by speed); the cache is meshed into a water helix.
  - Tools: xpFlowField, xpExplosiaFX (advection), xpEmitter, xpCache, xpOpenVDBMesher.
  - Today: nxExplosiaFX + nxWarp Helix (works on smoke) or nxFlowField; nxMesher with color transfer.
- **2018-06-14 — xpReel Tutorials, Particle Advection, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=YUW7NqPDk6Y
  - What: shading cached advected particles — mixing/adding glint and emissive shaders keyed on baked-in particle color, plus lighting and DOF.
  - Tools: Cycles 4D, xpCache.
  - Today: Redshift particle/point-cloud shading with NeXus channels.
- **2018-06-11 — xpReel Tutorials, Particle Advection, X-Particles - Part 1** — https://www.youtube.com/watch?v=lw5aRCM7k_w
  - What: MoGraph-cloned cylinders emit EFX fuel whose plumes (varied via temperature) advect particles; color data is burned into the cache for rendering.
  - Tools: xpExplosiaFX, MoGraph Cloner, xpEmitter, xpCache.
  - Today: nxExplosiaFX advecting an nxEmitter, nxCache.
- **2018-06-05 — xpReel Tutorials, Procedural Growth - Cycles 4D - Part 2** — https://www.youtube.com/watch?v=WGUggSQaBFs
  - What: rendering the coral growth with noise-masked gold-flake and emissive shaders driven by cached color data, plus DOF and motion blur.
  - Tools: Cycles 4D, xpCache, xpOpenVDBMesher.
  - Today: Redshift with nxMesher/nxBioLogic attributes.
- **2018-06-05 — xpReel Tutorials, Procedural Growth - X-Particles - Part 1** — https://www.youtube.com/watch?v=aCf110U-aBI
  - What: xpCellAuto growth meshed into coral, with a separate EFX system advecting floating dust and color data cached.
  - Tools: xpCellAuto, xpOpenVDBMesher, xpExplosiaFX, xpCache.
  - Today: nxBioLogic (coral / growth) + nxExplosiaFX.

## Quick Guides
- **2018-05-29 — Quick Guide - How to import OpenVDB files to X-Particles, then render with Cycles 4D** — https://www.youtube.com/watch?v=6qsxhWhJqTo
  - What: loading a downloaded VDB cloud into an xpExplosiaFX domain via xpCache and rendering it with Cycles 4D volume presets.
  - Tools: xpExplosiaFX domain, xpCache, Cycles 4D.
  - Today: C4D Volume Loader / Redshift Volume or a Blender Volume; nxExplosiaFX writes VDB output for its own sims.

## Early Access New Features (2018)
- **2018-05-25 — Early Access New Features - X-Particles, xpEmitter** — https://www.youtube.com/watch?v=MHPrgcvGtGA
  - What: emitter Modifier Field display (visualize turbulence forces as arrows/dots/lines), UV Emission Data (color particles from a video texture), emitters instanced by MoGraph, falloffs in questions.
  - Tools: xpEmitter, xpTurbulence, xpQuestion, MoGraph Cloner.
  - Today: NeXus 2026.1 viewport renderer draws fields; color from textures via nxColor / Mapping.
- **2018-05-23 — Early Access New Features - X-Particles, xpOVDBMesher** — https://www.youtube.com/watch?v=tCMndzHMKWk
  - What: OpenVDB Mesher transfers particle color and velocity to vertex maps (for render and post motion blur) and generates per-source object ID maps.
  - Tools: xpOpenVDBMesher, xpSplineFlow.
  - Today: nxMesher outputs color / velocity / emitter IDs.
- **2018-05-22 — Early Access New Features - X-Particles, Generators & Modifiers** — https://www.youtube.com/watch?v=Id2R5UtrptY
  - What: xpAttractor with scene objects as targets (nearest/furthest), modifiers reading physical data (temperature, fuel), and xpNetwork Constrain Axis keeping 90° grid paths under turbulence.
  - Tools: xpAttractor, xpNetwork, xpTrail, xpTurbulence.
  - Today: nxAttract; xpNetwork has no direct NeXus equivalent.

## X-Particles 4 Tutorials
- **2018-01-26 — X-Particles 4 - Nearest Particle Tutorial** — https://www.youtube.com/watch?v=7bl2ERnKpk8
  - What: a perpetual spawning system — flat, drag-damped particles spawn new ones when an xpQuestion detects a nearby particle.
  - Tools: xpLimit, xpDrag, xpQuestion (Nearest Particle), xpSpawn action, collisions.
  - Today: nxQuestion neighbour search + nxSpawn; nxLimit, nxDrag.
- **2018-01-09 — StrangeOrb Tutorial** — https://www.youtube.com/watch?v=1k2AK6SUBzU
  - What: particles driven by xpStrangeAttractors rattle inside a sphere collider (normals inside), rendered in Cycles 4D with an HDRI environment.
  - Tools: xpStrangeAttractors, xpCollider tag (inside), xpTrail, Cycles 4D.
  - Today: nxCollider for the shell; strange attractors stay CPU-only.
- **2017-12-14 — xpExplosiaFX - Rendering Guide** — https://www.youtube.com/watch?v=o3xq7I1FRtY
  - What: simple sphere-sourced smoke/fire rendered with a Cycles 4D volume material (absorption + scatter, blackbody), then exported as VDB for Redshift and Octane.
  - Tools: xpExplosiaFX, Source tag, Cycles 4D volume nodes, VDB export.
  - Today: nxExplosiaFX with the default Redshift smoke material / VDB output; Pyro link in C4D 2025.3+.

## Cycles 4D Updates
- **2017-12-13 — Cycles 4D Update - Build 247** — https://www.youtube.com/watch?v=h2jZtHBd0PU
  - What: node editor upgrades (channel colors, contextual filter, mini viewer, wire modes, per-node output preview) and camera post effects (bloom, glare, vignette, filmic).
  - Tools: Cycles 4D.
  - Today: Cycles 4D is no longer developed — Redshift post effects / Blender compositor.

## X-Particles 4 Sneak Peeks
- **2017-11-28 — xpFluidPDB & xpFluidFX - X-Particles, New Feature Sneak Peek** — https://www.youtube.com/watch?v=7gGSdnJXbaE
  - What: xpFluidPBD for fast small-scale liquids (external pressure tendrils, viscosity, surface tension, works with constraints) and xpFluidFX hybrid SPH with per-emitter fluid settings for mixed densities.
  - Tools: xpFluidPBD, xpFluidFX, xpSplineFlow, xpOpenVDBMesher.
  - Today: nxFluids PBD/SPH/FLIP + Mixer per emitter.
- **2017-11-22 — xpExplosiaFX Part II - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=m98WDn-uIKg
  - What: XP modifiers layered into EFX forces, xpFlowField steering smoke, and one-click particle advection with color inherited from the sim.
  - Tools: xpExplosiaFX, xpTurbulence, xpRotator, xpFlowField.
  - Today: nxExplosiaFX with nx modifiers and nxWarp on smoke.
- **2017-11-20 — xpExplosiaFX Part I - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=j_wnmiu3UsQ
  - What: EFX basics — domain, Source tag, voxel size vs detail, channel display, fuel/ignition/buoyancy, EFX wind and turbulence, collider tags.
  - Tools: xpExplosiaFX, EFX Source tag, EFX Collider tag, EFX Wind.
  - Today: nxExplosiaFX (sources in the Sources tab, nxCollider).
- **2017-11-13 — xpVertexMap Maker - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=c-rCBcBmBCY
  - What: animated vertex maps from texture, vertex speed, particle contact or explosion data, used to drive displacement, emission and xpScale.
  - Tools: xpVertexMap, xpScale, xpDrag.
  - Today: nxFalloffMap (C4D 2026.1) bakes nxFalloff (incl. Wet) to vertex maps.
- **2017-11-06 — xpOpenVDB - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=aNFOQ2jOL50
  - What: OpenVDB Mesher for particles and geometry — voxel/radius control, stackable filters, fill with spheres, remeshing and live booleans.
  - Tools: xpOpenVDBMesher.
  - Today: nxMesher for particles; xpOpenVDBMesher / C4D Volume Builder for geometry remesh and booleans.
- **2017-10-30 — xpStrangeAttractors & xpNewtonGravity - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=XRqy2K2msZ0
  - What: eight chaotic attractor presets with scale/delta/constants, trails meshed into abstract shapes, and Newton gravity giving objects orbital pull with distance-based resizing.
  - Tools: xpStrangeAttractors, xpGravity (Newton), xpTrail, xpOpenVDBMesher.
  - Today: nxGravity (Effect Towards) for orbits; strange attractors remain CPU-only.
- **2017-10-23 — xpCirclePacker & xpCellAuto - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=rwhY3v01zfk
  - What: Circle Packer emits non-overlapping particles with min/max radius and scale curves; Cell Auto grows patterns via elementary rules, Game of Life and diffusion-limited aggregation.
  - Tools: xpCirclePacker, xpCellAuto.
  - Today: nxBioLogic replaces xpCellAuto; circle packing has no direct equivalent (approximate with nxPush + nxScale).
- **2017-10-16 — xpSplineFlow - X-Particles 4 - New Feature Sneak Peek** — https://www.youtube.com/watch?v=TgWvZXlw94Y
  - What: particles follow any spline with per-handle Along/Towards/Rotate/Attraction forces, mixable with turbulence and fluids.
  - Tools: xpSplineFlow, xpTurbulence.
  - Today: nxFollowGeo (spline mode) or nxWarp Path.
- **2017-10-09 — xpFlowField - X-Particles - New Feature - Sneak Peek** — https://www.youtube.com/watch?v=S282_UbC63s
  - What: a velocity field built from splines, geometry normals/tangents, particles/trails or shaders, with falloff and layered modes.
  - Tools: xpFlowField.
  - Today: nxFlowField (NeXus 2026); xpFlowField still available in Fused.
- **2017-10-02 — xpClothFX - X-Particles - New Feature - Sneak Peek** — https://www.youtube.com/watch?v=5834UlTSS84
  - What: cloth tag/deformer with pinning, colliders, self-collision, map- or group-driven tearing and a Cloth Surface object for torn edges and thickness.
  - Tools: xpClothFX tag, Cloth Pin tag, Cloth Surface, xpCollider tag.
  - Today: nxConstraints + nxPin, nxDeformer for tearing (GPU cloth announced for the next beta); xpClothFX still on CPU.

## Webinars
- **2017-07-26 — Maxon Webinar 2017 Cycles 4D Motion Design** — https://www.youtube.com/watch?v=nRgDMUnwldM
  - What: Cycles 4D for motion design — node materials (stacked mix shaders, Fresnel, glass), CPU/GPU rendering, MoGraph and X-Particles rendering.
  - Tools: Cycles 4D, MoGraph, X-Particles.
  - Today: Cycles 4D is no longer developed — Redshift in C4D.

## Tutorials (2017)
- **2017-07-21 — xpWind Twister - Tornado Effects - Full Tutorial** — https://www.youtube.com/watch?v=6uumSQpGOrA
  - What: original tornado setup — cloned xpWind fans spiral particles upward; variants with xpSkinner liquid, lava/snow and an xpGenerator fish school.
  - Tools: xpWind, MoGraph Cloner, xpSkinner, xpGenerator.
  - Today: nxWarp Helix/Twist + nxTurbulence or nxWind layers; nxMesher, nxGenerator.

## Other (no technique)
- 2018-10-08 — X-Particles Speed Improvements - Public Release 2018 — https://www.youtube.com/watch?v=WmVMn06Guhk
- 2018-10-05 — X-Particles Client Story - Territory Studio — https://www.youtube.com/watch?v=RTn-KSgC4-0
- 2018-05-01 — X-Particles Sneak Peek - Speed; E.A.R - 10th May — https://www.youtube.com/watch?v=-TMsxTsL5NY
