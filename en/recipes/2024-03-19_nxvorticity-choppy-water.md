# Choppy, swirling water body (nxVorticity on PBD vs SPH)

- Source: Top Tip Tuesday — nxVorticity — https://www.youtube.com/watch?v=4WS1-4s6EXc (2024-03-19)
- Host / generation: C4D; NeXus GPU (nxFluids PBD/SPH, nxVorticity, nxGravity) + xpCollider tag
- Goal: stop a drop-tank sim from settling; keep strong eddies like wind against tide.

## Base
xpEmitter Box 100×100×100, **Hexagonal shot**, speed 0, radius 1.5. Default nxGravity, default **nxFluids PBD**. Cube with **xpCollider tag set to Inside**.

## Steps
1. Add **nxVorticity** — it measures existing swirl and amplifies it.
2. PBD: **Radius 150%** (neighbour search), then **Strength 8%** → clear eddies; **20%** = tidal chop.
3. Tame runaway growth with **Force Limit** (10 → 5): strong but controlled swirls.
4. Larger radius = bigger, slower coherent swirls; smaller = choppy small eddies.
5. SPH: switch solver, raise substeps; SPH solves velocity so accurately it has little internal swirl → needs far more strength: **200%**, up to **300%**, and re-tune Force Limit.

## Gotchas
- Required strength depends heavily on the solver (PBD low, SPH roughly 10× higher).

## Newest equivalent
nxVorticity carries over to NeXus 2026; for big water consider **nxOcean** (2026.1 beta) or FLIP/APIC with nxVorticity.
