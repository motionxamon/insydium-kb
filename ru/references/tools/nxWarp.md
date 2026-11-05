# nxWarp — карточка инструмента

Встречается в **29** рецептах · 2023-02-14 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxWarp Scroll** по размеру так, чтобы охватить все частицы (тяните за хэндлы); Radius 8, Spacing 1, потом увеличьте Radius и Roll; отрицательный Direction. По желанию: масштаб по Y 15–40% для глубины, затем поднимите высоту варпа (по умолчанию 1 cm), чтобы всё влезло. **nxColor** — градиент по Speed. [▶ 10:34](https://youtu.be/WJwIek6M8z8?t=634) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **Поток по трубе (C4D):** Disc-эмиттер r 15 cm, rate 15,000, life 300, + nxTurbulence + nxColor. **nxWarp Bend** повернуть на 90° навстречу потоку, Angle 90°. [▶ 11:17](https://youtu.be/WJwIek6M8z8?t=677) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxWarp Twist** вокруг всей колонны, режим Guide, Angle 500 → 2000 с пониженным Guide Strength; поднимите силу аттрактора, чтобы удержать струю. [▶ 35:40](https://youtu.be/WJwIek6M8z8?t=2140) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*

## Все рецепты (29)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-09-22 · [Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-07-09 · [Дымчатый point cloud, адвектированный взрывом (nxExplosiaFX Particle Advect, Fast-адвекция скорости, силы с привязкой ко времени, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Усики из слоёной curl-турбулентности (слои nxTurbulence Curl + FBM + Voronoi, привязка к возрасту по слоям, ограничение nxSpeed, плавное появление через nxScale)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-25 · [Огонь с горением топлива и дым с живым рендером в Cycles (источники nxExplosiaFX, силы, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-05 · [Аддитивный вихрь частиц, рендер как point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, экспорт Point Cloud)](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)
- 2025-10-28 · [Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-08-14 · [Обзор функций: сплайновые режимы nxFollowGeo, nxUpres по каналам, слои nxSpeed Range](../../recipes/2025-08-14_nxfollowgeo-splines-nxupres-channels-nxspeed-range.md)
- 2025-07-24 · [Обзор функций: слои nxSpin, Noise/Neighbor-градиент в nxColor, Direction Force в nxDirection (превью Fused 2025, часть 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-05-27 · [Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-05-08 · [Лента частиц, обёрнутая вокруг сплайна деформерами C4D (Spline Wrap + Twist на xpEmitter)](../../recipes/2025-05-08_c4d-deformers-twist-spline-wrap-particles.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-02-13 · [Деформация мешей и статичных облаков частиц эффектором MoGraph Random (режим Deformer + список Modifiers у xpEmitter)](../../recipes/2025-02-13_mograph-effector-deformation-particles.md)
- 2024-05-07 · [Реалистичные листья на порывистом ветру (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-04-16 · [Изгибаем прямую симуляцию огня по спирали (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-10-03 · [Частицы, органично текущие вдоль сплайна (слои xpFlowField Along Spline + Curl + To Spline)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-09-27 · [«Живой» shatter-обратный отсчёт (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-08-15 · [Миллионы частиц, адвектируемых дымом, с аддитивным рендером (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-02-14 · [Извивающиеся анимированные трейлы, превращённые в сужающиеся трубки (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
