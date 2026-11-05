# Emission density from a procedural vertex map (Vertex Map + Linear field ▸ xpJoin ▸ xpEmitter Selection)

- Source: Bite-Sized — Vertex Map Emission — https://www.youtube.com/watch?v=yAZ7aY8Ed4Y (2025-04-10)
- Host / generation: C4D; CPU xpEmitter + xpJoin utility; native C4D Vertex Map tag and fields
- Goal: a particle cloud whose thickness follows an (animatable) vertex weight, thinning to nothing where the weight is low.

## Steps
1. Plane primitive, **100 × 100** segments. Tags ▸ Other Tags ▸ **Vertex Map**; Use Fields is on by default — add a **Linear field** (red = 0, yellow = 1). Animate the field if you want the map to move. [▶ 0:29](https://youtu.be/yAZ7aY8Ed4Y?t=29)
2. Put the plane inside **X-Particles ▸ Utilities ▸ xpJoin**; switch off **Hide Source** to see the weights again. [▶ 1:17](https://youtu.be/yAZ7aY8Ed4Y?t=77)
3. **xpEmitter ▸ Object**: Emitter Shape Object = the join, Emit From **Polygon Area**; Emission ~**50,000**; Display **Dots** to read the cloud. [▶ 1:47](https://youtu.be/yAZ7aY8Ed4Y?t=107)
4. Emitter Object tab ▸ **Selection** link: drag in the vertex map (it also takes point/edge/polygon selections) → density now follows the weight. [▶ 2:28](https://youtu.be/yAZ7aY8Ed4Y?t=148)
5. **Vertex Map Threshold**: 50 → no particles where weight < 50%; back to 0 for a soft gradient. [▶ 3:03](https://youtu.be/yAZ7aY8Ed4Y?t=183)
6. More contrast: Linear field ▸ Remapping ▸ Contour Mode **Curve**, steepen the spline → most of the plane has little weight, only the high end gets a thick cloud. [▶ 4:17](https://youtu.be/yAZ7aY8Ed4Y?t=257)

## Newest equivalent
In the NeXus 2026.1 C4D beta, **nxFalloffMap** bakes nxFalloffs (16 modes) to vertex map / vertex color tags, so the same weight-driven emission can be built from nxFalloff instead of C4D fields.
