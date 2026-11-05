# Soot deposits on walls from nxExplosiaFX smoke (xpVertexMap + Redshift)

- Source: Top Tip Tuesday — Soot Damage — https://www.youtube.com/watch?v=kGTKDlTTyxE (2026-04-07)
- Host / generation: C4D, nxExplosiaFX + **xpVertexMap** (CPU utility) + Redshift
- Goal: after the smoke clears, the wall it touched stays blackened.

## Steps
1. Wall (cube) is an nxExplosiaFX **collider** so smoke rolls up it. [▶ 0:24](https://youtu.be/kGTKDlTTyxE?t=24)
2. **xpVertexMap** (X-Particles ▸ Utilities), Object = wall → a vertex map tag appears. [▶ 1:41](https://youtu.be/kGTKDlTTyxE?t=101)
3. Change the default Polygon layer's **Layer Mode → ExplosiaFX**, link the EFX object, Channel **Smoke**, range 0–10. (With Blend Normal the map just mirrors current smoke and fades.) [▶ 2:15](https://youtu.be/kGTKDlTTyxE?t=135)
4. Accumulate: layer **Blend → Screen** (or Add) and lower **Strength** (~8–23%, settled at 14%) so it builds up gradually without covering everything. [▶ 3:22](https://youtu.be/kGTKDlTTyxE?t=202)
5. Material: existing brick material's final Standard node → **Material Blender** base; duplicate a Standard as soot (black, full roughness) → Layer 1. **Vertex Attribute** node (drag the map in) → **Ramp** (crush the white knot to taste) → Blend Color. [▶ 6:30](https://youtu.be/kGTKDlTTyxE?t=390)

## Newest equivalent
NeXus 2026.1: nxFalloff **Wet** / memory layers (Grow, Decay) and nxFalloffMap can build accumulating GPU vertex maps; EFX source weighting by vertex map is shown in the "NeXus Falloffs" recipe.
