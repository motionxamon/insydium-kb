# Upres a granular sim while keeping its shape (cached low-res + nxUpres velocity blend)

- Source: Top Tip Tuesday — Upres Granular Sims — https://www.youtube.com/watch?v=GU37kEW507c (2025-04-15)
- Host / generation: C4D; NeXus inside X-Particles (nxFluids SPH Granular, nxUpres) + xpCache
- Goal: art-direct grains fast at low count, then get a ~10× denser sim with the same clumps and cracks.

## Base
Object emitter (bust volume), **Shot Hexagonal, radius 2 cm**, **speed 500 cm along −X** into a wall. **nxFluids SPH Granular**: **Substeps 20, Friction 100, Stability 20, Cohesion 10**.

## Steps
1. Emitter ▸ Emission: **Subframe Emit off** when using initial speed in granular sims (on = staggered birth → explosive start).
2. Simply dropping radius to 1 gives detail but a completely different sim — so instead **cache the radius-2 sim** (xpCache ▸ Build Cache).
3. Duplicate the emitter; remove the cache tag from the copy; set copy radius **1 cm** (still live in nxFluids).
4. Add **nxUpres**: Source = cached low-res emitter, Destination = live high-res emitter, transfer **Velocity only**.
5. Neighbours: default 3 closest source particles → raise to **20** for a smoother blend (more cost). Hide the source; play.

## Gotchas
Result is still a live fluid sim — overall shape and big lumps match, fine detail differs. That's the point.

## Newest equivalent
nxUpres is still the tool (also in NeXus 2026 / Blender). For new sand work the 2026.1 beta **nxMPM** sand material is an alternative solver; the low-res-cache → nxUpres approach still applies to it conceptually.
