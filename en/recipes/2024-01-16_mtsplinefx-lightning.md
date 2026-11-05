# Procedural forked lightning with sparks (mtSplineFX + xpSplineMesher + xpSpawn)

- Source: Top Tip Tuesday — mtSplineFX Lightning — https://www.youtube.com/watch?v=sctuPLrOw60 (2024-01-16)
- Host / generation: C4D; MeshTools **mtSplineFX** + CPU X-Particles (xpSplineMesher, xpSprite, xpJoin, xpSpawn, xpGravity)
- Goal: electric arcs from a sphere to a plane, with sub-forks and falling sparks.

## Base
Emitter Start (blue, on a sphere) and Emitter End (orange, on a small plane), both **Pulse** mode, sticking to their source objects.

## Steps
1. **mtSplineFX**: Start = emitter start, End = emitter end, connection type **to points** → each start particle links to its nearest end particle.
2. **xpSplineMesher**: Joins off, Vertex Colors off, spline = mtSplineFX, size ~1 cm, scaling spline tapered to a point at the tip; emissive material.
3. mtSplineFX ▸ Motion ▸ **Large noise**: amplitude 150, scale 500, animation speed 350 → frantic lightning.
4. Connections ▸ add **Fork** layer (default 2 forks/spline). Edit the **distribution curve** to zero at base and tip so forks sprout mid-spline.
5. Forks can only target geometry: **xpSprite** (Cube) on emitter end inside an **xpJoin**; Fork layer ▸ connect to **Custom Object** = the join. Hide join and particles.
6. Ctrl-drag a copy of the Fork layer as a **child** of the first → sub-forks.
7. Sparks: **xpSpawn**, exclude it on the start emitter's Modifiers tab; new spawn emitter: lifespan 10 (var 5), speed 200 (var 150), **Lines** display, thin, orange; spawn 60 (var 20) per frame, default spherical direction.
8. **xpGravity** with reduced strength; Draw Emitter off. Move the sphere to steer the bolts.

## Newest equivalent
**nxSpawn** (2026.1 beta) for spark children; mtSplineFX remains the lightning tool.
