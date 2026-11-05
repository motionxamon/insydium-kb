# xpOpenVDBMesher — карточка инструмента

Встречается в **21** рецептах · 2023-03-29 → 2026-10-27 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpOpenVDBMesher** с копией в качестве дочернего → voxel size ~3 для замкнутой оболочки; поднимите **Iso value**, чтобы тонкие части (кисти) не пропали. Сделайте редактируемым (C). [▶ 8:24](https://youtu.be/C0P7UtWroDo?t=504) — *[2026-10-27](../../recipes/2026-10-27_mocap-sim-proxy.md)*
- **xpOpenVDBMesher** со всеми тремя эмиттерами. Для цвета вершин нужен плотный меш → **Voxel Size 1**; **Point Radius 2** (менее пузырчато). [▶ 1:44](https://youtu.be/oHF1dIMGtUs?t=104) — *[2025-09-30](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)*
- **xpOpenVDBMesher** с 3 эмиттерами; **Voxel 1.5**; **Point Radius 4** (по умолчанию 10 = ×10 радиуса частиц, слишком комковато). [▶ 1:22](https://youtu.be/e49Ob7tPXfc?t=82) — *[2025-09-02](../../recipes/2025-09-02_openvdb-mesher-object-ids.md)*
- **xpOpenVDBMesher granular**: Voxel size **0.5**, Point Radius **1.9** (дефолтные 10× дают раздутость), Filters: удалите Median, добавьте **Curvature**, iterations **2** (остальное спрячет SSS). [▶ 42:43](https://youtu.be/Siw3tkJepaU?t=2563) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- **xpOpenVDBMesher liquid** (дубликат): Voxel **0.6**, Point Radius ~**2**, Curvature **10** iterations. Если брызги пропадают — уменьшите вокселы или увеличьте Point Radius. [▶ 47:53](https://youtu.be/Siw3tkJepaU?t=2873) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- Снег: **xpOpenVDBMesher**, связанный с кэшем: Voxel Size **4 → 0.5**, Point Radius **10 → 1.9**; Filters ▸ удалить Median, добавить **Curvature** (Strength 100, Iterations 2) — сохраняет трещины, лёгкая шероховатость помогает SSS. Кэшировать mesher через **Build Cache ▸ Continue** (~10 мин), затем выключить эмиттер. [▶ 32:52](https://youtu.be/fxJI8py9BzU?t=1972) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- **xpOpenVDBMesher** с эмиттером: по умолчанию **Point Radius 10 = 10 × радиус частицы** (сферы 30 cm). [▶ 1:17](https://youtu.be/-4wYDCnis9M?t=77) — *[2024-11-05](../../recipes/2024-11-05_openvdb-velocity-stretch-trails.md)*
- **xpOpenVDBMesher** на spawn-эмиттере: Voxel Size **3**, Point Radius **2**, **Filters** включены (по умолчанию). [▶ 3:25](https://youtu.be/jHu6mpJfEUQ?t=205) — *[2024-10-01](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)*
- **xpOpenVDBMesher**: источник — эмиттер, **Voxel size 1**, **Point Radius 3**, один фильтр **Curvature**, Iterations 4. [▶ 4:58](https://youtu.be/DCggkQ6Mu_w?t=298) — *[2024-04-02](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)*
- Лоупольный дамми: **xpOpenVDBMesher** с xpJoin; в записи объекта поставьте режим меша **Surface → Points**; **Voxel size 6**; фильтры: удалите Median по умолчанию, добавьте **Curvature** (несколько итераций) + **Offset** (сжимайте, пока настоящая машина не начнёт чуть проступать). **C** — сделать редактируемым, назовите «dummy car», скройте. [▶ 1:22](https://youtu.be/BGuwXsKofbo?t=82) — *[2024-03-26](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)*
- **xpOpenVDBMesher**, General ▸ перетащите закэшированный эмиттер. По умолчанию результат «пузырчатый»: **Point Radius 10 = оболочка 10 × радиус частицы**. [▶ 2:05](https://youtu.be/vbolWCL3KgY?t=125) — *[2023-11-28](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)*
- Generators ▸ **xpOpenVDBMesher**, перетащите xpEmitter в его список. Voxel size **3** для большего числа полигонов. [▶ 2:09](https://youtu.be/fvS3h7uk35s?t=129) — *[2023-09-05](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)*
- Вариант 3 (органичный, вязкий вид): **xpOpenVDBMesher** с Spline Mesher в качестве source; уменьшить Voxel Size и увеличить радиус Spline Mesher, чтобы было достаточно объёма для меширования. [▶ 16:28](https://youtu.be/WeuXOmENNXA?t=988) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- Меш: **xpOpenVDBMesher**, source = эмиттер; увеличить Voxel Size, уменьшить Point Radius, добавить фильтры сглаживания **Gaussian**. [▶ 20:26](https://youtu.be/dnyn6Lrj8-A?t=1226) — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*

## Все рецепты (21)
- 2026-10-27 · [Живой лоупольный прокси для симуляции на мокап-персонаже (огонь / коллизии)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-09-30 · [Меширование симуляции смешивания красок и рендер цвета вершин (xpOpenVDBMesher → Redshift)](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)
- 2025-09-02 · [Один меш — свой материал для каждого эмиттера (xpOpenVDBMesher Object IDs → Redshift)](../../recipes/2025-09-02_openvdb-mesher-object-ids.md)
- 2025-06-17 · [Скрытый логотип, видимый только в преломлениях жидкости (Redshift primary ray выкл. + material blender с лавой)](../../recipes/2025-06-17_fluid-mesh-reveal-secondary-rays.md)
- 2025-05-14 · [Вода размывает снежную скульптуру (nxFluids SPH granular + liquid tag, nxGravity с маппингом по Age, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-22 · [Вид микроклеток в Redshift (светящиеся сферы с Fresnel-прозрачностью внутри стеклянного меша с дисперсией)](../../recipes/2025-04-22_redshift-cellular-particles-fresnel-dispersion.md)
- 2025-01-21 · [Motion blur на замешенной жидкости в Redshift (xpOpenVDBMesher Transfer Velocity → motion vectors в Redshift Object tag)](../../recipes/2025-01-21_volume-mesh-motion-blur-redshift.md)
- 2024-11-05 · [Меши, вытянутые по скорости, и цвет вершин (xpOpenVDBMesher Point Radius, Transfer Velocity, источник Trails)](../../recipes/2024-11-05_openvdb-velocity-stretch-trails.md)
- 2024-10-29 · [Рампа замедления на мешированной жидкости (ретайм кэша частиц, затем кэш мешера из ретаймленных частиц)](../../recipes/2024-10-29_retime-cached-meshes.md)
- 2024-10-01 · [Рендер связей-пружин + стеклянная оболочка под водой (xpTrail Algorithm Constraints, xpOpenVDBMesher, туман Redshift Environment)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-04-02 · [Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-11-28 · [Гладкий меш жидкости с сохранением тонких усиков (xpOpenVDBMesher Point Radius, Voxel Size, фильтры Curvature + Offset)](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)
- 2023-09-05 · [Тягучая жидкость в меше с переносом цветов частиц (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
