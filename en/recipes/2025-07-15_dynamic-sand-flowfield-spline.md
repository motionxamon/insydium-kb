# Sand that piles into a spline shape (granular SPH + xpFlowField To-Spline layer)

- Source: Top Tip Tuesday — Dynamic Sand Simulation — https://www.youtube.com/watch?v=D8XcG_EuvG8 (2025-07-15)
- Host / generation: NeXus nxFluids **SPH Granular** + CPU **xpFlowField** + nxSpeed
- Goal: a logo/flower outline made of drifting sand ridges.

## Base
Floor plane 1000×1000 with xpCollider (bounce 0, friction 12). Circle emitter r 200, raised 1 cm, rate 1000 (25 000 for final), lifespan 100 ± 50, speed 0, radius 0.5.
- Ctrl+D: **simulate at 60 fps, render interpreted at 30** → half-speed playback. Re-check lifespan after changing fps (it rescales).

## Steps
1. **nxGravity 400**; **nxFluids ▸ SPH Granular**, substeps up, **Check Density** on (particles born overlapping), friction / stability / cohesion low (no clumping).
2. Flower spline 50/150 cm, lifted Y 12 cm.
3. **xpFlowField** sized around it: delete default Random layer → **To Spline** layer, cell size 10, mode **Velocity 300**, falloff off.
4. **nxSpeed**: Incremental +0, **Max speed ~65** (calms it).
5. Variation: flowfield Fields ▸ **Random field** scale 1000, anim speed 100%, Remapping Contour curve → hard on/off patches.
6. Shade with Redshift; for mask-based color see "Advanced Color Animation" (2025-08-19).

## Newest equivalent
Fused 2025.4/2026.1: **nxDirection** / nxFollowSpline-type flows and the GPU flow field in NeXus; 2026.1 beta **nxMPM** for sand and snow.
