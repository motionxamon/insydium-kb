# Tree that grows inside any object's volume (Taiao Tree: Volume Objects, attraction points, multi-instance leaves)

- Source: Top Tip Tuesday — Taiao toTree — https://www.youtube.com/watch?v=G7vDdlvLIzM (2023-04-11)
- Host / generation: C4D; Taiao Tree (space-colonisation style; no particles); C4D materials
- Goal: a tree whose crown takes the shape of a model or logo (an INSYDIUM rubber duck in the demo).

## Steps
1. INSYDIUM ▸ Taiao ▸ **Taiao Tree** (+ Growth Point = trunk start). Branches are drawn to **attraction points** in the crown volume without intersecting. [▶ 0:31](https://youtu.be/G7vDdlvLIzM?t=31)
2. Display: show attraction points + **Crown Mesh** (default cylinder) to understand it. [▶ 0:48](https://youtu.be/G7vDdlvLIzM?t=48)
3. Volume Points tab: attraction points **100 → 1000** (more points = more branches). Crown shape can come from the Tree Crown Profile spline, or… [▶ 1:08](https://youtu.be/G7vDdlvLIzM?t=68)
4. Generation Method → **Volume Objects**; drag the model in and hide it — points now fill the model. Turn displays off. [▶ 1:21](https://youtu.be/G7vDdlvLIzM?t=81)
5. Lighter mesh: **Ring Segments 6**, **Resolution Length 5 → 10** (new segment every 10 cm). [▶ 2:20](https://youtu.be/G7vDdlvLIzM?t=140)
6. Organ mode (leaves/fruit are organs): Single Poly → **Multi-Instances**. Leaves tab ▸ **Use Leaves**. [▶ 2:45](https://youtu.be/G7vDdlvLIzM?t=165)
7. Leaf Geometry: **Length segments 3**; pinch the **Leaf Profile** spline at base and tip; Size **0.95**, variation **20%**. [▶ 3:27](https://youtu.be/G7vDdlvLIzM?t=207)
8. Distribution ▸ **Position on Tree** spline: move the base knot so no leaves sprout from the trunk. [▶ 4:12](https://youtu.be/G7vDdlvLIzM?t=252)
9. Fill out: attraction points **5000** (slower to solve). [▶ 4:29](https://youtu.be/G7vDdlvLIzM?t=269)
10. Materials tab: bark → Trunk (+ assign to trunk children = branches); Leaf 1 and Leaf 2 both on Leaf → light/dark mix. [▶ 5:00](https://youtu.be/G7vDdlvLIzM?t=300)
11. Object Properties: animate **growth** to grow tree and leaves on/off. [▶ 5:23](https://youtu.be/G7vDdlvLIzM?t=323)

## Newest equivalent
Particle-based branching today: **nxDendrite** (branches/network) or nxBioLogic (2026.1 beta); Taiao itself gained growth animation and forces in Fused 2023.3.
