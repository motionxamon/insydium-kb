# Emitting from a spline projected onto a rippling surface (mtSplineSample + mtPointProject + Jiggle cache)

- Source: Top Tip Tuesday — Surface Project Particles — https://www.youtube.com/watch?v=iPU7lU5pCUA (2024-07-02)
- Host / generation: C4D; MeshTools (mtSplineSample, mtPointProject) + xpEmitter + NeXus (nxGravity, nxTurbulence, nxConstraints)
- Goal: an "X" text spline rides an animated, springy surface and emits particles that tumble over it.

## Surface
1. Plane 800×400, segments **80×40**. Child **Displacer** with a Noise, **global scale 2000**, **animation speed 1**.
2. Child **Jiggle** below it: **Stiffness 10**, **Structural 10**, **Strength 200%** → rippling spring.
3. Jiggle ▸ Cache ▸ **Calculate**, then disable the Displacer (it's baked).

## Projection
4. **mtSplineSample** with the text as child, Method **Distance** (point every 2 cm), close the spline, hide points/gradient display.
5. **mtPointProject**: surface = plane, spline sample as child. Default ray direction is Parallel +Y → change to **+Z** so it hits the plane. **Offset 1 cm**, **Blend 99%**.

## Particles
6. xpEmitter Object = the point project, **Edges**; Rate, lifespan 35 (var 10), **2000/frame**, speed 0, radius 2. xpCollider on the plane.
7. **nxGravity** 200, **nxTurbulence**.
8. Optional **nxConstraints ▸ Viscosity**: connection limit 4, radius 25 cm → particles cling together as the surface knocks them around.
