# Kill stray foam outside an arbitrary container (nxKill + field Volume invert / nxQuestion Document Object Distance)

- Source: Top Tip Tuesday — nxKill Custom Bounds — https://www.youtube.com/watch?v=MRrkMcNyU-w (2023-10-31)
- Host / generation: C4D; G2 NeXus inside X-Particles (nxFluids SPH, nxFoam, nxKill, nxQuestion) + C4D fields
- Goal: remove foam particles that are born just outside a capsule-shaped collider (they look like leaks).

## Base
Capsule container; **nxFluids SPH** default; **nxGravity**; **nxWind** with a Vibrate tag on rotation; strong Voronoi **nxTurbulence**. Cached (600 F in ~30 s).

## Steps
1. **nxFoam** on the cache ▸ **Add Emitter** (display Dots). Born after age **60 → 10**, **Crest 0**, **Aerated ~20**, **Min Impact 0 / Max Impact 10** → impact foam. [▶ 1:21](https://youtu.be/MRrkMcNyU-w?t=81)
2. Why "leaks": foam is born within a radius around edge particles, sometimes outside the collider, and can't get back. [▶ 2:43](https://youtu.be/MRrkMcNyU-w?t=163)
3. Method A — **nxKill**: Volume **Outside Bounds**, Radius **0** (kills everything), then Fields ▸ drag in the collider, layer mode **Points → Volume**, Remapping ▸ **Invert** → only particles outside the capsule die. [▶ 3:52](https://youtu.be/MRrkMcNyU-w?t=232)
4. Method B — **nxQuestion**: Question type **Document**, data **Object Distance** using the collider's **volume**; **> 0** = outside → Action **Kill**. [▶ 5:08](https://youtu.be/MRrkMcNyU-w?t=308)

## Newest equivalent
2026.1 beta **nxFalloff Object** mode (one of 16) on nxKill gives the same custom shape without C4D fields; nxFoam was rewritten in Fused 2025.4 (foam/bubbles/spray layers).
