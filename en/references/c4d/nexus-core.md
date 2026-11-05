# NeXus (C4D) — core concepts, nxConstraints, nxFluids, nxExplosiaFX, nxMesher

Source: docs.insydium.ltd/nexus/ (Fused 2025, checked 2026-11-03). Paraphrased notes, not a copy of the docs.

## What NeXus is
- GPU particle/simulation layer **inside X-Particles** (Vulkan, "Theron" engine). Not a separate system object: you still use **xpSystem → xpEmitter**.
- **How GPU mode switches on:** put a NeXus object (any `nx*` modifier or solver) as a **child of / affecting an xpEmitter**. The xpEmitter icon turns **blue → orange** = that emitter is now simulated on the GPU. No checkbox.
- Only `nx*` objects run on GPU; classic `xp*` modifiers run on CPU. Both can live in one scene (e.g. nxPush + xpFlowField), each on its own processor — but mixing CPU modifiers on a GPU emitter costs transfer time; prefer staying all-`nx` on a given emitter.
- Biggest wins: millions of particles, fluids. nxPush / nxBlend are much faster than xpPush/xpBlend.
- Multiple GPUs: choose device in **C4D Preferences → NeXus**.
- Common tabs on every nx object: **Groups Affected** (drop xpGroup objects; empty = all), **Mapping** (drive any parameter by particle data — see mapping), **Fields/Falloff** (limit where it acts; nxFalloff).

## nxConstraints (particle–particle physics, layer stack)
Global settings:
- **Iterations** (start ~3): accuracy; with Connections also makes springs stiffer when Stiffness is maxed.
- **Damping**: calms the solve so you can raise Iterations.
- **Add Constraint** → layers: Connections (Birth / Distance / Custom), Collisions, Forces, Viscosity, Friction, Surface Tension. Each layer toggled green/red — disable layers to isolate behaviour.
- Every layer has **Weight** (100% default). With several layers you may need >100% on the one you want to dominate.

Layers:
- **Collisions** — Weight, Stiffness (low = soft/bouncy). Fix repeated bouncing by adding a Friction layer with Connection Limit 1.
- **Connections → Birth** — springs made once at birth. Only Born, Connection Limit (2–12), Radius, Stiffness, Minimum Distance (avoid clumping), Break + Break Type: None / Relative Connected (% of birth length, default) / Relative Radius / Absolute. Show links: xpEmitter → Display → Enable Display Constraints. Use: soft bodies, jelly, tearing (lower break).
- **Connections → Distance** — springs form any time particles come within Radius; Break as % of length at connection time (e.g. 160%). Use: gooey networks that stick on contact.
- **Connections → Custom** — see notes below (rules-based).
- **Forces** — Attraction (Radius, Inner = no-collapse zone, Falloff Flat/Linear/Quadratic/Cubic, default Cubic) + Repulsion (own Radius, Falloff). Connection Limit. Use: clumping/cohesion, spacing.
- **Viscosity / Friction / Surface Tension** — see below.

## nxFluids (liquid & granular)
Three solvers:
| Solver | Use for | Notes |
|---|---|---|
| **PBD** | small–mid, fast, stylised; plays well with nxConstraints/modifiers | Substeps 3, density iter Min 1/Max 10, Attraction 10% < Repulsion 20%, Ext Pressure 10% (cohesion). High Attraction without Repulsion breaks liquid. |
| **SPH** | mid–large realistic liquid; **Granular** mode (sand/snow) | Fluid Type Liquid/Granular, Smoothing Radius 100%, Substeps 3 (granular may need up to 30), Min/Max density 3/7, Velocity Correction (natural flow, slower), Viscosity + Viscosity Iter, Vorticity Small/Large, Surface Tension (beading), Internal Pressure 100% (volume), External Pressure 30% (cohesion). Granular: Friction, Friction Iterations, Stability (break-free speed), Cohesion. |
| **FLIP / APIC** | large, detailed, grid-based | Voxel Size, Domain Size, Retiming, FLIP fraction (100% energetic/noisy, lower = calmer PIC), Viscosity, Vorticity, Surface Tension, Weak Particle Repulsion (anti-clumping). Walls per face: Closed/Open/Kill. Accuracy: Pressure/Viscosity accuracy+iterations, CFL, Min/Max substeps. APIC = more swirl, no FLIP fraction. |
- **Check Density** (PBD/SPH, off by default): deletes over-dense new particles — stops "blasting" at emission, but silently removes particles.
- Viscosity is also affected by X-Particles Project Settings → **Subframe Steps**.
- **Multi-fluid:** add an **nxFluids tag** to each emitter (INSYDIUM Tags / Extensions) — per-emitter Density, Viscosity, Surface Tension, Friction, Fluid Type (e.g. Grains), PBD Viscosity/Ext Pressure/Vorticity. PBD tab only works when the nxFluids object is set to PBD. Use: water + sand, oil + water.
- Mesh result with **nxMesher**.

## nxExplosiaFX (GPU smoke & fire)
- Sources tab: meshes (Emit From Surface/Volume), emitters, splines. Per channel (Smoke, Temperature, Fuel, Pressure): Mode Set/Blend/Add/Sub, Weight by Tag/Texture/Noise; Frame Limit start/end on Fuel & Pressure (no keyframes needed). Motion Gap Fill for fast sources. Velocity from Object Motion/Normal/Custom; Color from Object/Shader.
- Simulation: Domain Size, **Voxel Size** (main detail/speed knob), **Upscaling** (adds detail keeping shape — heavy VRAM, check Memory Stats), Retiming; Burning (Burn Rate, Temperature/Smoke Production, Gas Expansion = explosiveness, Ignition Temperature); Diffusion; Dissipation; Buoyancy (negative smoke buoyancy = sinking smoke).
- Solver: channels (enable Color here + in Display to see colored smoke), pressure/diffusion accuracy, Advection CFL + substeps, **Adaptive Bounds** (keep ON), boundary walls.
- Dynamics: built-in Turbulence/Vorticity/Wind layers with mapping; Modifiers subtab accepts nxDirection, nxAttract etc.; **Particle Advection** — emitter particles ride the smoke velocity field (great for embers/dust).
- Colliders: Objects, Add Pressure (negative attracts), Velocity State.
- Display: Ray Marching (default) or Slicing; Smoke Extinction/Tint/Albedo; Flame Blackbody. Velocity field/trails display = memory-heavy.
- Gotcha: Fuel off + Smoke on with fire-style setup → nothing visible. Mesh it via nxMesher (smoke/temperature iso).

## nxMesher (GPU particle → polygon)
- Layers: drag emitters and/or nxExplosiaFX in; optional Smoothing modifier per layer (Gaussian / Laplacian = keeps volume / Mean Curvature = removes noise; Strength, Influence Range, Iterations).
- General: **Polygon Size** (resolution), Surface Size Custom (Radius) or Source (particle radius × Scale), **Surface Type**: Spheres (fastest, blobby) / **Zhu-Bridson** (smooth liquid) / Anisotropic (stretch by speed: Eccentricity, Max Speed). Tris or Quads.
- Export Tags: particle Color → vertex color tag; Velocity → UV tag (for motion blur/shading).
- Domain: Adaptive (default on) or fixed size; particles outside are not meshed.
- Tip: big Polygon Size for previews, small for final.
