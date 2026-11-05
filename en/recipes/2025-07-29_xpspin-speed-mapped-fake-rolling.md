# Fake rolling of non-spherical particles (xpSpin random spin mapped to Speed)

- Source: Top Tip Tuesday — Particle Spinning — https://www.youtube.com/watch?v=rzvJhmq1jbE (2025-07-29)
- Host / generation: NeXus collisions sim + **CPU xpSpin** modifier + Redshift object instancing
- Goal: skulls/boxes driven by a sphere-collision sim appear to tumble when moving, stop when at rest.

## Steps
1. Emitters ▸ **Extended Data ▸ Use Rotation** + random rotation at birth (orientation variety, no spin).
2. Emitter **Simple Spin** spins forever, even at rest — avoid.
3. **xpSpin** (Modifiers ▸ Motion) ▸ **Randomize Spin**, unidirectional off (±), ~5° per axis.
4. Mapping ▸ Random Spin ← **Speed**: 0 below ~5–8 cm/s, full at 15 cm/s → rest = no spin.
5. Redshift Object tag on the emitters instances custom geometry; it now tumbles.

## Gotchas
Collisions stay spherical → corners of boxy shapes intersect slightly.

## Newest equivalent
**nxSpin ▸ Roll** mode (see "Rolling particles nxSpin Roll", 2026) does real rolling; for true rigid bodies see "Particle Rigid Bodies" or the next beta's unified rigid bodies.
