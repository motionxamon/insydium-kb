# nxEmitter — карточка инструмента

Встречается в **44** рецептах · 2023-03-14 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **2D-сим → 3D-волна (C4D):** nxEmitter сплющен (высота почти 0), стоит у задней стороны варпа; Birth Rate 50,000 (потом 150,000); размер в Display 2; Full Lifespan выкл., Life 100, вариация 20. [▶ 4:32](https://youtu.be/WJwIek6M8z8?t=272) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **FLIP-спираль (Blender):** высокий домен nxFluids FLIP; сферический nxEmitter внизу, **Match Solver Resolution** → FLIP, направление +Z, скорость 2.5; nxColor по Speed; nxTurbulence strength 16. [▶ 30:13](https://youtu.be/WJwIek6M8z8?t=1813) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxEmitter**: Shape Object (зомби), эмиссия из **Volume**, режим сетки **Hexagonal**, Shot, скорость 0. В режиме hexagonal радиус задаёт количество (0.01 → ~13k частиц для тестов). [▶ 1:40](https://youtu.be/-QzOnmifveY?t=100) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- Используйте новый GPU **nxEmitter** из меню NeXus — старый xpEmitter с новыми инструментами не работает. [▶ 1:57](https://youtu.be/UT9_Aht5waE?t=117) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- nxEmitter: Sphere, радиус ~14–17, направление −Y, Rate, скорость 30 см; **Match Solver Resolution** → nxMPM. Добавьте **nxGravity**; длинный таймлайн (8000 F). [▶ 3:36](https://youtu.be/UT9_Aht5waE?t=216) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- Второй **nxEmitter** «brittle»: Box 50×50×50, −Y, скорость 30, Shot примерно на F220, Match Solver Resolution → тот же MPM. Остановите эмиттер песка (Emit All Frames выкл., ~200 кадров). [▶ 15:15](https://youtu.be/UT9_Aht5waE?t=915) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (автоматический радиус + упаковка по сетке). Emission **Shot** для одного сгустка. [▶ 2:35](https://youtu.be/jItRyLgdjPg?t=155) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxEmitter**: Shape **Disc**, направление **+Z**, Birth Rate **10,000**; размер точек на дисплее 2 (только отображение). [▶ 1:21](https://youtu.be/I9Fq5NPENdc?t=81) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- Плоскость пола + тор (оба скрыты). **Sand nxEmitter**: Object ▸ тор, **Volume**, **Shot**, **Hexagonal**, Speed 0; Display Spheres, Gradient по **Granular**, Auto Scale выкл, 0–20. [▶ 0:52](https://youtu.be/yp5579on6J8?t=52) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **Water nxEmitter**: Sphere, радиус 0.2, размещён вдоль Y; **Rate** + режим Hex; направление **−Y**, скорость **3.5**. **Radius 0.015 — должен совпадать с песком**; разные радиусы заставляют SPH взрываться. [▶ 4:20](https://youtu.be/yp5579on6J8?t=260) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **nxEmitter**: **Disc**, только Edges, Angle **90°**, **Shot** из 200 (2,000 для финала), Speed **2.5**, вариация **1** (диапазон 1.5–3.5 m/s). [▶ 0:34](https://youtu.be/I2ERiN8Vk2Q?t=34) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Сюзанна (Subdivision 2, применён), поднята и повёрнута. **nxEmitter**: Object, **Volume**, **Shot**, **Hexagonal**, Speed 0. Display Spheres показывает реальную упаковку; радиус **0.01 m** для большего количества гранул (в продакшене: 3–4 M+). [▶ 2:14](https://youtu.be/rkuNbceXolQ?t=134) — *[2026-07-28](../../recipes/2026-07-28_sph-granular-clumping-sand.md)*
- **nxEmitter**: широкий/высокий прямоугольник, **Shot** ~700, Speed 0; Display **Circle Filled**. [▶ 0:33](https://youtu.be/QDBN_Xu_l68?t=33) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*
- **nxEmitter** Sphere, радиус **0.2**, направление **−Z**, Rate случайно **50,000/s**, радиус частиц **0.01**, эмиссия **120 кадров**. Bezier circle повёрнут по X лицом к камере; эмиттер на его краю. [▶ 0:38](https://youtu.be/na6NGPw4XWM?t=38) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*

## Все рецепты (44)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-21 · [Идущий персонаж рассыпается в песок (nxBind + отрыв по фоллоффу + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-10-20 · [Распад объёма частиц снаружи внутрь (nxQuestion Neighbors → Set Group, силы с маппингом по скорости)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-10-11 · [Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-22 · [Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-09-08 · [Струя воды размывает комковатый песок (nxFluids SPH Granular + жидкость в Mixer, цвет nxBlend → mapped-настройки granular)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-25 · [Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-28 · [Слипающийся песок / снег через SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-07-14 · [Пружинистая сетка констрейнтов, отрендеренная трейлами (связи nxConstraints Birth + nxTrail в режиме Constraints)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2026-07-09 · [Дымчатый point cloud, адвектированный взрывом (nxExplosiaFX Particle Advect, Fast-адвекция скорости, силы с привязкой ко времени, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Усики из слоёной curl-турбулентности (слои nxTurbulence Curl + FBM + Voronoi, привязка к возрасту по слоям, ограничение nxSpeed, плавное появление через nxScale)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-07-02 · [Макро-всплеск воды с тонкими плёнками (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-29 · [Основы Data Mapping: гравитация по возрасту/радиусу/яркости, циклические импульсы fuel/smoke в EFX (вкладка Mapping, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-22 · [Запуск модификаторов переключением групп частиц (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-15 · [Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-12 · [Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-06-08 · [Анимация размера частиц через слой Range и его ease-кривую (nxScale Range)](../../recipes/2026-06-08_blender-nxscale-range-ease-curve.md)
- 2026-06-05 · [Аддитивный вихрь частиц, рендер как point cloud (nxEmitter Disc Edge Only, nxTurbulence, nxRotate + Sphere falloff, экспорт Point Cloud)](../../recipes/2026-06-05_blender-additive-particle-vortex-point-cloud.md)
- 2025-08-12 · [Чистая эмиссия частиц с mocap-персонажа (xpJoin → Alembic → запекание PLA)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-08-07 · [Процедурный плазменный шар (nxFollowGeo + nxTurbulence на частицах, дуги mtSplineFX, ответвления от пересечений mtEdgeSpline)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-07-22 · [Прячем жёсткое кольцо эмиссии шумной маской прозрачности (слои nxColor + сплайн birth rate)](../../recipes/2025-07-22_nxcolor-noise-opacity-emission-fade.md)
- 2025-04-29 · [Объёмное облако частиц, окрашенное UV-текстурой объекта (эмиттер с поверхности по текстуре + nxUpres Color + Initial State)](../../recipes/2025-04-29_textured-particle-volume-nxupres-color.md)
- 2025-04-01 · [Как спрятать гексагональную сетку в сыпучих симуляциях (Jitter эмиттера + nxPush на один кадр + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2024-12-31 · [Искры фейерверка от рукописного текста (nxScale + убийство через nxQuestion + ограничение nxSpeed, замапленное на Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-06-04 · [Трейлы с цветом по вершинам, аддитивный рендер в Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-05-02 · [Обзор функций: mtPointProject и новые режимы mtSubdivider (MeshTools 2024.2)](../../recipes/2024-05-02_feature-notes-mtpointproject-mtsubdivider-modes.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-04-23 · [Лазерные лучи от частиц внутри сферы (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-09-12 · [Запуск сима жидкости переносом частиц в новую группу (nxQuestion Field + Random math, Set Group)](../../recipes/2023-09-12_nxquestion-field-group-switch-random.md)
- 2023-05-09 · [Типы отображения частиц во viewport и их рендер (вкладка Display у эмиттера + генератор Display Render)](../../recipes/2023-05-09_particle-display-modes-display-render.md)
- 2023-04-17 · [Взрывающаяся планета: детальные частицы на поверхности, вращающиеся вместе со сферой (эмиссия с текстуры на смещённой геометрии, Global Transform, отступ по цвету)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Взрывающаяся планета: эмиссия с текстуры, зависящая от скорости вращения, и слипающиеся обломки (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-03-28 · [Эмиссия только с самых быстро движущихся частей меша (слой Vertex Speed в xpVertexMap + эмиссия по текстуре)](../../recipes/2023-03-28_vertex-speed-emission-xpvertexmap.md)
- 2023-03-16 · [Песочный logo reveal, где симулируются только «геройские» гранулы (nxFluids SPH Granular + статичный разброс по vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-14 · [Частицы, наследующие движение объекта-эмиттера (Motion Inheritance linear + rotational, xpTurbulence)](../../recipes/2023-03-14_motion-inheritance-linear-rotational.md)
