# Clone and mirror emitters for a kaleidoscope (xpEmitter Instance mode + MoGraph Cloner)

- Source: Top Tip Tuesday — Cloning Particle Emitters — https://www.youtube.com/watch?v=tantnHiZWE4 (2024-10-22)
- Host / generation: C4D; X-Particles emitter **Instance** shape + NeXus nxTurbulence / nxSpeed
- Goal: one sim, many mirrored radial copies.

## Steps
1. Base emitter: rectangle 30×0, rate 2000, life 60, speed 50; Display dots, Gradient by **Direction (bank)**. [▶ 0:45](https://youtu.be/tantnHiZWE4?t=45)
2. **nxTurbulence** strength 15 with **Y axis scale 0** (flat motion). [▶ 4:28](https://youtu.be/tantnHiZWE4?t=268)
3. Putting the base emitter in a Cloner clones the shape only, not particles. [▶ 2:13](https://youtu.be/tantnHiZWE4?t=133)
4. New emitter ▸ Shape **Instance** → base emitter; hide base. This instance emitter **does** clone. [▶ 2:10](https://youtu.be/tantnHiZWE4?t=130)
5. Mirror: C4D **Instance** object of the instance emitter, scale X **−1**, same position; group both (Alt+G). [▶ 4:28](https://youtu.be/tantnHiZWE4?t=268)
6. **Cloner Radial**, count 11, null as child → kaleidoscope. [▶ 1:53](https://youtu.be/tantnHiZWE4?t=113)
7. Variants: turbulence Voronoi, more octaves, low persistence; **nxSpeed** (no acceleration) **max 50** with very strong turbulence → slow evolving patterns. [▶ 6:44](https://youtu.be/tantnHiZWE4?t=404)
