# Effect index — "I want to make…" → what to use

**Newest-first rule:** for every effect check the "Newest way" table in `references/whats-new.md` (NeXus 2026.1 beta objects: nxMPM, nxMaterial, nxOcean, nxWarp, nxShatter, nxSpawn, nxBioLogic, nxDeformer, nxPin, nxBind, nxFluid2D, nxScatter, Pyro/native-particle link in C4D 2025.3+). The lines below list all routes.

C4D-CPU = classic X-Particles · GPU = NeXus (`nx*`, C4D or Blender) · Fused = MeshTools/TerraformFX/Taiao/Jidou. File names are under `references/`. Recipes (one per Top Tip Tuesday / tutorial, newest first, each with a newest-equivalent note) are indexed in `recipes/README.md` — grep it for a tool name.

## Liquids & fluids
- Water pour / splash / fill container → **GPU** nxFluids FLIP/APIC (large) or PBD (small, stylised) + nxMesher (Zhu-Bridson) + nxFoam → `c4d/nexus-core.md`, `c4d/nexus-dynamics-logic.md`. Blender one-click: nxLiquid → `blender/nexus-blender.md`. CPU: xpFluidFLIP / xpFluidFX + xpOpenVDBMesher → `c4d/xp-generators-dynamics.md`.
- Honey / viscous / goo → nxFluids PBD/SPH Viscosity + nxConstraints Viscosity layer (moderate stiffness, more iterations); Blender: FLIP non-Newtonian.
- Paint mixing / two-colour fluids → nxFluids tags per emitter + **nxBlend** (color) → `c4d/nexus-modifiers.md`.
- Oil + water, water + sand → per-emitter nxFluids tags (SPH Granular for sand).
- Ocean / waves / shoreline → Blender/2026: **nxOcean** (+FLIP coupling); C4D-CPU: xpOcean; waves inside a fluid: nxWave; rolling choppy water: nxVorticity.
- Whitewater / foam / bubbles / spray → nxFoam layers (Simulation Bounds = fluid domain).
- Splash at impact → nxSplash (Start Time = impact frame).
- Melting object → nxFluids + nxGravity (melt by falloff/age), or xpDeformer/nxDeformer; MPM elastic→liquid via Mixer (Blender 2026.1).
- Condensation / droplets on glass → QuickTools Condensation; nxConstraints Surface Tension.
- 2D ink in a UV map / interactive dye → nxFluid2D (2026.1).

## Smoke, fire, explosions
- Smoke / fire / campfire / candle → **nxExplosiaFX** (GPU) → `c4d/nexus-core.md`; CPU xpExplosiaFX + Source tag → `c4d/xp-generators-dynamics.md`. Quick start: QuickTools EFX Basic Flame / Camp Fire.
- Explosion → nxExplosiaFX with Pressure + Fuel Frame Limits, Gas Expansion; add debris via xpShatter/nxShatter.
- Smoke deformed by objects / turbulence → Dynamics layers (Turbulence, Vorticity, Wind) + Modifiers subtab (nxDirection, nxAttract).
- Embers / dust carried by smoke → Particle Advection subtab.
- Render smoke → cache to OpenVDB (xpCache / nxCache) → renderer volume; C4D 2026.1 beta adds default Redshift smoke material.

## Destruction, cloth, soft bodies
- Shatter / fracture / recursive breaking → xpShatter (Volume/Surface, recursive layers, Collision trigger + xpBullet) or nxShatter (2026.1).
- Rigid bodies → xpBullet Rigid Body / Collider tags, xpBulletConstraints (hinges, breakable).
- Cloth, flags, tearing, **metal dents** → xpClothFX (Create Cloth) + xpCloth tag (Plasticity, Tearing) → `c4d/xp-generators-dynamics.md`. GPU alternative: nxMPM Metal/Elastic (Blender 2026.1).
- Jelly / soft body → nxConstraints Birth connections (stiffness, break) or xpDynamics tag; nxMPM Elastic.
- Sand, snow, gravel, grains → nxFluids SPH Granular (substeps up to 30) or nxMPM Sand/Snow; friction layer for piles.
- Crumbling / peeling / disintegration → nxInfectio (Infected Lifespan 1 frame) + nxTurbulence; stick-to-source emitters + nxKill.

## Particle motion & motion-graphics
- Particles form a logo/shape, morph between shapes → nxCover (Sequence / Time to Target) or xpCover; xpInherit (copy another emitter's formation).
- Flow along splines / spirals / tubes → nxFollowGeo spline mode (Twists, Offset) or xpFollowSpline / xpSplineFlow.
- Crawl over surfaces / edges → nxFollowGeo surface/edge mode, xpFollowSurface.
- Curl-noise wisps → nxTurbulence (Curl) / QuickTools Curl Noise.
- Swarms, birds, fish, chase → nxFlock (behaviours + Pursuit/Flee reactors).
- Orbits / gravity wells → nxGravity Effect Towards, xpGravity Newton.
- Tornado / vortex → xpVortex (Helix), nxRotate.
- Strange attractor lines → xpStrangeAttractors + xpTrail.
- Circuit / PCB / network paths → xpNetwork + xpTrail; mtShortestPath growth.
- Particle reveal / dissolve / disintegration → nxInfectio, nxKill with falloff, nxScale by age.
- Particles sticking / gathering on object → nxSticky / xpSticky, xpCollider Connect on Collision.
- Speed ramps on sims → cache then xpCache/nxCache Retiming → Custom spline.
- Upres a light sim → nxUpres (2 k → 80 k particles).
- Particles driven by audio → xpSound, xpSoundDisplacement, xpSoundShader.
- Text / counter sprites → xpSprite Text + xpText.

## Trails, lines, growth
- Particle trails (wiggly, natural) → xpTrail + **xpTrailDeformer** (Top Tip #1) → xpSplineMesher / Sweep / Hair; Blender nxTrail Splines.
- Plexus / nearest connections → xpTrail Algorithm Nearest by Distance + xpPlanarMesher; nxConstraints Distance + Display Constraints.
- Lightning → xpElektrix, **mtSplineFX** (forks), xpBranch.
- Lasers / light rays bouncing → **mtRayline** (X-Particles shape for particle rays).
- Branches, roots, tendrils, trees → xpBranch + Sub-Branch, xpTendril, nxDendrite, Taiao toTree (grow into a logo volume).
- Cellular / coral / reaction-diffusion growth → xpCellAuto (DLA), nxBioLogic (2026.1).
- Blooming particle-trail flower → nxFollowGeo/nxTurbulence + trails (recipe).

## Mesh / procedural modelling (MeshTools)
- Tech panel growth / inset growth → mtInset driven by animated field/shader.
- Origami unfold → mtPolyFold. Dissolve polys → mtPolyScale. Shells/thickness → mtShellGen. Greebles → mtInset + mtShellGen + mtSubDivider stack.
- Toon / outline lines → mtEdgeSpline Outline/Contour.
- Fractals → mtFractal. Remesh for sims → mtRemesh.
- Dynamic MeshTools (falling inset pieces) → MeshTools stack + xpDynamics.

## Terrain & nature
- Mountains, erosion → TerraformFX tfNoise + tfErosionHydraulic (Inertia) + tfHighpass → `c4d/terraformfx.md`.
- Rivers, roads, rocks → tfRiver (+tfRiverExport), tfRoad, tfRock. Logo → terrain: tfTrace.
- Animated rolling landscape → Time Dependent operators / animated tfNoise offset ("Terrain Flow").
- Snow on tops / moss in crevices → emitter Topology tab (height/slope/curvature) or Terrain shader layers.
- Grass, plants, trees, flowers, wind → Taiao toGrass / toPlant / toTree / toFlower → `c4d/taiao-jidou.md`. Falling leaves → toPlant X-Particles output.
- Rain with splashes → xpRainRig / QuickTools Simple Rain + xpCollider spawn; wet surfaces → xpWetMap.

## Animation helpers (Jidou)
- Wiggle/pulse any parameter → jdDriver (Noise/Wave/Time). A→B moves → jdAniMate. Camera paths → jdFlowCam. Rolling objects → jdGeoRoll.

## Pipeline
- Cache / VDB / Alembic → `c4d/xp-system-cache-control.md`, `blender/nexus-blender.md` (nxCache).
- Duplicate/reuse cached sims to populate scenes → xpCache playback offsets/retime, multiple cache objects.
- Rendering in Redshift/Octane/Cycles → `c4d/xp-utilities-render.md`; Blender: Create Point Cloud + Particle Info node.
- Converting old CPU scenes → nxConvert (C4D 2026.1 beta) + `legacy-vs-nexus.md`.

- `references/tools/` — tool cards: one page per tool (79 tools) with every setting/value used in the videos, pitfalls and all recipes. Start here for "how do I set up nxMPM / nxFLIP / xpTrail".
