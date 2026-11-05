# Particle-driven laser rays inside a sphere (mtRayline + nxConstraints Forces + xpTrail)

- Source: Top Tip Tuesday — Rayline Particles — https://www.youtube.com/watch?v=t-gWrfo_NRk (2024-04-23)
- Host / generation: C4D; NeXus GPU (nxTurbulence, nxConstraints) on an xpEmitter + MeshTools **mtRayline** + CPU xpTrail
- Goal: every particle fires a ray that stops on a sphere; contact points birth short curved trails.

## Base
Sphere (display tag Lines/isoparms to see inside). xpEmitter **Rectangle**, height 1 cm (long thin strip), **Shot 1000**, speed 0. **nxTurbulence Curl**: scale 70, frequency 10, additive velocity off.

## Steps
1. **mtRayline**: Shape → **X-Particles**, drag in the emitter; Point Count **Custom (10) → All Points**.
2. Emitter **Extended Data ▸ Rotation: Tangential** — otherwise all rays point +Z.
3. Rayline: add the sphere as a **collider**, raise Ray Length so rays always reach it, enable **Single Shot** (stop at first contact, no reflections).
4. Keep the particles in strips: **nxConstraints ▸ Forces** layer, repulsion off; attraction up to 30 neighbours within 35 cm (later larger), min distance 5 → **0**, falloff **Flat**, attraction strength high → long tendrils that split and rejoin.
5. Calm the frantic swirling: lower the tangential rotation **rate of change** on the emitter.
6. Rayline ▸ Points ▸ **Contact Points ▸ add emitter** (the green contact dots become particles).
7. **xpTrail** on that new emitter: length 10 frames, var 5. Trail spline → **B-spline, Natural** intermediate points for smooth curves.
8. Hide emitters; render with an additive material.

## Newest equivalent
nxTrail (NeXus 2026) for the contact-point trails; the source particles/constraints work the same with an nxEmitter. mtRayline remains the ray tool.
