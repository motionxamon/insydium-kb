# Turbulent text reveal with particles (nxCover Edges + weak layer strength + Spring holding, nxColor by Direction)

- Source: Top Tip Tuesday — Particle Spline Reveal — https://www.youtube.com/watch?v=dL2bCkQf5HM (2024-05-21)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxCover — new in 2024.2, nxTurbulence, nxColor)
- Goal: a stream of particles swirls in and dusts the outline of the word "COVER".

## Steps
1. xpEmitter Rate, stop at 450 F, **4000/frame**, speed 50 (var 10). Set **width and height 0** → point emission for much finer, wispier detail.
2. **nxCover**: text spline, **Edges**; movement uses particle speed; **Hold Time 0** = held forever.
3. **nxTurbulence** Voronoi, strength 20 → only speed waves while nxCover dominates.
4. Lower the nxCover layer **strength to ~19%** so turbulence can swirl them before they settle.
5. **nxColor ▸ Gradient by Parameter** (blue–green preset) mapped to **Direction ▸ Heading** (better definition than Age).
6. Thicker letters: nxCover holding **Attract** (default, slows from 50 cm) → **Spring**, damping **15%**; increase **spring length** for a random dusting around the edges. More damping/stiffness = less wobble.

## Newest equivalent
nxCover still applies; 2026.1 adds per-layer falloff lists to localise the cover.
