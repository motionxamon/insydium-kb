# Rippling field of clones: nxTurbulence "Direction" mode + nxSpin Tangential + nxLimit

- Source: Top Tip Tuesday — Turbulence Direction — https://www.youtube.com/watch?v=HUTvETBii0k (2026-01-20)
- Host / generation: NeXus (Fused 2025.4+: Direction mode, layered modifiers, GPU falloffs) + xpGenerator Multi-Instance
- Goal: 40 k thin pillars on a plane that sway like seaweed/fur without moving position.

## Instance object
Cube X/Z 5 cm, tall → make editable → **Axis Center** Y −100 (pivot at the base) → enable Axis mode, rotate so the **Z axis points up** (90°, Shift snaps 5°).

## Stack (order matters)
1. **nxSpin** (top): layer **Tangential**, axis Z → particles point along their velocity/direction.
2. **nxTurbulence**: mode **Direction** (instead of Acceleration) → noise rotates particles, doesn't move them. Layer **Curl**, larger Scale, lower Frequency; Octaves ↑ with **Persistence ↓** → keep big swirls + some fine detail.
3. **nxLimit** (last): layer **Rotation**, Relative; limit **Pitch** +90 / −90 (no tipping below the plane; ±45 keeps them from lying flat), heading free; add variation.
4. **xpGenerator** Multi-Instance with the pillar as child; emitter radius variation → size variety.

## Interactive wave
nxTurbulence Falloff tab: **Sphere** falloff; animate it across the field → ripple passes through. Raise the falloff spline's low end to ~0.5 → slight motion everywhere, full effect inside.
