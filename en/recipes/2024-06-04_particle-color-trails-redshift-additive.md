# Per-vertex colored trails rendered additively in Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)

- Source: Top Tip Tuesday — Particle Color Trails — https://www.youtube.com/watch?v=gXGQ4H_MS5k (2024-06-04)
- Host / generation: C4D; xpEmitter + xpStrangeAttractors + xpTrail (CPU) + nxTurbulence, nxColor (GPU); Redshift
- Goal: Lorenz-attractor trails whose color paints in over time, rendered as glowing additive curves.

## Sim
1. xpEmitter **Rectangle** width 0 (thin, tall), Rate for 120 F, 300/s. xpTrail default.
2. **xpStrangeAttractors** (Lorenz default): clamp **max speed ~105**, strength **28%** so other forces can act.
3. **nxTurbulence** Voronoi, strength 28, **scale 450**.

## Color
4. **nxColor ▸ Time Dependent** layer: over **75 F**, reverse after; load the black-violet preset, delete the black knot, redistribute.
5. Set every knot's value (brightness) to **50%** — looks dull in viewport but keeps additive brightness consistent.

## Render
6. **Redshift Object tag on the xpTrail ▸ Curves: Boxes**, thinner thickness.
7. Redshift Standard Material: base/reflection/transmission/coat 0, **Emission 2**.
8. **Vertex Attribute** node, preset **Curves ▸ Curve Color** → **Geometry Opacity**.
9. xpTrail ▸ Thickness & Color ▸ **Trail Color Mode: Per Vertex** (Particle Color colors the whole trail with the current color).
10. Redshift Camera ▸ Lens Effects ▸ **Bloom** override: threshold 1, intensity 400.

## Gotchas
- Trail color isn't visible in the viewport; check in the render view.

## Newest equivalent
NeXus 2026 **nxTrail** on nxEmitter for the trail side; xpStrangeAttractors has no nx counterpart listed.
