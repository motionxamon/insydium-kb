# Flower-burst trails with speed-mapped thickness and per-vertex color (nxTrail, nxScale + nxTurbulence speed mapping)

- Source: Top Tip Tuesday — Particle Trails — https://www.youtube.com/watch?v=I2ERiN8Vk2Q (2026-08-25)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxSpeed, nxTurbulence, nxColor, nxScale, nxTrail; Eevee
- Goal: particles burst out, curl and slow to a stop, leaving trails that taper and shift color along their length.

## Steps
1. **nxEmitter**: **Disc**, Edges only, Angle **90°**, **Shot** of 200 (2,000 for the final), Speed **2.5**, variation **1** (range 1.5–3.5 m/s).
2. **nxSpeed** ▸ default Incremental layer with a **negative** value (**−0.04**) + variation → gentle slow-down.
3. **nxTurbulence** ▸ Voronoi layer, mode **Direction** (steers, no added speed); raise strength (~49) and scale.
4. Turbulence ▸ **Mapping ▸ Speed map** → layer Voronoi Noise, parameter strength, range **0–3.5** → fast particles curl strongly, slow ones settle.
5. Display **Circles Filled**; radius 0.05.
6. **nxColor**: Magma gradient, parameter **Distance** travelled, max ~**5 m** (Speed 0–3.5 also works; reverse gradient for dark→light).
7. **nxTrail** ▸ emitter. Thickness tab ▸ Trail Color Mode **Per Vertex Color** (default Particle Color recolors the whole trail) → color is painted along the trail.
8. Thickness mode **Use Radius Variable** → trail width from particle radius.
9. Animate radius: emitter radius 0; **nxScale** layer **Set Value** 0.05, 60% variation, **Clamp to Radius Limit off**; Mapping ▸ Speed map → **Radius Value**, range 0–3.5; lift the curve's low end so slow particles keep some width → trails taper but never vanish.
10. Render: nxTrail Display **Lines → Splines** → auto Geometry Nodes (Curve to Mesh) + material with the **NeXus trail color attribute**; e.g. pipe it into Principled Emission color.

## Gotchas
- Lines mode is GPU viewport-only; only Splines renders (and is slower, CPU GN).
