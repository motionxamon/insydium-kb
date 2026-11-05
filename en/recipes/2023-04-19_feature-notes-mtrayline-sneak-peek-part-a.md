# Feature notes: mtRayline sneak peek (MeshTools raycast spline generator)

- Source: INSYDIUM LIVE! — April 2023 - X-Particles, NeXus & MeshTools — https://www.youtube.com/watch?v=U8zISIlBq90 (2023-04-19)
- Host / generation: C4D; MeshTools (pre-release preview; shipped in Fused 2023.3)
- Goal: what the then-upcoming **mtRayline** does and its main controls.

## What it does
Casts rays from a source and turns them into a **spline object** (Make Editable → plain spline) that bounces off collider geometry — usable for render splines, sweeps, laser/scanner/FUI looks. Fully live: animated colliders or an animated Rayline update the rays.

## Key parameters
- **Colliders**: layer list, any number of objects; rays reflect on contact, and a source **inside** a closed volume fills it with bounces.
- **Rays**: Count (e.g. 40), **Length** (+ variation), **Angle** (+ variation), one **Seed** for both variations.
- **Single Shot**: stop at the first hit, no reflections → scan-line look when the object rotates.
- **Shape**: Center (default), **Circle** (radial ring, Spread), **Line** (laser-beam rows), **Custom Object** (rays from its points; Point Count by ray count or **All Points**), **X-Particles** (emitter link or Add button; rays follow particles, and particles with an xpCollider tag bounce where the rays do).
- Display: Gradient (viewport only) or single color; **Spline** type options (e.g. **B-Spline** for curvy bounces); **Growth** to animate the rays on.
- **Points** tab: objects or particles at **Start**, **End** and **Contact** points (e.g. cubes, toruses, spheres), with a **Tangential** option to align them along the ray.

## Replaces / relates to
New tool, no older equivalent; previously faked with xpTrail or hand-built splines. Today still the ray tool in Fused — see recipes "Rayline Particles" (2024-04-23) and the Redshift additive-curves recipe (2025-06-03).
