# Big swirls plus fine detail (nxTurbulence Voronoi, Octaves, Persistence, Lacunarity)

- Source: Top Tip Tuesday — nxTurbulence Octaves — https://www.youtube.com/watch?v=_q9xeElfTfI (2023-09-26)
- Host / generation: C4D; G2 NeXus inside X-Particles (nxTurbulence — not the same controls as CPU xpTurbulence)
- Goal: keep large curling motion from the base noise while adding animated fine detail from higher octaves.

## Base
Two emitters: short-lived particles colored by direction (2D readout of the noise) and a thin emitter showing the 3D motion.

## Steps
1. Noise type **Simplex → Voronoi** → big swirls. Scaling the noise down gives flame-like fine detail but loses the swirls. [▶ 3:12](https://youtu.be/_q9xeElfTfI?t=192)
2. Scale back to **100**; **Octaves 1 → 10**. [▶ 3:38](https://youtu.be/_q9xeElfTfI?t=218)
3. **Persistence** (default 100% = equal strength in every octave): lower it so the first octave dominates; raise it again just enough to keep some fine detail. [▶ 3:04](https://youtu.be/_q9xeElfTfI?t=184)
4. **Frequency** (100) animates the noise; 0 = static. [▶ 3:38](https://youtu.be/_q9xeElfTfI?t=218)
5. **Lacunarity**: at 0 only the first octave animates (higher octaves frozen). Raise to **~2.3** → all octaves animate; slightly less keeps the big curls calmer. [▶ 3:31](https://youtu.be/_q9xeElfTfI?t=211)

## Newest equivalent
Fused 2025.4 makes nxTurbulence **layered** (stack noise layers instead of tuning one); see recipe 2026-01-20 for its Direction mode.
