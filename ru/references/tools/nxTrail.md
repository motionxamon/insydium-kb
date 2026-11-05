# nxTrail — карточка инструмента

Встречается в **19** рецептах · 2023-02-14 → 2026-08-25 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxTrail** ▸ emitter. Вкладка Thickness ▸ Trail Color Mode **Per Vertex Color** (дефолтный Particle Color перекрашивает весь шлейф целиком) → цвет прорисовывается вдоль шлейфа. [▶ 13:33](https://youtu.be/I2ERiN8Vk2Q?t=813) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Рендер: nxTrail Display **Lines → Splines** → автоматически создаются Geometry Nodes (Curve to Mesh) + материал с **атрибутом цвета шлейфа NeXus**; например, подай его в Emission color у Principled. [▶ 13:31](https://youtu.be/I2ERiN8Vk2Q?t=811) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- **nxTrail** ▸ эмиттер ▸ Connections ▸ **Constraints** (вместо траекторий частиц); выключите отображение констрейнтов у эмиттера. [▶ 9:37](https://youtu.be/QDBN_Xu_l68?t=577) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*

## Все рецепты (19)
- 2026-08-25 · [Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-07-14 · [Пружинистая сетка констрейнтов, отрендеренная трейлами (связи nxConstraints Birth + nxTrail в режиме Constraints)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2025-05-20 · [Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2024-12-10 · [Шлейфы, толщина которых следует за радиусом частиц (xpTrail Thickness: Use Radius Variable → кривые Redshift)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-10-01 · [Рендер связей-пружин + стеклянная оболочка под водой (xpTrail Algorithm Constraints, xpOpenVDBMesher, туман Redshift Environment)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-06-04 · [Трейлы с цветом по вершинам, аддитивный рендер в Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-04-23 · [Лазерные лучи от частиц внутри сферы (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-03-12 · [Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2023-12-19 · [Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-02-14 · [Извивающиеся анимированные трейлы, превращённые в сужающиеся трубки (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
