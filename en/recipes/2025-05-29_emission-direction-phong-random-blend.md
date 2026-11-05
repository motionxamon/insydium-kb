# Emission direction from objects: Normal, Phong Normal and Random Blend (xpEmitter direction modes)

- Source: Bite-Sized — Emission Direction — https://www.youtube.com/watch?v=90Qk_MPNZbg (2025-05-29)
- Host / generation: C4D; xpEmitter (object emission settings, applies to CPU and orange GPU emitters)
- Goal: control whether particles stream straight off polygon normals, emit smoothly over low-poly geometry, or spread around the normal.

## Steps
1. **xpEmitter ▸ Object**: shape Object, link a primitive sphere. Default emission is from **Polygon Center** with direction **Normal** → one stream per polygon.
2. **Polygon Area** still follows each face normal → visible gaps between faceted directions.
3. For smooth emission from low-poly geometry: keep a **Phong tag** on the object and set direction to **Phong Normal**. Phong angle 0 = faceted again; raising the angle smooths both shading and emission.
4. Spread around the normal (demo on a plane, Polygon Center): direction must be **Normal**. Plain **Random** loses the streams entirely.
5. Twirl open the direction arrow to reveal the **Random Blend** curve. Delete one knot so it's a flat line; 0 = pure normal, small value = slight cone spread around each stream, **0.5 = 180° spread**, **1 = identical to Random**.

## Gotchas
- Random Blend only exists in Normal mode.
- Phong Normal depends on the Phong tag's angle, not on the mesh resolution.
