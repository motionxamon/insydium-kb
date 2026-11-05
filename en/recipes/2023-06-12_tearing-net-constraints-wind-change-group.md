# Tearing constraint net peeled off a logo (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)

- Source: Maintenance Training — Dynamics - Constraints - Tearing Net Tutorial — https://www.youtube.com/watch?v=WeuXOmENNXA (2023-06-12)
- Host / generation: C4D; CPU X-Particles (xpConstraints, xpWind, xpChangeGroup, xpTrail, xpSplineMesher, xpOpenVDBMesher)
- Goal: a web of connected particles covering a MoText logo that is torn away by wind, art-directed with a moving field, then turned into renderable trails / meshes.

## Base
MoText "XP" (bold, centered), extruded a bit deeper, Fillet Caps 3 steps / radius 3, later hidden.

## Steps
1. **xpEmitter ▸ Object**: Emitter Shape Object = MoText, emit from **Polygon Area**; **Offset Origin 1 cm** so particles sit just above the surface. [▶ 1:54](https://youtu.be/WeuXOmENNXA?t=114)
2. Emission: **Shot**, **2000** particles, full lifespan, speed 0. Display: Squares + **Display Constraints** on. [▶ 2:33](https://youtu.be/WeuXOmENNXA?t=153)
3. **xpConstraints ▸ Connections ▸ Birth Connections** on with defaults → instant netting look. [▶ 4:14](https://youtu.be/WeuXOmENNXA?t=254)
4. **xpWind** rotated 90° to blow upward. Put an **xpCollider tag** on the MoText so particles slide over it and the links strain and snap (break settings in the Constraints object control when). [▶ 7:12](https://youtu.be/WeuXOmENNXA?t=432)
5. Art-direct with groups: emitter **Groups** ▸ add 2 groups, Mode **First Group Only** (all start in group 1). Wind ▸ **Groups Affected** = group 2 only. [▶ 8:43](https://youtu.be/WeuXOmENNXA?t=523)
6. **xpChangeGroup** (Control modifiers): New Group = group 2, falloff = **Spherical field**. Animate the sphere across the text → particles join group 2, get blown off and drag their neighbours, tearing organically. [▶ 10:36](https://youtu.be/WeuXOmENNXA?t=636)
7. Render route 1: **xpTrail** with the emitter, **Algorithm ▸ Connections: Constraints**, then pick the Birth Connections layer; hide Display Constraints. Trails take an X-Particles material and render. [▶ 13:23](https://youtu.be/WeuXOmENNXA?t=803)
8. Route 2: **xpSplineMesher** on the trail, radius ~0.5, **Joins off** (Joins are for xpBranch-style branching and triangulate constraint trails). [▶ 15:05](https://youtu.be/WeuXOmENNXA?t=905)
9. Route 3 (organic/viscous look): **xpOpenVDBMesher** with the Spline Mesher as source; lower Voxel Size and raise the Spline Mesher radius so there is enough volume to mesh. [▶ 16:28](https://youtu.be/WeuXOmENNXA?t=988)

## Gotchas
- Rate emission would fire 2000/s — use Shot for a one-off fill.
- Wind with a field falloff only demonstrates the idea; the group-switch method gives proper control.
- Trails + meshers on top of the constraint sim slow playback noticeably.

## Newest equivalent
**nxConstraints** (same layers, GPU) + **nxPin** for anchoring and **nxDeformer** for a tearing mesh in the 2026.1 beta; **nxTrail** and **nxMesher** replace xpTrail/xpOpenVDBMesher. Native GPU cloth/tearing + fraying is only announced for a future NeXus beta.
