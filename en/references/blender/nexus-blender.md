# NeXus for Blender (2026.0 → 2026.1 Beta 3)

Source: docs.insydium.ltd/blender/* (checked 2026-11-03; latest = 2026.1 Beta 3, 30 Oct 2026). Paraphrased.
Most object parameters are **identical to NeXus in C4D** — read `../c4d/nexus-*.md` for nxConstraints, nxFluids (PBD/SPH/FLIP-APIC), nxExplosiaFX, nxMesher, nxFoam, nxSplash, nxWave, nxQuestion, Mapping, nxFalloff and every nx modifier. This file covers what's Blender-specific or new.

## Setup
- Blender **4.3+**, INSYDIUM licence, online check at each start, access token. Install as **extension**: Preferences → Get Extensions → add INSYDIUM repository (with access token) → install NeXus → enter licence in Add-ons.
- Add objects: **Add ▸ INSYDIUM NeXus ▸ Presets / Generators / Dynamics / Modifiers / Warps** (split in 2026.1). Settings live in **Properties ▸ Physics** tab (not the modifier stack, not Geometry Nodes).
- **NeXus Hierarchy** (N-panel ▸ NeXus): tree of all NeXus objects; **top→bottom = evaluation order**; indent = child; folders disable together; deleting a row deletes the objects. **nxSystem** (Beta 3) adds a preset folder set.
- **NeXus Panel** tabs: Object Properties, Groups Affected, Mapping, Falloff. **Particle Console** inspects live particle data (filter by emitter). Preferences: Compute Device, Precompile Shaders, VRAM.
- Units: Blender is **metres, Z-up**; C4D is **cm, Y-up** (Blender Z+ = C4D Y+; 1 m = 100 cm). Blender hides irrelevant options; C4D greys them out.

## Core objects (Blender)
- **nxEmitter** — Shape Rectangle/Disc/Sphere/Box/Object (meshes, curves, point clouds, nxFluids domains, Collection Instances, Gaussian splats on Blender 5.3+, Blender particle systems); Emission Rate / Pulse (Interval = start→start since Beta 3) / Shot / **Liquid Fill** / **Liquid Flow**; Mode Random / Regular / Hexagonal; Speed 1.5 m/s, Radius 0.03 m, Mass 1, Lifespan 90; Motion Inheritance; **Stick to Source**; Initial State (needs ≥1 simulated frame); up to 8 **Display Channels**; **Export ▸ Create Point Cloud** (required for rendering / Particle Info node) and Create Gaussian Splats. Match Solver Resolution overrides radius/spacing.
- **nxLiquid** (Presets) — one-click Fill (standing water, Fill Level 30%) or Flow (pour): emitter + nxFluids (FLIP default) + mesher + foam (both start disabled) + gravity under one empty; Resolution master slider.
- **nxCollider** — Colliders list (meshes/curves/collection instances); Normals Outside / Inside / Any / Outside-Fill Hollows; Bounce 40%, Friction 1%, **Adhesion**, Attraction/Repulsion; **Global on by default** (first collider drives all). FLIP/APIC: Any acts as Outside; Scatter ignored by FLIP/APIC/MPM.
- **nxGenerator** — instance meshes on particles; Display Preview (viewport only) vs **Geometry** (needed for render/collisions); layers with Bias (Random mode), Mode random/sequence/index; native **motion blur** in Cycles/EEVEE.
- **nxTrail** — Lines (preview) or **Splines** (real curve objects → Curve to Mesh/geometry nodes); Length by time or distance; Connections.
- **nxCache** — Build: Record, Format NeXus / **Alembic (single file)** / **PLY** / OpenVDB for EFX, Directory, Auto Frame Range, **Disk Reserve** 1024 MB; Playback: Local Coords, Retiming Disabled (Offset, Time Scale) / Frame / Time / Custom spline. Empty Cache deletes everything.
- **nxGroup** — groups (+ gradient/noise color in Beta 3; Shader/Object Color modes removed).
- **Node integration** — Shader/Geometry editor: **Add ▸ NeXus ▸ Particle Info** (Color, Speed, Age, Life, Rotation, Scale, Radius, ID…). Emitter needs Create Point Cloud + channels in Transfer Properties. Raw attributes `nx_color` etc. (`position`, `radius` unprefixed). ID float in shaders, int in GN.

## New in 2026.1 Beta (Blender first, most also in C4D beta)
- **nxMPM** — Material Point Method multi-material solver: Liquid, Elastic (jelly), Snow, Sand, Brittle (concrete/glass/rock — cracks), Metal (bend → tear), Foam. Domain box (Resolution/Voxel Size, walls Closed/Open/Kill, Use Bounds off = grid follows), solver MPM or CK-MPM (crisper contacts, heavy; forced by concrete/glass/rock/ice/steel presets). Density, Viscosity, Stiffness (E), Poisson Ratio, CFL, substeps, Auto Sleep, fracture (Fragment Size, Strength, Toughness — MPM only). **Mixer**: blend materials by Speed/Age/Height/Damage. Snow strength in Pa.
- **nxMaterial** (Presets) — one-click MPM setup (emitter + nxMPM + mesher + gravity).
- **nxDeformer** — mesh/curve follows particles (pair with nxMPM): Bind Radius 0.2 m; Deform Mode Breaking → tears using Tear Damage 0.9 / Tear Stretch 50%.
- **nxPin** — anchor selected particles. **nxBind** — hold particles to a deforming mesh/collection, release by criteria (Stay Released on).
- **nxBioLogic** — organic growth: reaction-diffusion (Feed/Kill), coral, differential growth, Physarum (slime mould), particle-life ×2; Meshing tab builds tubes; Stop Frame 0 = never stops.
- **nxDendrite** — branches / network / Bethe lattice / dendrite crystal growth from particles (layered, Spawn, Curl bend).
- **nxOcean** — GPU ocean (Phillips / Pierson-Moskowitz / JONSWAP spectrum, Wind Speed/Direction, Choppiness, Patch Size > 0.64·wind² m), whitecap foam, spray via an nxEmitter, **shoreline** breaking/swash/sand beach, wave reflection off colliders (Wave Masking 0 by default), **FLIP coupling** (link ocean in nxFluids domain; nxMesher Blend into Ocean). Geometry On Render by default.
- **nxWarp** — 19 cage warps (Bend, Bulge, Cast, FFD, Flatten, Helix, Melt, Noise, Path, S Bend, Scroll, Shear, Spherify, Squash&Stretch, Taper, Twist, Wave, Wind, Wrap); Modes Deform / Guide / **Flow**; Reach/Extent (Flow Reach 0% default in Beta 3 — 300% = Beta 2 behaviour).
- **nxShatter** — Voronoi/Glass/Wood/Bricks fracture, Solid (closed mesh) / Surface, Gap, SubFracture layers, triggers Frame/Collision, Driven By nxEmitter or nxMPM (Build Shatter along MPM cracks).
- **nxSpawn** — child particles: trigger Instant / At Age / On Collision / On Death; Rate / Burst / Pulse; up to 8 sub-layers (fireworks).
- **nxFluid2D** — realtime 2D dye fluid in a mesh's UV map → texture / vertex group (needs UVs).
- **nxScatter** (Presets) — points over meshes. **nxFalloff Modifier** (reshape/blur falloffs; new Wet, Curvature, AO modes). **Vertex Maps** — write falloffs to attributes/vertex groups.
- **nxQuestion** additions: Asleep/Bound flags, Sleep/Bind actions; **Quill** layer (Blender). **Mapping**: one layer → several destinations. **nxSpeed** layer is now Acceleration (exponential). **nxGenerator** "Spawn" renamed Bias.
- **C4D ↔ Blender scene import/export** (Beta 3, Blender side): meshes+UVs, curves (first spline), cameras, lights, NeXus settings & gradients, materials (Cycles 4D → shader nodes); not animation keys, per-face materials, layered lists, bezier handles.

## Version history (short)
- 2026.0.0 (13 Jul 2026) first Blender release · 2026.0.1 (16 Jul) HUD counts, nxGenerator motion blur · 2026.1 Beta 1 (1 Oct) NeXus in C4D beta + nxMPM etc. · Beta 2 (7 Oct) nxOcean, nxShatter, nxWarp; **PBD strengths no longer depend on particle size** (old scenes look different) · Beta 3 (30 Oct) nxSpawn, nxFluid2D, nxScatter, nxSystem, Alembic/PLY cache, C4D interchange.
