# xpJoin — tool card

Mentioned in **17** recipes · 2023-04-14 → 2025-11-04 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Parametric spheres inside **xpJoin**; emitter Object = join, **Offset Origin 3 cm**, Polygon Area, **Shot 60 000**, speed 0, **radius 0** (Squares display ignores radius). [▶ 0:39](https://youtu.be/Xe1seJC3g0k?t=39) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- MoGraph cityscape cloners inside **xpJoin**. Emitter Object = join, **Emit From Edges**, **Shot 200 000**, speed 0, black particles. [▶ 1:06](https://youtu.be/veRxUHtrnFA?t=66) — *[2025-10-14](../../recipes/2025-10-14_city-lights-edge-infection.md)*
- Alt + **xpJoin** over the mesh null → body parts become one object. [▶ 1:24](https://youtu.be/Qd_kEHZ-4JY?t=84) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Fix: right-click xpJoin ▸ **Bake as Alembic** → still a generator, still lags → drag into the Timeline Dope Sheet ▸ Functions ▸ **Bake Objects** with **Create Copy + PLA** → polygon object with point-level animation. [▶ 4:30](https://youtu.be/Qd_kEHZ-4JY?t=270) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Put the plane inside **X-Particles ▸ Utilities ▸ xpJoin**; switch off **Hide Source** to see the weights again. [▶ 1:17](https://youtu.be/yAZ7aY8Ed4Y?t=77) — *[2025-04-10](../../recipes/2025-04-10_vertex-map-emission-density.md)*
- Hide the low-poly collider rocks (xpJoin); show the high-res tfRocks; one rough material on their null, dark desaturated red. [▶ 11:03](https://youtu.be/hK1BxHqw4QU?t=663) — *[2024-11-04](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)*
- Cheap rock colliders: Ctrl-drag a copy of the tfRock null into Utilities, hide the high-res set, drop the copy's tfRock **Subdivisions to 1** (same shape, far fewer polys). Put the copy in an **xpJoin** and give the join one xpCollider tag (Bounce 0). [▶ 7:26](https://youtu.be/_W2ivetBEPo?t=446) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **xpJoin** with plant and flower as children; xpEmitter Object = the join, **Polygon Area**. [▶ 1:58](https://youtu.be/ZgUIL-udXks?t=118) — *[2024-05-28](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)*
- Low-poly dummy: **xpOpenVDBMesher** with the xpJoin; on the object entry set mesh mode **Surface → Points**; **Voxel size 6**; filters: remove default Median, add **Curvature** (a few iterations) + **Offset** (shrink until the real car just pokes through). **C** to make editable, name "dummy car", hide. [▶ 1:22](https://youtu.be/BGuwXsKofbo?t=82) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- Forks can only target geometry: **xpSprite** (Cube) on emitter end inside an **xpJoin**; Fork layer ▸ connect to **Custom Object** = the join. Hide join and particles. [▶ 4:24](https://youtu.be/sctuPLrOw60?t=264) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- **tfTrace** (ray-traced height from objects): object = the xpJoin. [▶ 1:40](https://youtu.be/jQlOjJUVaoI?t=100) — *[2023-11-21](../../recipes/2023-11-21_tftrace-text-landscape-reveal.md)*
- **xpCollider** tag on terrain sim (Bounce 0, Friction 0). Steps and rocks each go in an **xpJoin** (one collider tag per join); rocks Bounce 10, Friction 5. Display colour black for all colliders. [▶ 6:29](https://youtu.be/t-1ZIIRF8Jg?t=389) — *[2023-11-20](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)*
- Generator terrains must be wrapped in an **xpJoin** to be used as surfaces (one join per sim terrain). [▶ 7:06](https://youtu.be/yqfkRKgW1Mo?t=426) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- Several surfaces: Utilities ▸ **xpJoin**, eyedropper the Kaiju, duck and plane, then move the single xpCollider tag onto the xpJoin — one tag drives all. [▶ 5:19](https://youtu.be/x1SAOjOSOzs?t=319) — *[2023-08-22](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)*

## All recipes (17)
- 2025-11-04 · [Particles that bloom in the crevices of geometry (nxQuestion neighbours + field)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-14 · [City lights spreading along building edges (nxInfectio + groups)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-08-12 · [Clean particle emission from a mocap character (xpJoin → Alembic → PLA bake)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-04-10 · [Emission density from a procedural vertex map (Vertex Map + Linear field ▸ xpJoin ▸ xpEmitter Selection)](../../recipes/2025-04-10_vertex-map-emission-density.md)
- 2024-11-04 · [Rendering speed-colored foam as additive glow in Redshift, ACEScg into After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Angry swirling water seen only as foam (nxFluids + nxVorticity Force Limit + keyframed nxRotate → nxFoam colored by speed)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-07-23 · [Self-spawning particle networks inside a volume (nxQuestion neighbor search + Spawn, volume kill)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-05-28 · [Pollen from a Taiao flower's stamen tips (tiPlant custom object, xpJoin, layer selection, nxWind)](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)
- 2024-03-26 · [Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-01-16 · [Procedural forked lightning with sparks (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-11-21 · [Landscape logo/text that grows on (tfTrace + tfBlur + Snow erosion + masked noise + tfAdjustment with linear field)](../../recipes/2023-11-21_tftrace-text-landscape-reveal.md)
- 2023-11-20 · [Art-directed slow-mo particle splashes over steps and sand (nxFluids SPH, hidden tfRock bashers, xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-08-22 · [Splashing rain rig (xpCollider Spawn on collision, xpJoin for many colliders)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-05-30 · [Gloopy liquid without a fluid solver (nxConstraints birth springs → xpTrail Constraints algorithm → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-14 · [Wispy particles squirting from a breaking crystal (cached xpShatter, xpExplosiaFX Source tag, Advection, inner-face emission, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
