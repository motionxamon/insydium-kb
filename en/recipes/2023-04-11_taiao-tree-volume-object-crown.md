# Tree that grows inside any object's volume (Taiao Tree: Volume Objects, attraction points, multi-instance leaves)

- Source: Top Tip Tuesday — Taiao toTree — https://www.youtube.com/watch?v=G7vDdlvLIzM (2023-04-11)
- Host / generation: C4D; Taiao Tree (space-colonisation style; no particles); C4D materials
- Goal: a tree whose crown takes the shape of a model or logo (an INSYDIUM rubber duck in the demo).

## Steps
1. INSYDIUM ▸ Taiao ▸ **Taiao Tree** (+ Growth Point = trunk start). Branches are drawn to **attraction points** in the crown volume without intersecting.
2. Display: show attraction points + **Crown Mesh** (default cylinder) to understand it.
3. Volume Points tab: attraction points **100 → 1000** (more points = more branches). Crown shape can come from the Tree Crown Profile spline, or…
4. Generation Method → **Volume Objects**; drag the model in and hide it — points now fill the model. Turn displays off.
5. Lighter mesh: **Ring Segments 6**, **Resolution Length 5 → 10** (new segment every 10 cm).
6. Organ mode (leaves/fruit are organs): Single Poly → **Multi-Instances**. Leaves tab ▸ **Use Leaves**.
7. Leaf Geometry: **Length segments 3**; pinch the **Leaf Profile** spline at base and tip; Size **0.95**, variation **20%**.
8. Distribution ▸ **Position on Tree** spline: move the base knot so no leaves sprout from the trunk.
9. Fill out: attraction points **5000** (slower to solve).
10. Materials tab: bark → Trunk (+ assign to trunk children = branches); Leaf 1 and Leaf 2 both on Leaf → light/dark mix.
11. Object Properties: animate **growth** to grow tree and leaves on/off.

## Newest equivalent
Particle-based branching today: **nxDendrite** (branches/network) or nxBioLogic (2026.1 beta); Taiao itself gained growth animation and forces in Fused 2023.3.
