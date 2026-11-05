# nxInfectio — tool card

Mentioned in **7** recipes · 2023-03-29 → 2025-10-14 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **nxInfectio** → **Add Seed Object** (volume — particles inside start infected), Search Radius 25 cm, Max Infected 3. [▶ 2:08](https://youtu.be/veRxUHtrnFA?t=128) — *[2025-10-14](../../recipes/2025-10-14_city-lights-edge-infection.md)*
- **nxInfectio** ▸ **Add Seed Object**; move the seed to the tube's edge — infection spreads from there (default: plain circular growth). [▶ 1:26](https://youtu.be/xGxf_IIIekY?t=86) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- nxInfectio mode **Fixed Value → Use Groups**; Ctrl-add an incubating and an infected group (group 2 = the ones to peel). [▶ 3:14](https://youtu.be/xGxf_IIIekY?t=194) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxInfectio** with 3 **seed objects** at the top. Lighter particles infect faster; raise search radius and allowed infections per particle to speed it up. [▶ 1:29](https://youtu.be/DsZ56QYQ2cY?t=89) — *[2024-06-11](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)*
- **nxFluids** below nxInfectio, solver **SPH** (unlocks **Granular**): **Friction 100%**, **Stability 10**, **Cohesion 5**; substeps 3 for previews. [▶ 3:31](https://youtu.be/DsZ56QYQ2cY?t=211) — *[2024-06-11](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)*
- **nxInfectio** ▸ **Add Seed Object** (spherical volume) — place it near the belly. Orange = infected, blue = incubating. [▶ 1:34](https://youtu.be/Be90jYTwF0c?t=94) — *[2023-12-12](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)*
- nxInfectio ▸ **Infected Lifespan 300 → 150** frames so blown pieces die. [▶ 5:47](https://youtu.be/Be90jYTwF0c?t=347) — *[2023-12-12](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)*

## All recipes (7)
- 2025-10-14 · [City lights spreading along building edges (nxInfectio + groups)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-05-22 · [Paint-style peeling off a surface (nxInfectio groups + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2024-06-11 · [Statue crumbling into sand as an infection spreads (nxInfectio groups + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2023-12-12 · [Infection-driven peel-away (nxInfectio Use Groups + nxWind/nxTurbulence on infected group + nxConstraints Distance break)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-11-16 · [Asteroids orbiting planets + spreading glow (nxAttract Force/Speed Limit, xpColor with particle fields, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-06-26 · [Feature notes: new NeXus modifiers — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, nxBlend modes, nxFoam on caches, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-03-29 · [Higher-res fire re-sim from spawned fuel particles (xpSpawn on infected groups, cache Include, finer xpExplosiaFX voxels)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
