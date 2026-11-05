# Clumping sand / snow with SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)

- Source: Top Tip Tuesday — NeXus Granular — https://www.youtube.com/watch?v=rkuNbceXolQ (2026-07-28)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxEmitter Hexagonal, nxFluids SPH Granular, nxCollider, nxGravity
- Goal: a Suzanne of grains that drops and cracks into lumps (dry sand → clumpy sand/snow).

## Steps
1. Big hidden plane + **nxCollider**: Bounce 0, Friction high (**80%**, up to 100 for clumping). **nxGravity** default. [▶ 0:57](https://youtu.be/rkuNbceXolQ?t=57)
2. Suzanne (Subdivision 2, applied), raised and rotated. **nxEmitter**: Object, **Volume**, **Shot**, **Hexagonal**, Speed 0. Display Spheres shows the true packing; radius **0.01 m** for more grains (production: 3–4 M+). [▶ 2:14](https://youtu.be/rkuNbceXolQ?t=134)
3. **nxFluids** ▸ **SPH** ▸ Fluid Type **Granular** → dry sand. Display Gradient by **Granular**, Auto Scale off, 0–20. [▶ 4:02](https://youtu.be/rkuNbceXolQ?t=242)
4. Substeps **6 → 12** and **Adaptive off** — the key setting for grains (fixed high substeps every step). [▶ 5:45](https://youtu.be/rkuNbceXolQ?t=345)
5. Friction **100%** → first clumps; **Friction Iterations 30** (50 for big lumps; slower). [▶ 9:25](https://youtu.be/rkuNbceXolQ?t=565)
6. **Stability** = relative-speed threshold above which grains break free of friction: lower = many small chunks, **60** = bigger chunks. [▶ 9:19](https://youtu.be/rkuNbceXolQ?t=559)
7. Emitter **Subframe Emit off** so all grains fall in sync and do not split mid-air. [▶ 7:47](https://youtu.be/rkuNbceXolQ?t=467)
8. **Cohesion** is a springy constraint — high values (50) look jelly-like; keep ≤ default **10** (5 tested). [▶ 9:51](https://youtu.be/rkuNbceXolQ?t=591)
9. Over-bouncy impacts: Smoothing Radius **120%** (slower); then raise display max to ~40. [▶ 11:24](https://youtu.be/rkuNbceXolQ?t=684)
10. Collider friction: low = grains spread out on landing; full = mass grips and stays as a lump. [▶ 13:12](https://youtu.be/rkuNbceXolQ?t=792)

## Newest equivalent
2026.1 beta **nxMPM** (snow, sand) / **nxMaterial** presets (Snow packed/sticky, Sand wet).
