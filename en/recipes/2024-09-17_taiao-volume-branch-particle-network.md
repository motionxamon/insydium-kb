# Non-intersecting particle branches inside a mesh (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)

- Source: Top Tip Tuesday — Volume Particle Networks — https://www.youtube.com/watch?v=WTMgHpdgOhY (2024-09-17)
- Host / generation: C4D; **Taiao** tree (spline output) + NeXus G2 (nxPush, nxQuestion, nxScale, nxColor) on xpEmitters; C4D fields
- Goal: a branching network filling a wolf head, grown/revealed as particles where a field passes.

## Steps
1. Add a **Taiao tree**; Display ▸ show **attraction points** (branches compete for points inside the green crown).
2. Volume Points: **Crown shape → Volume Objects**, drop in the head mesh; points **100 → 1,000** (slower to generate).
3. Object type **Poly → Spline**; optionally make editable (C) and set the spline to **B-Spline** to soften sharp corners.
4. xpEmitter Object mode = the spline, **emit from edges**; **Shot 15,000**, full lifespan, speed 0, radius **1**.
5. **nxPush**, Distance mode **Particle Radius** — then exclude it from the parent emitter (Modifiers tab, exclude list) so parents stay put.
6. **nxQuestion** + **Spherical Field**: Particle **Field > 0** → **Spawn** once, 1 particle, distance 0, new spawn emitter (Spheres display), Inherit off, speed 0, radius ~**1.5**. Hide parents.
7. Spawn at radius 0 instead, then **nxScale ▸ Value over time**, small rate + variation, clamp **0 → 1.5** → particles grow after birth.
8. **nxColor ▸ Gradient by Parameter**, preset gradient, parameter = **Field**; field = the head mesh in **Surface** mode → outer particles light, inner dark; adjust radius to move the boundary.

## Newest equivalent
**nxDendrite** (branches/network/lattice) can build the network inside NeXus; **nxSpawn** (2026.1 Beta 3) for the reveal; nxFalloff **Object** / **Spline** modes instead of C4D fields.
