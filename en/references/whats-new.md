# What's new — INSYDIUM release timeline (newest first)

Checked 2026-11-03 against insydium.ltd news + docs.insydium.ltd. **Default to the newest tool that does the job**, then give the older/CPU route as a fallback. Use this file to date a tutorial: if a Top Tip shows an object, it can't be older than the release that introduced it.

## Announced: next NeXus beta (teased 3 Nov 2026 in the final Top Tip Tuesday, #196)
- **Unified dynamics** coming to the GPU engine: **cloth**, **ropes / cords**, **rigid bodies**, **tearing + fraying**, and **two-way coupling with EFX** (smoke/fire pushing and being pushed).
- Not shipped yet as of Nov 2026 — until it lands, use nxConstraints (cloth/soft-body style), C4D Rigid Body tags on xpGenerator geometry (see recipe 2025-08-26), or CPU xpCloth.
- Top Tip Tuesday series ended with that episode (weekly since Feb 2023).

## NeXus 2026.1 Beta (1 Oct 2026; Beta 2 7 Oct; Beta 3 30 Oct) — Cinema 4D + Blender, one engine
- **One unified GPU system ("Theron", Vulkan + own compute core):** identical solvers/modifiers/results in C4D and Blender; features ship to both at once. NVIDIA/AMD/Intel on Windows & Linux (Vulkan 1.3), Apple Metal 3 (macOS 13+). ≥4 GB VRAM.
- **Hosts:** C4D R19+ (Win/mac; native particles/Pyro link needs **C4D 2025.3+**), Blender 4.3+ incl. 4.5 LTS and 5.x (Win/mac/Linux, Windows ARM64).
- **Licence:** NeXus licence works in both hosts (Blender owners get C4D free); perpetual + 12 months updates; Fused/X-Particles owners −50%. **Beta free for any INSYDIUM licence** (or request a free beta licence); in C4D any INSYDIUM licence unlocks full Fused + NeXus beta while the beta runs.
- **New solvers/objects:**
  - **nxMPM** — multi-material: liquid, elastic, snow, sand, brittle, metal, foam; 2 solver modes (MPM / CK-MPM), grid memory estimate, openable walls, collider support, **material change by age/speed/stretch/damage** (Mixer), fracture, auto-sleep. **nxMaterial** = one-click MPM setup (presets: Snow packed/sticky, Sand wet, Glass bottle, Metal steel…). Sparse solver (domain optional), per-emitter material overrides (Sand Powder Fine, Sand Dry, Brittle Concrete, Elastic Rubber, Liquid Water…; Momentum 0 for dry), Auto Sleep (Sleep Speed 5 cm/s, Wake Speed/Spread), color by Material or Sleep State. Tech preview 16 Sep 2026, trainings 7 & 11 Oct 2026.
  - **nxDeformer** — mesh follows particles, **tearing** + remeshing (Blender: subdivision & curve deformation).
  - **nxPin** — anchor particles (select by Falloff/Groups, ID list, particle data, object; In Place or To Object) → cloth/rope with nxConstraints, solids with nxMPM.
  - **nxBind** — hold particles inside a deforming volume, release by age/life/speed/temperature; Break tab Falloff (default) / Age range / Color Brightness, Chunks + Chunk Size, Soften (off once a solver takes over). Training 21 Oct 2026 (crumbling character → nxMPM).
  - **nxBioLogic** — reaction-diffusion, differential growth, Physarum, particle life, coral, primordial; tube meshes.
  - **nxOcean** — GPU ocean: wind/spectrum (Phillips, Pierson-Moskowitz, JONSWAP), foam, spray, wakes, shorelines, **beaches with swash/surf** (Beta 3), floating objects, waves reflecting off colliders, **FLIP coupling**.
  - **nxShatter** — GPU fracture (Voronoi, Glass, Wood, Bricks; sub-fracture; triggers; driven by emitter or MPM damage).
  - **nxWarp** — 19 cage warps for particles, meshes **and smoke** (Helix, Path, Wind gust wave, Melt, Noise, FFD, Scroll, Bend, Twist…); Deform / Guide / Flow modes. Shared Twist/Taper/Bulge + Fit to Parent; Guide Strength (low = particles escape); Flow profiles Square/Circle/Star/Custom, exit only through the end face; warps stack (downstream bounds must cover upstream output). Training 30 Oct 2026.
  - **nxSpawn** (Beta 3) — child particles (Instant / At Age / On Collision / On Death; Rate/Burst/Pulse; 8 sub-layers).
  - **nxFluid2D** (Beta 3) — realtime 2D fluid in a UV map. **nxScatter** (Beta 3) — points on meshes → nxGenerator.
  - **nxSystem** — preset folder structure (C4D object; Blender "Pipeline Manager" / Hierarchy).
- **Control:** 16 nxFalloff modes (Box, Linear, Sphere, Noise + Cylinder, Torus, Box Frame, Capsule, Cone, Object, Points, Spline, Attribute + Curvature, AO, **Wet**); every modifier layer has its own Falloff list; **nxFalloff Modifier** layers Invert, Clamp, Remap, Step, Quantize, Curve, Cycle, Blur, memory (Freeze, Decay, Delay, Grow); **Cyclic** layer (nxColor, nxFlowField); Mapping: one layer → many targets.
- **Liquids:** FLIP/APIC **non-Newtonian** (Flow Index, Yield Stress), **Wall Friction**, Recolor by Density/Viscosity, Mixer per emitter/group (density, viscosity, flow index, yield stress, surface tension), ocean coupling. Defaults (Blender): voxel 0.1 m, FLIP fraction 95%, CFL 0.7.
- **nxCollider:** adhesion, attraction, repulsion, surface-mapped settings, collection instances, Fill Hollows. **nxMesher:** UV advection, Detail Aware smoothing, nxGroups source, camera UV projection, Blend into Ocean. **nxCache:** frame range, Disk Reserve, **Alembic single file, PLY**, Local Coords. **nxEmitter:** Initial State + Keep Stored Age, up to 8 display channels, Match Solver Resolution, Stick to Source, emit from point clouds / **Gaussian splats** / Blender particle systems.
- **Workflow:** new shared viewport renderer (better voxel drawing for FLIP/EFX/FlowField); Add menu split into Presets / Generators / Dynamics / Modifiers / Warps; help text on every parameter; GPU selection; shader precompile.
- **C4D-only:** native **C4D particles & Pyro link** (preview video 9 Oct 2026) (NeXus modifiers drive native particles; nxExplosiaFX ↔ Pyro smoke/fire exchange), NeXus Project Settings (HUD / Document: substeps, GPU, Rewind on Load), **nxFalloffMap** (falloffs → vertex map / vertex color tags), **nxConvert** (xpEmitters & groups → NeXus in one undo), NeXus modifiers on plain xpEmitters, default Redshift smoke material for nxExplosiaFX VDB, nxShatter Make Editable → null of pieces, GPU memory freed before render.
- **Blender-only:** Particle Info node (shader/GN), Collection Instances, vertex-map falloffs, GLSL Script window, **Quill** (AI that builds nxQuestion setups from plain-language prompts — configure a cloud model with API token or local Ollama/CLI; treat as a first draft), **C4D scene import/export**.
- **Breaking changes in the beta:** PBD strengths no longer depend on particle size (Beta 2); Pulse Interval start→start, nxWarp Flow Reach 0% (300% = old), nxSpeed layer = Acceleration, nxGenerator Spawn → Bias, nxCache Auto → Auto Frame Range, FLIP & MPM respect collider group filters (Beta 3).

## NeXus for Blender 2026.0 (13 Jul 2026; 2026.0.1 16 Jul)
- Preceded by a public **Blender beta (1 Jun 2026)** and a run of Official Training / Quick Guide videos (Jun–Jul 2026); short tool previews Apr–May 2026.
- Blender specifics seen in trainings: **Export ▸ Create Point Cloud** (auto Geometry Nodes + Particle Info material; viewport particles don't render), **Liquid Fill** preset + emission type, **nxSheeter** (fills gaps in thinning FLIP sheets), nxExplosiaFX **VDB Output: Live** → Blender Volume + preset fire material, nxMesher Transfer Velocity for Cycles/Eevee motion blur, Particle Console, Render ▸ Lock Interface.
- First Blender release: full NeXus set (PBD/SPH/FLIP/APIC fluids, nxFoam, nxExplosiaFX, nxInfectio, nxDendrite, constraints, flocking, P-P collisions, emitters, nxGenerator, nxMesher, nxTrail, nxUpres, all forces, nxQuestion + **Quill AI**). Extension install, 21-day trial, perpetual + 12 months.
- 2026.0.1: per-emitter HUD counts, nxGenerator motion blur, console emitter filter.

## Fused 2025.4.1 (25 Feb 2026) — service update
- FLIP/APIC color by particles-per-voxel (density diagnostics), better advection at domain edges, faster EFX DirectX 12 / Metal ray marchers; Jidou playback modes (stop/loop/ping-pong/continue) for jdFlowCam & jdGeoFlow; mtEdgeSpline handles n-gons; licence server fallbacks; xpBranch crash in **C4D 2026** fixed. Builds: NeXus 514, X-Particles 1875.

## Fused 2025.4 (8 Dec 2025) — the big GPU release for C4D
- **Rewritten NeXus GPU core** (faster, less VRAM); layered GPU falloffs; Data Mapping with looping.
- **nxExplosiaFX (new, GPU smoke/fire)** — emit from objects, splines, vertex maps, shaders, particles; layered emitters, collisions, forces; volumetric GPU viewport.
- **nxFluids FLIP & APIC (new)** — variable viscosity, liquid sheeting, surface-tension tendrils.
- **nxMesher (new GPU)** flicker-free, layered smoothing, outputs color/velocity/emitter IDs. **nxFoam** rewritten (layers: foam, bubbles, spray). **nxSplash (new)** crown splashes.
- Layered modifiers (Photoshop-style stack: Strength, Normal/Multiply/Add/Max, per-layer GPU falloff, per-layer mapping): nxTurbulence, nxScale, nxLimit, nxSpeed, nxColor, nxSpin, **nxDirection** (existed since early 2024 as a simple +Z push; 2025.4 made it layered with Direction Force / twist / attract). nxFollowGeo multi-spline + Guide/Force modes. nxQuestion variation + better neighbour search.
- **Jidou (new suite):** jdAniMate, jdDriver, jdFlowCam, jdGeoFlow, jdGeoRoll.
- Public previews before release: Modifier Improvements 1–3 (Jul–Aug 2025), Core Improvements (11 Sep 2025: ~20 % faster, no first-play shader-compile pause), NeXus ExplosiaFX (16 Oct 2025), Final (26 Nov 2025), Jidou (8 Dec 2025).
→ Any tip using **nxExplosiaFX, nxFluids FLIP/APIC, nxMesher, nxSplash, layered nxDirection or Jidou dates from Dec 2025 or later** (or from the summer–autumn 2025 previews). Older smoke/fire/FLIP tips use CPU xpExplosiaFX / xpFluidFLIP / xpOpenVDBMesher.

## Fused 2024.x
- **2024.4** (10 Feb 2025) — stability only (cache, Bullet, VDB import fixes).
- **2024.3** (10 Sep 2024) — **C4D 2025 compatibility**; keyframable xpFlowField layers; misc NeXus fixes.
- **2024.2** (9 May 2024) — **Fused Create** (buy components) / Complete; NeXus: faster core, **animated-geometry collisions**, new **nxColor, nxCover, nxFollowGeo, nxSticky**; Taiao growth-point scatter, toLeaf venation + presets; TerraformFX **Advanced Terrain Shader**, curvature channel, **tfDistribute**, new noise generator; MeshTools **mtPolyFold**, **mtPointProject**.

## Fused 2023.x
- **2023.3** (5 Jul 2023) — NeXus: GPU versions of popular XP modifiers, **nxQuestion redesign (object hierarchy + coding)**, **Data Mapping**, new **nxFlock, nxInfectio, nxWave, nxUpres, nxAvoid**; Taiao overhaul (growth animation, forces); MeshTools **mtRayline**, **mtSplineFX**; TerraformFX landscape animation tools; X-Particles caching improvements.
- C4D 2024 compatibility: 2023.3.1 (28 Sep 2023).

## Earlier
- **NeXus unveiled Sept 2022** (GPU solvers inside X-Particles; nxPush, nxBlend, nxConstraints, nxFluids PBD/SPH, nxTurbulence…).
- Top Tip Tuesday series started **Feb 2023** (xpTrailDeformer episode); **194 episodes** by the final one on 3 Nov 2026 (per-video recipes in `recipes/`).
- X-Particles 4 (2017): xpFluidFX, xpExplosiaFX, xpClothFX, Bullet.

## "Newest way" cheat sheet (what to suggest first in Nov 2026)
| Effect | Newest (2026.1 beta) | Stable C4D (Fused 2025.4.x) | Legacy CPU |
|---|---|---|---|
| Liquids | nxFluids FLIP + Mixer, non-Newtonian, wall friction; nxLiquid preset (Blender) | nxFluids FLIP/APIC + nxMesher | xpFluidFLIP / xpFluidFX |
| Ocean | nxOcean (beach, FLIP coupling) | nxWave in FLIP | xpOcean |
| Smoke/fire | nxExplosiaFX + nxWarp on smoke; Pyro link (C4D 2025.3+) | nxExplosiaFX | xpExplosiaFX |
| Snow/sand/jelly/metal/glass | **nxMPM / nxMaterial** | nxFluids SPH Granular, nxConstraints | xpFluidFX granular, xpCloth plasticity, Bullet |
| Destruction | nxShatter (+MPM damage) | xpShatter + Bullet | xpShatter |
| Cloth/rope | nxConstraints + nxPin; nxDeformer tearing | xpClothFX | xpClothFX |
| Growth/organic | nxBioLogic, nxDendrite | nxDendrite (Blender) / xpBranch | xpCellAuto, xpBranch |
| Spawning | nxSpawn | nxQuestion Spawn action | xpSpawn/xpMultiSpawn |
| Shaping streams | nxWarp (Path, Helix, Flow) | nxFollowGeo, nxDirection | xpFollowSpline, xpVortex |
| Logic | nxQuestion + Quill (Blender) | nxQuestion | xpQuestion/xpAction |
| Falloffs | 16 nxFalloff modes + nxFalloff Modifier, Wet/AO/Curvature | nxFalloff | C4D Fields |
