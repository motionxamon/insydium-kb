# Smooth fluid mesh that keeps thin tendrils (xpOpenVDBMesher Point Radius, Voxel Size, Curvature + Offset filters)

- Source: Top Tip Tuesday — nxFluids Detailed Meshes — https://www.youtube.com/watch?v=vbolWCL3KgY (2023-11-28)
- Host / generation: C4D; G2 nxFluids PBD sim meshed with **CPU xpOpenVDBMesher** (pre-nxMesher); Cycles 4D render
- Goal: slick, smooth liquid mesh without losing the fine tendril detail of the particle sim.

## Base
Spherical emitter, **Shot – Hexagonal**, speed 0, radius **1 cm**; **nxTurbulence** Voronoi strength **9**; **nxFluids PBD**, substeps **5**, External Pressure **100** (exaggerates tendrils), Attraction **40**, Repulsion **80**. Cached in ~17 s.

## Steps
1. **xpOpenVDBMesher**, General ▸ drag in the cached emitter. Default result is blobby: **Point Radius 10 = 10 × particle radius** shell.
2. Lower **Point Radius** to **~1.5**; reduce **Voxel Size to 1** so the small shells can be sampled.
3. Filters: the default **Median** smooths but more iterations eat thin bridges — removed.
4. Add a **Curvature** filter instead and raise iterations (~4): removes lumps while keeping volume.
5. Lost a little volume → Point Radius **1.5 → 1.7**, then smooth a bit more with Curvature.
6. Top filter **Offset** to shrink the surface back onto the particles; default is too strong, lower its strength until no mesh disappears.
7. Apply a random-walk SSS shader; render in Cycles 4D.

## Gotchas
- Small Point Radius without smaller voxels makes parts vanish.
- Filter order matters: Curvature for smoothing, Offset last to tighten.

## Newest equivalent
**nxMesher** (Fused 2025.4, GPU) — flicker-free with **layered smoothing**; 2026.1 adds **Detail Aware** smoothing, made exactly for keeping thin features.
