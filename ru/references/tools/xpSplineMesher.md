# xpSplineMesher — карточка инструмента

Встречается в **12** рецептах · 2023-02-14 → 2025-11-06 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpSplineMesher** (X-Particles ▸ Generators): objects = оба edge-сплайна + сплайн SplineFX; Joins выкл, Size **2**. Сгруппировать сплайны в null (Alt+G) и скрыть — риг остаётся процедурным. [▶ 3:09](https://youtu.be/rDSSeIZUl08?t=189) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- **xpSplineMesher** с объектом shortest-path в качестве источника: выключаем **joins**, **size 2**, **subdivisions 2** (круглое сечение вместо квадратного). [▶ 4:35](https://youtu.be/POC6gx3p4rc?t=275) — *[2025-09-18](../../recipes/2025-09-18_meshtools-slime-mold-shortest-path.md)*
- Чтобы рендерить/мешить пружины: **xpTrail ▸ Algorithm: Constraints ▸ Birth Constraints** вкл. → меш через **xpSplineMesher**. [▶ 6:38](https://youtu.be/9w-L9qWwGqQ?t=398) — *[2024-02-27](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)*
- **xpSplineMesher**: Joins выкл., Vertex Colors выкл., spline = mtSplineFX, размер ~1 см, scaling spline сужается в точку на конце; эмиссионный материал. [▶ 1:15](https://youtu.be/sctuPLrOw60?t=75) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- **xpSplineMesher** на трейл: Joints и Vertex Colors выкл., **1 subdivision**, Size **1.5**, сужение к острию графиком **Scale Along Spline**. Трейл скрыть, назначить стеклянный материал. [▶ 3:41](https://youtu.be/M4z3kOU4YEw?t=221) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- **xpSplineMesher** на трейл, vertex colors + joints выключены, size 1.5. **xpCache** (внешние файлы, 90 F); затем отключите управляющий эмиттер и трейл. [▶ 23:17](https://youtu.be/yqfkRKgW1Mo?t=1397) — *[2023-11-16](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)*
- Вариант 2: **xpSplineMesher** по трейлу, радиус ~0.5, **Joins выключить** (Joins нужны для ветвления в духе xpBranch и триангулируют трейлы из констрейнтов). [▶ 15:05](https://youtu.be/WeuXOmENNXA?t=905) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- **xpTurbulence** для извивания. **xpTrail ▸ Algorithm: Tendrils** connections (а не след от birth-частицы). **xpSplineMesher** по трейлу: Subdivision 1, Size ▸ кривая **Scale Spline**, чтобы сузить конец в точку. [▶ 3:11](https://youtu.be/KBktASa5O2o?t=191) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- INSYDIUM ▸ X-Particles ▸ Generators ▸ **xpSplineMesher**: Joins выкл., vertex colors выкл.; привяжите mtShortestPath. Скройте путь, покажите оригинальную модель. [▶ 3:06](https://youtu.be/_03xlveAuZ4?t=186) — *[2023-04-25](../../recipes/2023-04-25_meshtools-shortest-path-growing-veins.md)*
- Generators ▸ **xpSplineMesher**; привяжите xpTrail → простая геометрия вокруг каждого трейла. **Subdivisions** 1–2 → круглые трубки. [▶ 4:06](https://youtu.be/YaFY_HUvnug?t=246) — *[2023-02-14](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)*

## Все рецепты (12)
- 2025-11-06 · [Частицы, разрастающиеся по процедурному проволочному мешу (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-09-18 · [Рост слизевика по бревну (mtRemesh + mtShortestPath + xpSplineMesher)](../../recipes/2025-09-18_meshtools-slime-mold-shortest-path.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-27 · [Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-01-16 · [Процедурная ветвящаяся молния с искрами (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-12-19 · [Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-04-25 · [Процедурно растущие вены на модели (MeshTools Remesh + mtShortestPath + xpSplineMesher)](../../recipes/2023-04-25_meshtools-shortest-path-growing-veins.md)
- 2023-02-14 · [Извивающиеся анимированные трейлы, превращённые в сужающиеся трубки (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
