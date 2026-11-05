# Дым сухого льда, стекающий по логотипу (отрицательная плавучесть nxExplosiaFX)

- Источник: Top Tip Tuesday — Dry Ice — https://www.youtube.com/watch?v=JKU37-9l0_U (2025-11-11)
- Хост / поколение: C4D, Fused 2025.4 beta (nxExplosiaFX)
- Задача: тяжёлый, долго держащийся туман, который стелется по полу и обтекает препятствие.

## Шаги
1. Источники: скрытый **Tube** (брусок сухого льда), **Emit From Volume**, **Smoke 5**, температура по умолчанию, **Fuel 0**, **Pressure 30** (выталкивает дым наружу).
2. **Voxel 2**. Simulation ▸ Buoyancy: **Smoke Buoyancy −20** (оседает после небольшого подъёма от тепла).
3. Solver ▸ Domain Boundary Walls: **закрыть −Y** (пол).
4. Solver ▸ Advection: Velocity и Temperature → **Fast** (быстрее + мягче — то, что нужно для тумана).
5. Dissipation: smoke **~0.2** (держится долго).
6. Colliders: логотип.
7. Dynamics: Turbulence **Voronoi** (любимый у автора), strength ~10, length scale поменьше, **Octaves 0** (только крупные завихрения); **Vorticity ~6** для мелкой детализации (от 10 и выше — пушистая «вата»).
8. **Retiming 50%** = то же движение, вдвое медленнее (слоумо-туман).
9. Вид в отображении: Albedo на полную, отрицательная Scatter Anisotropy → ярче, туманнее.
10. Финал: **Upscaling 1** для тонких прядей; материал Redshift — в файле сцены.
