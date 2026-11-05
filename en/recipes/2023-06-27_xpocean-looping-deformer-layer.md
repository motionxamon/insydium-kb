# Large looping ocean without visible tiling (xpOcean Looping + second xpOcean as Deformer)

- Source: Top Tip Tuesday — Looping Ocean — https://www.youtube.com/watch?v=xQFbyD2fMNo (2023-06-27)
- Host / generation: C4D; G1 CPU X-Particles (xpOcean generator)
- Goal: a big gale-swell ocean that loops seamlessly over 180 frames and doesn't look repetitive when scaled up.

## Steps
1. X-Particles ▸ Generators ▸ **xpOcean**. Width / Height segments **200** each for detail.
2. Settings: **Wind Speed** way up (gale swell), Wave Height up a little, **Time Scale** down (slower motion).
3. Underlying Tessendorf noise **Resolution 256** (512 more detail but slow playback).
4. **Choppiness**: raise until the crests just start to fold, then stop (too much breaks the mesh).
5. **Damping 0** = water sloshes back and forth like in a closed tank; **full** damping = strong current along **Wind Direction** (+Z by default; change direction to steer). Settle on partial damping for a current with some reflections.
6. Loop: enable **Looping**, **Loop Time = last frame + 1** (**181** for a 180-frame scene).
7. Anti-tiling: duplicate the ocean, disable the original. On the copy: Resolution **128**, raise **Smallest Wave** (smooth), hugely increase **Ocean Size**, more wave height, a bit of choppiness; tweak wind speed / time scale.
8. Copy ▸ Type Primitive → **Deformer**; re-enable the original and make the deformer ocean its child → large-scale secondary motion breaks up repetition. Stack more deformer oceans if needed.

## Newest equivalent
**nxOcean** (NeXus 2026.1 beta, GPU): Phillips / Pierson-Moskowitz / JONSWAP spectra, foam, spray, wakes, shorelines and beaches, FLIP coupling. Stable Fused 2025.4 has no GPU ocean (nxWave in FLIP for interaction); xpOcean as shown remains the fallback. See "Custom object ocean" (2025-04-08).
