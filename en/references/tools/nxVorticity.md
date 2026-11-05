# nxVorticity — tool card

Mentioned in **4** recipes · 2024-03-19 → 2025-09-11 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxVorticity**: radius 150, strength 2000, **limit 100** (vorticity accumulates); Mapping ▸ **Age 0 → 150** → strength builds = boiling. [▶ 2:17](https://youtu.be/u2MiqeckNaQ?t=137) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **nxVorticity** below the fluid solver: Strength **600%** already sustains swirls; raise **Radius** a little (bigger eddies). Very high strength (~1500%) boils the water — pair it with **Force Limit 20** to keep it strong but controlled. [▶ 12:23](https://youtu.be/_W2ivetBEPo?t=743) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Turn off nxFluids, nxVorticity and nxRotate (fluid is cached); **keep nxGravity** — nxFoam needs gravity for buoyancy/advection. Hide the fluid emitters. [▶ 27:07](https://youtu.be/_W2ivetBEPo?t=1627) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Add **nxVorticity** — it measures existing swirl and amplifies it. — *[2024-03-19](../../recipes/2024-03-19_nxvorticity-choppy-water.md)*

## All recipes (4)
- 2025-09-11 · [Feature notes: rewritten NeXus GPU core, per-layer GPU falloffs + Data Mapping, nxQuestion variations & neighbour search](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-06-10 · [Fluid sphere: settle → boil → explode → slosh (initial state + age-mapped nxVorticity / nxWind)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-03-19 · [Choppy, swirling water body (nxVorticity on PBD vs SPH)](../../recipes/2024-03-19_nxvorticity-choppy-water.md)
