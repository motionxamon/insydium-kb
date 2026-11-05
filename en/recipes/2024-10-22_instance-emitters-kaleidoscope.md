# Clone and mirror emitters for a kaleidoscope (xpEmitter Instance mode + MoGraph Cloner)

- Source: Top Tip Tuesday — Cloning Particle Emitters — https://www.youtube.com/watch?v=tantnHiZWE4 (2024-10-22)
- Host / generation: C4D; X-Particles emitter **Instance** shape + NeXus nxTurbulence / nxSpeed
- Goal: one sim, many mirrored radial copies.

## Steps
1. Base emitter: rectangle 30×0, rate 2000, life 60, speed 50; Display dots, Gradient by **Direction (bank)**.
2. **nxTurbulence** strength 15 with **Y axis scale 0** (flat motion).
3. Putting the base emitter in a Cloner clones the shape only, not particles.
4. New emitter ▸ Shape **Instance** → base emitter; hide base. This instance emitter **does** clone.
5. Mirror: C4D **Instance** object of the instance emitter, scale X **−1**, same position; group both (Alt+G).
6. **Cloner Radial**, count 11, null as child → kaleidoscope.
7. Variants: turbulence Voronoi, more octaves, low persistence; **nxSpeed** (no acceleration) **max 50** with very strong turbulence → slow evolving patterns.
