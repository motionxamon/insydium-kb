# Dry ice smoke spilling over a logo (nxExplosiaFX negative buoyancy)

- Source: Top Tip Tuesday — Dry Ice — https://www.youtube.com/watch?v=JKU37-9l0_U (2025-11-11)
- Host / generation: C4D, Fused 2025.4 beta (nxExplosiaFX)
- Goal: heavy, lingering fog rolling across the floor and around an obstacle.

## Steps
1. Sources: hidden **Tube** (dry-ice block), **Emit From Volume**, **Smoke 5**, default temperature, **Fuel 0**, **Pressure 30** (pushes smoke out). [▶ 1:05](https://youtu.be/JKU37-9l0_U?t=65)
2. **Voxel 2**. Simulation ▸ Buoyancy: **Smoke Buoyancy −20** (sinks after a little lift from heat). [▶ 1:53](https://youtu.be/JKU37-9l0_U?t=113)
3. Solver ▸ Domain Boundary Walls: **close −Y** (floor). [▶ 2:24](https://youtu.be/JKU37-9l0_U?t=144)
4. Solver ▸ Advection: Velocity and Temperature → **Fast** (quicker + smoother — suits fog). [▶ 3:28](https://youtu.be/JKU37-9l0_U?t=208)
5. Dissipation: smoke **~0.2** (lingers).
6. Colliders: the logo.
7. Dynamics: Turbulence **Voronoi** (author's favourite), strength ~10, smaller length scale, **Octaves 0** (just big swirls); **Vorticity ~6** for fine detail (10+ gets cotton-wool fuzzy). [▶ 6:29](https://youtu.be/JKU37-9l0_U?t=389)
8. **Retiming 50%** = same motion, half speed (slow-mo fog). [▶ 5:55](https://youtu.be/JKU37-9l0_U?t=355)
9. Display look: Albedo full, negative Scatter Anisotropy → brighter, misty. [▶ 2:52](https://youtu.be/JKU37-9l0_U?t=172)
10. Final: **Upscaling 1** for wispy detail; Redshift material in the scene file. [▶ 8:04](https://youtu.be/JKU37-9l0_U?t=484)
