# Endless river / fluid stream (open-sided container + refill emitter + nxKill)

- Source: Top Tip Tuesday — Fluid Streams — https://www.youtube.com/watch?v=q8Crdpa1XUw (2025-07-08)
- Host / generation: NeXus nxFluids SPH, nxGravity, nxKill + xpCollider
- Goal: constant one-direction flow over rocks, with glowing tracer particles.

## Steps
1. Cube "fluid container" a bit larger than the rocks; duplicate as "fluid kill" (slightly bigger, hidden).
2. Container: **xpCollider** bounce/friction 0, Normals **Inside**; make editable and **delete the exit face**.
3. Base emitter: box ≈ container footprint, 35 cm tall at the bottom; **Shot, Hexagonal**, speed 0, radius 3.
4. **nxGravity 300**, **nxFluids SPH** substeps 4. **Tilt the gravity** toward +Z to push the flow.
5. **nxKill ▸ Object**: kill outside "fluid kill" volume → escaped particles stop costing time.
6. Refill: thin wide box emitter at the far end, Hexagonal continuous, spacing **200%**, speed 0; widen it if the level drops.
7. Display: Gradient by Parameter ← Speed (auto) for a readable preview.
8. Glow tracers: third emitter from a join of spheres placed around the rocks, Shot Hex at frame 6, white — they ride the currents.

## Gotchas
SPH needs **every emitter at exactly the same radius**.

## Newest equivalent
FLIP/APIC (Fused 2025.4) for large rivers; 2026.1 beta **nxOcean** for open water.
