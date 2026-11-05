# Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)

- Source: Top Tip Tuesday — nxConstraints Reaction — https://www.youtube.com/watch?v=9w-L9qWwGqQ (2024-02-27)
- Host / generation: C4D; NeXus GPU (nxConstraints, nxScale, nxGravity, Mapping) + CPU xpTrail / xpSplineMesher
- Goal: a field of connected particles at rest; a nudge makes them grow, knock neighbours and spread a wave.

## Base
Floor plane + cylinder, both with xpCollider tags. Emitter Object mode on the plane (polygon area), **Shot 6000**, radius 3.

## Steps
1. **nxConstraints ▸ Birth**: up to 3 connections within **65 cm**, Stiffness **60%**, break when stretched past **150%** of birth length. See them via emitter Display ▸ **Display Constraints**.
2. Add a **Collisions** layer (particle-particle); **Iterations 8** (more accurate and stiffer).
3. **nxScale**: parameter Radius, operation **Set Value 10**.
4. nxScale ▸ Mapping ▸ **Distance (travelled)** → Radius value, range 0–100 cm. Edit curve: start at 0, peak at full almost immediately, then taper down — unmoved particles have radius 0, so nothing happens yet.
5. Animate/move the **cylinder** into the particles to trigger: moved particles grow, hit neighbours, and so on.
6. **nxGravity** (default) with Mapping ▸ Distance travelled → Gravity Strength, 0–100 cm: none until ~40 cm, full by ~60 cm.
7. Faster spread: nxScale distance range 100 → **50 cm**.
8. To render/mesh springs: **xpTrail ▸ Algorithm: Constraints ▸ Birth Constraints** on → mesh with **xpSplineMesher**.

## Newest equivalent
Same in NeXus 2026; **nxPin** (2026.1 beta) can anchor parts of the sheet; per-layer nxFalloff lists for spatial control.
