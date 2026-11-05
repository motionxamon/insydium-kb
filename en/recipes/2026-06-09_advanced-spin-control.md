# Random birth orientation + repeatable 360° spins (nxSpin + age reset)

- Source: Top Tip Tuesday — Advanced Spin Control — https://www.youtube.com/watch?v=I98idMM1O80 (2026-06-09)
- Host / generation: NeXus (nxSpin layers, nxQuestion) + xpGenerator (soccer balls), C4D
- Goal: instanced balls start randomly oriented, then do exactly one full spin each time they pulse up in size.

## Setup
1. Particles pulse in radius via nxQuestion Wave (see "Sine Wave Action").
2. **nxSpin "Spin Birth"** (bottom): layer **Spin**, Spin Time **On Birth**, Heading variation 360°, small variation on P/B → random start orientation only.
3. **nxSpin "Spin Animation"**: layer **Range**, Orientation **Particle**, Start 0 → End 360° (heading), Start/End time 0–60 (or 68) frames; move the curve knot to delay the start. Add spin variation (50°) and time variation so balls don't stop together.
4. Make the range repeat: **nxQuestion** `If Radius < 36.5 → Set Age = 0`. While a particle is small its age is held at 0; once big the age counts and the Range spin plays once; next pulse resets it.
5. Find the threshold with **xpConsole** (Utilities): Data to display → Radius; double-click → min/max (here min big radius ≈ 36.4).

## Notes
- Separate nxSpin objects for birth orientation and for animation.
- Spin layer with Particle orientation + 0 amount / 360 variation = random speeds in both directions.
- The "reset age" trick works for any Range layer (nxScale, nxColor, nxSpeed) to make it loop on an event.
