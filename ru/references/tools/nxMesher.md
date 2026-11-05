# nxMesher — карточка инструмента

Встречается в **44** рецептах · 2023-02-14 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Слой эмиттера в **nxMesher**: Resolution 0.02, Radius 0.03–0.04 (0.025 слишком тонко), Surface **Zhu-Bridson**. [▶ 37:52](https://youtu.be/WJwIek6M8z8?t=2272) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- По одному **nxMesher** на эмиттер. Вода: слой эмиттера, Surface **Zhu-Bridson**, Polygon mode **Quads**, Polygon Size поменьше, Radius 0.025. [▶ 16:52](https://youtu.be/jItRyLgdjPg?t=1012) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- Motion blur на мешах с меняющейся топологией: nxMesher ▸ Export ▸ **Transfer Velocity**. [▶ 28:43](https://youtu.be/jItRyLgdjPg?t=1723) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxMesher**: слой эмиттера, polygon size ~0.01, Surface **Zhu-Bridson**, radius ~0.015. [▶ 18:58](https://youtu.be/I9Fq5NPENdc?t=1138) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- NeXus ▸ **Liquid Fill** → домен, nxGravity и папка с эмиттером, **nxFluids**, **nxMesher (выкл.)**, группой «foam» и **nxFoam (выкл.)**. Сразу работает как бак. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Меш: включите **nxMesher** (уже связан; авто polygon size ~0.027); поднимите Scale до **300**, чтобы закрыть дыры; слой Smoothing **Mean Curvature**, iterations **5** (при 10 теряются капли). Export ▸ **Transfer Velocity** для motion blur. [▶ 18:41](https://youtu.be/vglrHSL-uc4?t=1121) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- **nxMesher** ▸ слой Emitter: radius **0.08**, polygon size покрупнее, surface type **Zhu-Bridson** (Spheres подходит для вязкого складывания). [▶ 12:35](https://youtu.be/eeigvIYA19Q?t=755) — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- Motion blur (по желанию — на настоящей макросъёмке его почти не видно): nxMesher ▸ **Export Tags ▸ Transfer Velocity** (здесь max 10) + Motion Blur в Cycles. [▶ 33:35](https://youtu.be/eeigvIYA19Q?t=2015) — *[2026-07-02](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)*
- **nxMesher** ▸ слой эмиттера: **Polygon Size 0.015**, **Radius 0.015**; Surface Type **Zhu-Bridson** (сам сглаживается, быстрый) вместо Spheres. Альтернатива: Radius 0.025 + сглаживание Mean Curvature 100%, 5 итераций (теряется немного деталей). [▶ 12:13](https://youtu.be/na6NGPw4XWM?t=733) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxMesher** ▸ слой эмиттера, wireframe + **Quads**. Проверяйте настройки на сложных кадрах (тонкие рвущиеся нити). **Polygon Size 0.008**, **Radius 0.013** (чуть толще, чтобы сглаживание могло истончить; на 0.012 терялись частицы). [▶ 17:36](https://youtu.be/pz6LDGGeD5A?t=1056) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*
- Мешите через **nxMesher Zhu-Bridson** (гладко без слоёв сглаживания), переносите цвет частиц в vertex color tag; итерации сглаживания смешивают цветовые пятна. [▶ 5:31](https://youtu.be/pbO2aDK4to8?t=331) — *[2026-03-17](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)*
- Кэш (≈1 мин). **nxMesher**: Polygon Size 1.3, радиус 1.6, Smoothing **Mean Curvature** 100%, 5 итераций (сохраняет гребни, убирает плоские участки). **Export Tags ▸ Transfer Color**. [▶ 8:33](https://youtu.be/VCGNxYZt21k?t=513) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxMesher**: radius **0.8**, Polygon Size **0.2** (убирает артефакты на складках); Smoothing **Gaussian** (Influence Range **0.8**, а не дефолтные 5 cm — слишком медленно), strength на максимум; второй слой **Mean Curvature** 5–10 итераций (убирает фасетки/полосы, проверьте, что складки уцелели). **Transfer Color**. [▶ 9:18](https://youtu.be/uadAsfGPo1Y?t=558) — *[2025-12-16](../../recipes/2025-12-16_viscous-folding-ribbon.md)*
- **nxMesher** radius 1.3, Polygon Size 1, **Zhu-Bridson** (гладко без слоёв сглаживания) → материал воды. [▶ 10:12](https://youtu.be/S4Bfw_hb9AI?t=612) — *[2025-12-09](../../recipes/2025-12-09_crown-splash-nxsplash.md)*

## Подводные камни
- В 2026.1 beta в nxMesher добавлены UV advection, сглаживание Detail Aware и nxGroups в качестве источника. — *[2026-08-18](../../recipes/2026-08-18_nxmesher-export-tags.md)*

## Все рецепты (44)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-27 · [Живой лоупольный прокси для симуляции на мокап-персонаже (огонь / коллизии)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-09-22 · [Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-08-18 · [Export-теги nxMesher: ID эмиттеров, цвет частиц, motion blur по velocity (Redshift)](../../recipes/2026-08-18_nxmesher-export-tags.md)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-02 · [Макро-всплеск воды с тонкими плёнками (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-23 · [Пузыри внутри вязкой FLIP-жидкости (поиск соседей)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-12 · [Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-05-26 · [Подводные пузыри от всплеска (адвекция EFX + nxMesher + дымка из частиц)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-03-17 · [Управляемая тягучая струя жидкости (PBD + nxDirection + nxMesher)](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)
- 2026-03-03 · [Завиток мягкого мороженого (nxFluids APIC, вязкость, гравитация с маппингом по возрасту)](../../recipes/2026-03-03_flip-apic-soft-serve-ice-cream.md)
- 2026-02-03 · [Расплавленный шоколад, застывающий при контакте (переменная вязкость APIC по цвету)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-12-16 · [Вязкая складывающаяся лента (FLIP из тонкого вращающегося emitter)](../../recipes/2025-12-16_viscous-folding-ribbon.md)
- 2025-12-09 · [Арт-директорский всплеск-корона (FLIP + хэндлы nxSplash)](../../recipes/2025-12-09_crown-splash-nxsplash.md)
- 2025-12-02 · [Абстрактная жидкость с цветными полосами по числу соседей (поиск соседей в nxColor → mesh → стеклянная рампа)](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)
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
- 2024-05-14 · [Дымчатая жидкость, ползущая по тору (nxFollowGeo с FOV 360° + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-02 · [Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-28 · [Гладкий меш жидкости с сохранением тонких усиков (xpOpenVDBMesher Point Radius, Voxel Size, фильтры Curvature + Offset)](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-09-05 · [Тягучая жидкость в меше с переносом цветов частиц (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-05-09 · [Типы отображения частиц во viewport и их рендер (вкладка Display у эмиттера + генератор Display Render)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
- 2023-02-14 · [Извивающиеся анимированные трейлы, превращённые в сужающиеся трубки (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
