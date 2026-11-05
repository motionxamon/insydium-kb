# Hide a hard emission ring with a noisy opacity mask (nxColor layers + birth-rate spline)

- Source: Top Tip Tuesday — Noisy Particle Emission — https://www.youtube.com/watch?v=PyCCkH-nxfw (2025-07-22)
- Host / generation: NeXus (nxColor layers, nxTurbulence Boron/Curl-type noise) + Redshift additive particles
- Goal: organic swirls where the circular emitter edge no longer reads as a shape.

## Base
Circle emitter, Ring Only, cone 90°, rate 2000/F (50 000 in production), life 90, speed 100, radius 3; **nxTurbulence** in Boron noise mode; additive Redshift particle material (color → opacity).

## Steps
1. **nxColor** layer 1 — *Gradient by Parameter* black→white driven by a **Random field** (Luka noise, scale ~800, animation speed ~40) → animated B/W noise. [▶ 1:52](https://youtu.be/PyCCkH-nxfw?t=112)
2. Layer 2 (above) — same gradient mapped to **Age** (black at birth, white quickly), blend **Multiply** → born invisible, then the noise reveals them. [▶ 3:22](https://youtu.be/PyCCkH-nxfw?t=202)
3. Layer 3 (top) — copy of the age layer, blend **Add** → older particles fully white; slide the gradient knots to let more noise through. [▶ 4:15](https://youtu.be/PyCCkH-nxfw?t=255)
4. Color drives opacity in Redshift → noisy, ragged fade-in at the emitter. [▶ 8:03](https://youtu.be/PyCCkH-nxfw?t=483)
5. Emitter ▸ Emission ▸ **Birth Rate spline**: ramp 0 → full at the start (no "flower petal" burst). [▶ 5:39](https://youtu.be/PyCCkH-nxfw?t=339)
6. Lifespan variation ~25 frames → particles don't all die at once. [▶ 6:34](https://youtu.be/PyCCkH-nxfw?t=394)

## Newest equivalent
2026.1 beta: nxColor layered modifiers + 16 falloff modes give the same without fields; emission falloffs on nxEmitter.
