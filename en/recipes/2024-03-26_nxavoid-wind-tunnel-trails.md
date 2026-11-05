# Stylised wind-tunnel flow lines around a car (nxAvoid + nxAttract + nxDirection + xpTrail)

- Source: Top Tip Tuesday — NeXus Wind Tunnel — https://www.youtube.com/watch?v=BGuwXsKofbo (2024-03-26)
- Host / generation: C4D; NeXus GPU (nxAvoid, nxAttract, nxDirection) on an xpEmitter + CPU xpOpenVDBMesher, xpJoin, xpTrail
- Goal: arrow particles that flow around a car body and leave aerodynamic streak lines.

## Base
xpEmitter Rate mode, lifespan 200, 60 particles/s, speed 240, Arrow display. Car = many objects in a null under **xpJoin**.

## Steps
1. Low-poly dummy: **xpOpenVDBMesher** with the xpJoin; on the object entry set mesh mode **Surface → Points**; **Voxel size 6**; filters: remove default Median, add **Curvature** (a few iterations) + **Offset** (shrink until the real car just pokes through). **C** to make editable, name "dummy car", hide.
2. **nxAvoid** with the dummy car, default **Change Direction** mode.
3. Emitter **Extended Data ▸ Rotation: Tangential** so arrows point along travel.
4. **nxAttract** at the car: **Force** mode (better than Velocity when mixing modifiers), Force ~200.
5. Limit nxAttract with a **Box field** around the car (small inner falloff) so particles stop clustering once past it.
6. **nxDirection**: default uses the modifier's rotation, pushes along its **+Z** — straightens the exit flow. Lower its strength for more variation.
7. **xpTrail** (default) on the emitter → streak lines.

## Gotchas
- Without the field, nxAttract makes particles pile up around the target.

## Newest equivalent
Same modifiers in NeXus 2026 (nxEmitter + nxTrail); **nxWarp Wind gust / Path** (2026.1 beta) or nxFollowGeo for guiding streams.
