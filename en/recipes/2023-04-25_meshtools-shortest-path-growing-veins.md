# Procedural growing veins on a model (MeshTools Remesh + mtShortestPath + xpSplineMesher)

- Source: Top Tip Tuesday — MeshTools Veins — https://www.youtube.com/watch?v=_03xlveAuZ4 (2023-04-25)
- Host / generation: C4D; MeshTools + X-Particles **xpSplineMesher** generator (CPU, no particles)
- Goal: tapered veins that grow across a mesh from one or several roots.

## Steps
1. Ctrl-drag a copy of the model, hide the original. INSYDIUM ▸ MeshTools ▸ **Remesh** with the copy as child → triangles (better vein flow); press **C** to make it editable. [▶ 0:15](https://youtu.be/_03xlveAuZ4?t=15)
2. MeshTools ▸ **mtShortestPath**, triangle mesh as child. Display tab ▸ show **start/end points** (bigger size): one random blue start vertex, random red end vertices; paths follow edges start → end. [▶ 1:12](https://youtu.be/_03xlveAuZ4?t=72)
3. Object tab: **End count 500**. Hide the point display. [▶ 1:56](https://youtu.be/_03xlveAuZ4?t=116)
4. Animate: enable **Custom Growth Rates** + variation so each path grows at its own speed; enable **Avoid** to stop paths overlapping. [▶ 2:21](https://youtu.be/_03xlveAuZ4?t=141)
5. Optional control: put a point selection tag in **Source** to choose the start points. [▶ 2:41](https://youtu.be/_03xlveAuZ4?t=161)
6. INSYDIUM ▸ X-Particles ▸ Generators ▸ **xpSplineMesher**: Joins off, vertex colors off; link mtShortestPath. Hide the path, show the original model. [▶ 3:06](https://youtu.be/_03xlveAuZ4?t=186)
7. Size **2–3 cm**; open the Size curve and drop the end to 0 so veins taper to a point. Red material on the mesher. [▶ 3:54](https://youtu.be/_03xlveAuZ4?t=234)
8. Reverse growth: mtShortestPath **Invert** — then flip the mesher's size curve (select both points ▸ **Flip Horizontal**) so the taper still points the right way. [▶ 4:32](https://youtu.be/_03xlveAuZ4?t=272)
9. More roots: **Start count 4** → paths recompute from four roots; they deform with the animated geo. [▶ 5:15](https://youtu.be/_03xlveAuZ4?t=315)

## Gotchas
Paths can also be rendered directly as glowing trails (FUI look) instead of meshing.
