# Self-organising particle blob (nxConstraints Forces attraction/repulsion + radius-mapped repulsion + Collisions + Friction)

- Source: Top Tip Tuesday — nxConstraints Forces — https://www.youtube.com/watch?v=avF-t9dIIXs (2023-10-10)
- Host / generation: C4D; G2 NeXus inside X-Particles (nxConstraints, nxTurbulence) + an attract modifier
- Goal: an organic, "alive" cluster where particles push and pull each other, small ones migrating to the outside.

## Base
**xpEmitter** with static particles in a grid, radius range **0–4 cm**.

## Steps
1. **nxConstraints** ▸ add **Forces** layer. Defaults are frantic: Attraction strength **10 → 1%**, Repulsion **→ 1%**. [▶ 0:03](https://youtu.be/avF-t9dIIXs?t=3)
2. Add a **Collisions** layer, weight **500** (no intersections). [▶ 1:16](https://youtu.be/avF-t9dIIXs?t=76)
3. Forces: connection limit **16 → 5**. Attraction radius **20 cm**, Repulsion radius **10 cm** — pulled in, then pushed away = organic motion. [▶ 2:03](https://youtu.be/avF-t9dIIXs?t=123)
4. Mapping ▸ **Radius** map, range **0 → 4**, category **Force**, parameter **Repulsion Radius**; curve: small particles full, large ones less. Raise the repulsion radius value until small ones move outward. [▶ 2:59](https://youtu.be/avF-t9dIIXs?t=179)
5. If repulsion radius exceeds attraction radius, particles escape → raise the attraction radius a little. [▶ 3:37](https://youtu.be/avF-t9dIIXs?t=217)
6. Enable the attract modifier (target = a null) to hold the ball together; raise repulsion strength to push the small particles to the rim. [▶ 4:30](https://youtu.be/avF-t9dIIXs?t=270)
7. **nxTurbulence** Voronoi, strong; Radius map 0–4 → small particles get full strength. [▶ 5:21](https://youtu.be/avF-t9dIIXs?t=321)
8. Calm it: **Friction** layer, connection limit **8**, low strength. [▶ 5:51](https://youtu.be/avF-t9dIIXs?t=351)

## Newest equivalent
Same layers exist in **nxConstraints** in NeXus 2026 (G3); compare recipe 2025-05-20 (spring network attract/repel forces). 2026.1 adds per-layer Falloffs for spatial control.
