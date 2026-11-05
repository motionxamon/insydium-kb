# Text disintegration / reveal (nxQuestion field → switch group → reset age → set lifespan)

- Source: Top Tip Tuesday — Particle Reveal — https://www.youtube.com/watch?v=bnaV15UoBRI (2024-12-17)
- Host / generation: NeXus (nxExplode, nxTurbulence, nxQuestion, groups, spherical field)
- Goal: particles peel off text as a growing field passes; play the cache reversed for a reveal.

## Steps
1. Emitter **Shot** on the text surface (text hidden).
2. **nxExplode** from the **modifier position** (not mass center), speed 150 ± 100, **Speed at Start Only off** (keeps pushing).
3. **nxTurbulence** below it: Boron noise, strength 25, more octaves, **lower persistence** (keeps big swirls + fine detail).
4. Emitter Groups: create 2 groups, mode **First Group Only** → all born in group 1. Both modifiers ▸ Groups Affected = **group 2**.
5. **nxQuestion**: `Field (spherical) → Set Group 2` → then **Set Age 0** (once) → **Set Lifespan 85**.
6. Animate the field size 0 → covers text (frames ~41 → 152).
7. Cache, then reverse playback for a forming reveal. Change text → new effect (fully procedural).

## Newest equivalent
2026.1 beta falloffs (16 modes) on modifiers can replace the field + group switch in simple cases.
