# Layered curl turbulence tendrils (nxTurbulence Curl + FBM + Voronoi layers, per-layer age mapping, nxSpeed clamp, nxScale fade-in)

- Source: NeXus for Blender Quick Guide — Turbulence Layers — https://www.youtube.com/watch?v=U937aVtRzMA (2026-07-06)
- Host / generation: Blender (NeXus for Blender, G3): nxEmitter, nxTurbulence (layers), nxColor, nxSpeed, nxScale
- Goal: high-count additive particle curls from a thin ring, all driven by a single layered nxTurbulence.

## Base
- Emitter **Disc ▸ Edge Only** (thin emission line is key), pointing up; **100,000/s** (≈5× for render); lifespan 170 ±30.
- **nxColor**: Gradient by Speed, gradient preset **Magma**.
- **nxSpeed**: default layer is incremental (+1.5 m/s per s) → set increment **0**, clamp **max speed ~1** so turbulence strength can go very high without runaway acceleration.

## Steps
1. **nxTurbulence**: delete default Voronoi, add **Curl** layer; strength way up, **scale ~600**, **frequency ~10%** (lower = slower animation, less jitter).
2. Curl **Blend vs Add**: disable Add; Blend slider mixes emitter velocity (left) with pure curl (right) — ~**0.38**, then raise strength.
3. Stepping between frames (identical speeds) → document **substeps 4** (default 1).
4. Display particle size 1 for detail (2 in the video for compression).
5. Add **FBM** layer **above** curl (layers stack top-down like Photoshop). Very low frequency → vein-like tendrils; strength ~10. Keep blend mode **Normal** and mix with the **layer strength** slider instead (blend modes multiply velocities and explode).
6. Add a **Voronoi** layer on top for mid-scale motion: larger scale, low layer strength, slightly higher frequency.
7. Per-layer mapping: Mapping ▸ **Age** → choose the layer (Curl / FBM / Voronoi) and parameter **Strength**; range **5→15 frames**, curve full→low, end knot raised so some FBM remains (stops edge fuzz while keeping character).
8. Optional: Curl **Axis Direction Scale Z = 0** → flat thin tendrils that later bloom; **0.5** = restrained, languid 3D curls.
9. Fade in the emission edge: display **Circles Filled** (Points ignore radius); **nxScale ▸ Range**: radius start 0 → end ~0.001 (0.01 for viewport tests), over 8 frames with 50% variation; longer (e.g. 25 frames) = softer feathering. Skip when the emission shape (logo/text) should read crisply.

## Variations
- Emit from an object's **vertices** → free tendrils (no constraints); from **edges** → wireframe-like curls; curves/text work too.

## Newest equivalent
2026.1 beta adds per-layer Falloff lists on every modifier, **nxWarp** (Helix/Path/Flow) for guided streams, and an **nxFalloff Modifier** for remapping; the layered-turbulence approach itself is current.
