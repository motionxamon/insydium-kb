# Particles that bloom in the crevices of geometry (nxQuestion neighbours + field)

- Source: Top Tip Tuesday — Neighbor Cracks — https://www.youtube.com/watch?v=Xe1seJC3g0k (2025-11-04)
- Host / generation: NeXus (nxQuestion Neighbors + Field, nxPush, nxColor layers) + Redshift
- Goal: as a field sweeps over clustered spheres, particles grow only in the seams where spheres meet.

## Steps
1. Parametric spheres inside **xpJoin**; emitter Object = join, **Offset Origin 3 cm**, Polygon Area, **Shot 60 000**, speed 0, **radius 0** (Squares display ignores radius).
2. nxQuestion: `Particle ▸ Neighbors (40 cm) > 420` → only seam particles (they see points from two surfaces). Tune the count by trial (300 = almost all, 400–420 = seams only).
3. Gate with a field: add the Sphere field to the **nxQuestion Fields tab** (must be listed!), then `If Field > 0.5` (inner falloff) **AND** child `Neighbors > 420` → actions.
4. Actions: **Set Radius 3** with **Delay** (springy growth). Display Circles/Spheres to see radius.
5. **nxPush** Particle Radius mode, strong → grown particles shove each other.
6. **nxColor** Gradient by **Radius** 2–6 (turquoise→orange preset); tone down saturation procedurally with a top **Set Color gray** layer in **Screen** blend (lower its strength to bring saturation back).
7. Redshift Object tag → Sphere Instances.
