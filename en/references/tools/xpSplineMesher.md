# xpSplineMesher — tool card

Mentioned in **12** recipes · 2023-02-14 → 2025-11-06 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpSplineMesher** (X-Particles ▸ Generators): objects = both edge splines + the SplineFX spline; Joins off, Size **2**. Group the splines in a null (Alt+G) and hide — the rig stays procedural. [▶ 3:09](https://youtu.be/rDSSeIZUl08?t=189) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- **xpSplineMesher** with the shortest-path object as source: turn off **joins**, **size 2**, **subdivisions 2** (round instead of box section). [▶ 4:35](https://youtu.be/POC6gx3p4rc?t=275) — *[2025-09-18](../../recipes/2025-09-18_meshtools-slime-mold-shortest-path.md)*
- To render/mesh springs: **xpTrail ▸ Algorithm: Constraints ▸ Birth Constraints** on → mesh with **xpSplineMesher**. [▶ 6:38](https://youtu.be/9w-L9qWwGqQ?t=398) — *[2024-02-27](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)*
- **xpSplineMesher**: Joins off, Vertex Colors off, spline = mtSplineFX, size ~1 cm, scaling spline tapered to a point at the tip; emissive material. [▶ 1:15](https://youtu.be/sctuPLrOw60?t=75) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- **xpSplineMesher** on the trail: Joints and Vertex Colors off, **1 subdivision**, Size **1.5**, taper with the **Scale Along Spline** graph to a point. Hide the trail, apply a glass material. [▶ 3:41](https://youtu.be/M4z3kOU4YEw?t=221) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- **xpSplineMesher** on the trail, vertex colors + joints off, size 1.5. **xpCache** (external files, 90 F); then disable the control emitter and trail. [▶ 23:17](https://youtu.be/yqfkRKgW1Mo?t=1397) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- Route 2: **xpSplineMesher** on the trail, radius ~0.5, **Joins off** (Joins are for xpBranch-style branching and triangulate constraint trails). [▶ 15:05](https://youtu.be/WeuXOmENNXA?t=905) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- **xpTurbulence** for wiggle. **xpTrail ▸ Algorithm: Tendrils** connections (not tracing the birth particle). **xpSplineMesher** on the trail: Subdivision 1, Size ▸ **Scale Spline** curve to taper to a point. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- INSYDIUM ▸ X-Particles ▸ Generators ▸ **xpSplineMesher**: Joins off, vertex colors off; link mtShortestPath. Hide the path, show the original model. [▶ 3:06](https://youtu.be/_03xlveAuZ4?t=186) — *[2023-04-25](../../recipes/2023-04-25_meshtools-shortest-path-growing-veins.md)*
- Generators ▸ **xpSplineMesher**; link the xpTrail → basic geometry around each trail. **Subdivisions** 1–2 → round tubes. [▶ 4:06](https://youtu.be/YaFY_HUvnug?t=246) — *[2023-02-14](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)*

## All recipes (12)
- 2025-11-06 · [Particles growing over a procedural wire mesh (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-09-18 · [Slime-mold growth over a log (mtRemesh + mtShortestPath + xpSplineMesher)](../../recipes/2025-09-18_meshtools-slime-mold-shortest-path.md)
- 2024-03-15 · [Wind-blown sand off a desert dune (TerraformFX tfSpline dune + nxWind Von Karman, nxAvoid, field-limited nxTurbulence)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-27 · [Spreading physics chain reaction (nxConstraints Birth + Collisions, nxScale/nxGravity mapped to Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-01-16 · [Procedural forked lightning with sparks (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-12-19 · [Swaying glass tendrils with particles on the tips (xpTendril + xpTrail Tendrils + xpSplineMesher + xpTrailTip tag)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Crystals sprouting along frozen particle paths (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-06-23 · [Feature notes: X-Particles 2023.3 — live spawn/foam from caches, multi-instances, stuck rotation, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-06-12 · [Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Wiggly tendrils held together by constraints (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-04-25 · [Procedural growing veins on a model (MeshTools Remesh + mtShortestPath + xpSplineMesher)](../../recipes/2023-04-25_meshtools-shortest-path-growing-veins.md)
- 2023-02-14 · [Wiggly animated trails turned into tapered tubes (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
