# Liquid countdown: fluid flowing along animated number splines (xpFlowField + nxFoam)

- Source: Top Tip Tuesday — Liquid Countdown — https://www.youtube.com/watch?v=C_fXmAUTb2Q (2025-10-28)
- Host / generation: C4D, NeXus fluids/foam + CPU **xpFlowField** + MeshTools **mtSplineSample**
- Goal: water in a box that swirls into 5-4-3-2-1 shapes.

## Steps
1. Container cube with **xpCollider Normals: Inside**. Box emitter same footprint, **Shot – Regular**, radius 3, full life. nxGravity; **nxFluids SPH** substeps 4, viscosity 4. [▶ 0:56](https://youtu.be/C_fXmAUTb2Q?t=56)
2. Text spline with keyframed numbers → resample evenly: **mtSplineSample** (child = text), Close, mode **Distance**, plus smoothing → even point spacing = even flow vectors. [▶ 3:00](https://youtu.be/C_fXmAUTb2Q?t=180)
3. **xpFlowField** sized to the container:
   - Layer **Along Spline** (link the spline-sample) → vectors along the outlines.
   - Layer **To Spline** (attract to outlines) on top with reduced strength (Normal blend) → mix.
   - Affect: **Velocity**, speed ~160 (Direction-only or Acceleration also possible). Optional turbulence layer/modifier for chaos.
4. **Cache** the fluid (170 frames, quick), then disable flow field, spline sample and fluids (keep emitter + gravity — foam needs gravity). [▶ 7:12](https://youtu.be/C_fXmAUTb2Q?t=432)
5. **nxFoam** → **Add Emitter** (Dots display); keep only **Crest** layer (remove Aerate/bubbles), lower crest rate, **After Age 7**, life ~70 → fine detail on the cached fluid. [▶ 7:38](https://youtu.be/C_fXmAUTb2Q?t=458)

## Newest equivalent
2026.1 beta has GPU **nxFlowField** (Blender/NeXus 2026) and **nxWarp Path/Flow** for steering particles along shapes.
