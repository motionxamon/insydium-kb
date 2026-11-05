# Soft-serve ice cream swirl (nxFluids APIC, viscosity, gravity mapped by age)

- Source: Top Tip Tuesday — FLIP Ice Cream — https://www.youtube.com/watch?v=ooB36pUD8Ys (2026-03-03)
- Host / generation: C4D, Fused 2025.4+ (nxFluids FLIP/APIC, nxMesher)
- Goal: a ridged, coiling viscous swirl that holds its shape.

## Emission (shape from splines)
- Emit from a **Star spline** attached to a Circle with Align to Spline; star position animated around the circle, the circle moves down and shrinks, the star shrinks at the end → the tip.
- Rate 1000/frame (2000 for final), speed 0.

## Sim
1. **nxFluids APIC** (bounded domain 200³), **Voxel Size 4** (default too coarse), **Viscosity ~300**. **nxGravity** defaults.
2. Stepping from a thin source with no initial speed → Project Settings (Ctrl+D) ▸ X-Particles **Subframe Steps 5** (8 for final).
3. Stop the swirl from sinking/melting: nxGravity **Mapping** → **Age** → Gravity Strength, range **40–50 F**, curve full → 0 (gravity switches off once a ridge has landed; only pushes from above move it).
4. Final quality: Solver Accuracy → **Viscosity accuracy full**, fluid **Min/Max Substeps 3/5** (separate from scene subframes). Cache ≈ 8 min.

## Meshing (nxMesher)
- Radius ~1.8, **Polygon Size 1**. For tight folds use **Spheres** (Zhu-Bridson smooths away sharp folds) + **Smoothing layer Mean Curvature** (or Laplacian) full strength, **7 iterations**.

## Gotcha
Spline emission = hollow shell; fine from a camera that doesn't see inside, otherwise fill a solid volume with many more particles.
