# Kill particles by distance traveled (nxQuestion age reset + Set Life)

- Source: Top Tip Tuesday — Custom Lifespan — https://www.youtube.com/watch?v=Lh_UZhFHCQ8 (2026-02-24)
- Host / generation: NeXus (nxQuestion, nxTurbulence layers, nxColor by speed) — C4D & Blender
- Goal: turbulent streams that thin out naturally — slow particles linger, fast ones die sooner.

## Options
1. Simple: emitter Full Lifespan off, Lifespan ≈ 174 F + variation.
2. Better: keep Full Lifespan, place **nxQuestion after nxColor**:
   ```
   If Traveled > 650–750 cm (± variation)
     Action Set Color yellow (debug, remove later)
     Action Set Age = 0  [Set Once]
        └─ Action Set Life = 30 F (±20)
   ```
   Without the **age reset**, a particle already 300 frames old dies instantly when given a 30-frame life. **Set Once** on the age action lets the age count up again.

## Why
Lifespan tied to distance → slow particles live longer, giving organic decay of noisy streams.
