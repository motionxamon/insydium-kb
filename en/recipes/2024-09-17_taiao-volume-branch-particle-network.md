# Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)

- Source: Top Tip Tuesday — Volume Particle Networks — https://www.youtube.com/watch?v=WTMgHpdgOhY (2024-09-17)
- Host / generation: C4D; **Taiao** tree (spline output) + NeXus G2 (nxPush, nxQuestion, nxScale, nxColor) on xpEmitters; C4D fields
- Goal: a branching network filling a wolf head, grown/revealed as particles where a field passes.

## Steps
1. Add a **Taiao tree**; Display ▸ show **attraction points** (branches compete for points inside the green crown). [▶ 0:28](https://youtu.be/WTMgHpdgOhY?t=28)
2. Volume Points: **Crown shape → Volume Objects**, drop in the head mesh; points **100 → 1,000** (slower to generate). [▶ 1:05](https://youtu.be/WTMgHpdgOhY?t=65)
3. Object type **Poly → Spline**; optionally make editable (C) and set the spline to **B-Spline** to soften sharp corners. [▶ 1:40](https://youtu.be/WTMgHpdgOhY?t=100)
4. xpEmitter Object mode = the spline, **emit from edges**; **Shot 15,000**, full lifespan, speed 0, radius **1**. [▶ 2:20](https://youtu.be/WTMgHpdgOhY?t=140)
5. **nxPush**, Distance mode **Particle Radius** — then exclude it from the parent emitter (Modifiers tab, exclude list) so parents stay put. [▶ 4:28](https://youtu.be/WTMgHpdgOhY?t=268)
6. **nxQuestion** + **Spherical Field**: Particle **Field > 0** → **Spawn** once, 1 particle, distance 0, new spawn emitter (Spheres display), Inherit off, speed 0, radius ~**1.5**. Hide parents. [▶ 4:14](https://youtu.be/WTMgHpdgOhY?t=254)
7. Spawn at radius 0 instead, then **nxScale ▸ Value over time**, small rate + variation, clamp **0 → 1.5** → particles grow after birth. [▶ 5:27](https://youtu.be/WTMgHpdgOhY?t=327)
8. **nxColor ▸ Gradient by Parameter**, preset gradient, parameter = **Field**; field = the head mesh in **Surface** mode → outer particles light, inner dark; adjust radius to move the boundary. [▶ 6:04](https://youtu.be/WTMgHpdgOhY?t=364)

## Newest equivalent
**nxDendrite** (branches/network/lattice) can build the network inside NeXus; **nxSpawn** (2026.1 Beta 3) for the reveal; nxFalloff **Object** / **Spline** modes instead of C4D fields.
