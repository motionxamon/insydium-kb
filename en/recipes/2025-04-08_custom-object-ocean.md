# Animated ocean surface inside any object (xpOcean Deformer + Boole Intersect, looping)

- Source: Top Tip Tuesday — Custom Object Ocean — https://www.youtube.com/watch?v=r_AyI7Bgi0U (2025-04-08)
- Host / generation: C4D; CPU X-Particles **xpOcean** (Generators) + C4D Boole; Standard material with Fresnel
- Goal: a "sea" filling a logo / 3D text (here a letter X), seamlessly looping.

## Base
Text object "X"; plane **250×250 cm, 300×300 segments** (denser = more wave detail, slower).

## Steps
1. **xpOcean** ▸ mode **Deformer** (not Primitive), child of the plane. [▶ 0:40](https://youtu.be/r_AyI7Bgi0U?t=40)
2. Look: **Wave Height 8**, **Ocean Size 250**, **Smallest Wave 0.1** (default 1 — lower pulls finer detail), wind speed slightly lowered, a little **Damping** (0 = waves just slosh back and forth, 1 = fully follow wind direction). [▶ 1:16](https://youtu.be/r_AyI7Bgi0U?t=76)
3. **Choppiness ≈ 1** — pinches crests/stretches troughs; too high folds the mesh. [▶ 2:59](https://youtu.be/r_AyI7Bgi0U?t=179)
4. Position the plane where the surface should cut the X. **Boole**: children text + plane, mode **Intersect**, **Remove Self Intersections off** (faster), **High Quality Normals on** (fixes shading errors). [▶ 4:10](https://youtu.be/r_AyI7Bgi0U?t=250)
5. Loop: xpOcean ▸ **Looping on**, Loop Time = last frame + 1 (**201** for a 200-frame scene). [▶ 5:38](https://youtu.be/r_AyI7Bgi0U?t=338)

## Gotchas
- Any choppiness folding breaks the Boole — the result vanishes on those frames. **Scrub the whole timeline** (it failed e.g. around F167 when too high) before baking/rendering.
- Boole regenerates every frame → slow playback; bake if needed.

## Newest equivalent
2026.1 beta **nxOcean** is the GPU ocean (spectra, foam, spray, shorelines, FLIP coupling), but whats-new lists no deformer mode on arbitrary meshes — for this logo trick CPU xpOcean in Deformer mode remains the documented route.
