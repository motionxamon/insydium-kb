# Springy constraint web rendered as trails (nxConstraints Birth connections + nxTrail Constraints mode)

- Source: Top Tip Tuesday — Birth Constraints — https://www.youtube.com/watch?v=QDBN_Xu_l68 (2026-07-14)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxConstraints, nxCollider, nxGravity, nxTrail; Cycles
- Goal: a sheet of spring-linked particles shot onto three Suzannes, with the connections rendered as glowing lines.

## Steps
1. **nxEmitter**: wide/tall rectangle, **Shot** ~700, Speed 0; Display **Circle Filled**.
2. **nxConstraints** ▸ one layer, **Birth** connections (springs). Visualise via emitter Display ▸ **Display Constraints**.
3. Three Suzannes (Shift+D); **nxGravity**; **nxCollider** picking all three, Friction full (particles stick). Emitter Speed **8**, widen to ~12 to cover them.
4. Break Type default **Relative Connected 50%** (snaps at 50% stretch) → set **None**.
5. **Stiffness** sets stretch (~80 for bouncier); for stiffer than 100%, raise **Iterations** (10 = nearly rigid; 1 = default, springy).
6. Connection Limit **8** within Radius **0.4 m** (nearest neighbours); 3 = sparse, 20 = dense.
7. Floor plane added to the collider: some bounce; no friction = slide, friction = stick-and-snap.
8. **nxTrail** ▸ emitter ▸ Connections ▸ **Constraints** (instead of particle paths); turn off the emitter's constraint display.
9. Color: trail Thickness tab ▸ Trail Color Mode **Particle Color**; emitter color **Noise** with Magma gradient.
10. Render: trail Display **Lines → Splines** (GN geometry + auto material with trail color attribute) → feed Emission color, strength ~5. Thickness **Set from Value** 0.1 = thick tubes, **0.001** = fine lines (+ variation).

## Newest equivalent
2026.1 beta **nxPin** anchors constraint networks for cloth/rope; GPU cords and cloth are announced for the next beta.
