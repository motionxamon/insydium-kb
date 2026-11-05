# nxFluids — карточка инструмента

Встречается в **73** рецептах · 2023-03-07 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **FLIP-спираль (Blender):** высокий домен nxFluids FLIP; сферический nxEmitter внизу, **Match Solver Resolution** → FLIP, направление +Z, скорость 2.5; nxColor по Speed; nxTurbulence strength 16. [▶ 30:13](https://youtu.be/WJwIek6M8z8?t=1813) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxFluids** ▸ SPH ▸ Fluid Type **Granular**; Substeps: **Adaptive выключен**, **20**; Granular Friction **~70**. [▶ 3:55](https://youtu.be/M2yxZlZQBec?t=235) — *[2026-10-06](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)*
- **nxFluids PBD**: поднимите Smoothing Radius (~110), добавьте External Pressure и немного Repulsion для тягучих нитей; радиус частиц эмиттера **0.01 m**. [▶ 13:59](https://youtu.be/I9Fq5NPENdc?t=839) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- **nxFluids** ▸ **SPH** (нужен, чтобы смешивать granular + жидкость), основной Fluid Type **Granular** — песок настраивается в главной панели, жидкость в Mixer. Substeps **Adaptive выкл, 15**; Friction **100**. [▶ 2:42](https://youtu.be/yp5579on6J8?t=162) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- nxFluids ▸ **Mixer** ▸ добавьте эмиттер воды как **Liquid**. Включите **Check Density**, чтобы убивать слишком плотные рождения (убирает взрывной старт). [▶ 5:42](https://youtu.be/yp5579on6J8?t=342) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- nxFluids ▸ **Mapping** ▸ три карты **Color Brightness** → **Friction**, **Stability**, **Cohesion**, кривые инвертированы (чёрный = полное значение, белый ≈ 0), чтобы мокрые песчинки крошились и смывались. [▶ 13:25](https://youtu.be/yp5579on6J8?t=805) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- NeXus ▸ **Liquid Fill** → домен, nxGravity и папка с эмиттером, **nxFluids**, **nxMesher (выкл.)**, группой «foam» и **nxFoam (выкл.)**. Сразу работает как бак. [▶ 0:59](https://youtu.be/vglrHSL-uc4?t=59) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Эмиттер: Object = домен, Volume, Emission Type **Liquid Fill**, ссылается на солвер nxFluids; **Resolution** (50 → 70/75) и **Fill Level** (30%, Show Fill Level). Resolution задаёт размер вокселя солвера **и** количество частиц, чтобы число частиц на воксель оставалось правильным (при неверном соотношении жидкость схлопывается). Проверяйте через nxFluids Display ▸ voxel grid Back Only. [▶ 4:31](https://youtu.be/vglrHSL-uc4?t=271) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Тип солвера связан: переключение эмиттера на **APIC** переводит в APIC и nxFluids. [▶ 7:19](https://youtu.be/vglrHSL-uc4?t=439) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- **nxFluids** ▸ **SPH** ▸ Fluid Type **Granular** → сухой песок. Display Gradient по **Granular**, Auto Scale выкл., 0–20. [▶ 4:02](https://youtu.be/rkuNbceXolQ?t=242) — *[2026-07-28](../../recipes/2026-07-28_sph-granular-clumping-sand.md)*
- **nxFluids** солвер **PBD** (лучше всех справляется с сильными, нереалистичными силами). Вздутие при рождении = слишком плотно → включите проверку **Density** (убивает частицы, рождённые выше порога плотности). [▶ 3:19](https://youtu.be/na6NGPw4XWM?t=199) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*
- **nxFluids**, solver **APIC** (FLIP/APIC — voxel-солверы с границами; PBD без границ). Автор выбирает APIC для очень вязких жидкостей. Плотно сожмите bounds вокруг действия (меньше voxel). Display ▸ draw grid (только задние) — чтобы видеть voxel; отображение пола выключите. [▶ 1:33](https://youtu.be/pz6LDGGeD5A?t=93) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*
- nxFluids **Voxel size 0.02** для точности. [▶ 11:02](https://youtu.be/pz6LDGGeD5A?t=662) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*
- **nxFluids SPH → Granular**; Substeps **30, adaptive выкл.**; Friction ~50, Stability ~3 (для мелких частиц поднимите до ~6), Cohesion ~7. Добавьте **nxGravity**. [▶ 4:08](https://youtu.be/zyN7ERz7yuw?t=248) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*

## Подводные камни
- Смешивание в SPH: у всех частиц один радиус и один объект nxFluids. — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*

## Все рецепты (73)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-11 · [Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-22 · [Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-09-08 · [Струя воды размывает комковатый песок (nxFluids SPH Granular + жидкость в Mixer, цвет nxBlend → mapped-настройки granular)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-28 · [Слипающийся песок / снег через SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-07-02 · [Макро-всплеск воды с тонкими плёнками (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-23 · [Пузыри внутри вязкой FLIP-жидкости (поиск соседей)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2026-06-12 · [Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-06-02 · [Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2026-03-17 · [Управляемая тягучая струя жидкости (PBD + nxDirection + nxMesher)](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)
- 2026-03-03 · [Завиток мягкого мороженого (nxFluids APIC, вязкость, гравитация с маппингом по возрасту)](../../recipes/2026-03-03_flip-apic-soft-serve-ice-cream.md)
- 2026-02-17 · [Перекраска закэшированных частиц через nxColor (и ограничение скорости по цвету)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2026-02-03 · [Расплавленный шоколад, застывающий при контакте (переменная вязкость APIC по цвету)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2026-01-06 · [Вода, налипающая на объект, поднимающийся из FLIP-бассейна (nxSticky)](../../recipes/2026-01-06_sticky-flip-object-rising.md)
- 2025-12-16 · [Вязкая складывающаяся лента (FLIP из тонкого вращающегося emitter)](../../recipes/2025-12-16_viscous-folding-ribbon.md)
- 2025-12-09 · [Арт-директорский всплеск-корона (FLIP + хэндлы nxSplash)](../../recipes/2025-12-09_crown-splash-nxsplash.md)
- 2025-12-02 · [Абстрактная жидкость с цветными полосами по числу соседей (поиск соседей в nxColor → mesh → стеклянная рампа)](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-11-18 · [Тягучая жидкость, кружащая вокруг нескольких сплайнов (nxFollowGeo в режиме Force + PBD)](../../recipes/2025-11-18_nxfollowgeo-spline-flow-pbd.md)
- 2025-10-28 · [Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-09-23 · [Смешивание краски из трёх цветных эмиттеров (nxBlend + маппинг по скорости)](../../recipes/2025-09-23_paint-mix-nxblend.md)
- 2025-09-16 · [Тянущиеся и рвущиеся волокна (nxConstraints Birth + трейлы по констрейнтам + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-09-09 · [Горячая текучая / холодная тягучая жидкость, которая снова плавится при контакте (группы + nxBlend + mapping вязкости)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-08-05 · [Три тягучие жидкости с тремя вязкостями (группы + nxConstraints Viscosity с mapping по Group)](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)
- 2025-07-24 · [Обзор функций: слои nxSpin, Noise/Neighbor-градиент в nxColor, Direction Force в nxDirection (превью Fused 2025, часть 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-07-15 · [Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-07-08 · [Бесконечная река / поток жидкости (открытый с одной стороны контейнер + эмиттер подпитки + nxKill)](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)
- 2025-06-10 · [Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-14 · [Вода размывает снежную скульптуру (nxFluids SPH granular + liquid tag, nxGravity с маппингом по Age, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-15 · [Upres гранулярной симуляции с сохранением формы (кэш в низком разрешении + смешивание velocity через nxUpres)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2025-04-01 · [Как спрятать гексагональную сетку в сыпучих симуляциях (Jitter эмиттера + nxPush на один кадр + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2025-03-27 · [Больше частиц в жидкость без взрыва давления (nxFluids Check Density / Max Density)](../../recipes/2025-03-27_nxfluids-check-density-max-density.md)
- 2025-03-25 · [Песок + вода в одной симуляции (nxFluids SPH Granular + тег nxFluids на эмиттере, stability через age)](../../recipes/2025-03-25_sand-and-water-granular-liquid-mix.md)
- 2025-02-27 · [Пристыкованные палитры для инструментов INSYDIUM (C4D Command Manager, отрывные подменю, Lock Icon)](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)
- 2025-01-21 · [Motion blur на замешенной жидкости в Redshift (xpOpenVDBMesher Transfer Velocity → motion vectors в Redshift Object tag)](../../recipes/2025-01-21_volume-mesh-motion-blur-redshift.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-16 · [Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-06-11 · [Статуя рассыпается в песок по мере распространения заражения (группы nxInfectio + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2024-05-14 · [Дымчатая жидкость, ползущая по тору (nxFollowGeo с FOV 360° + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-25 · [Обзор функций: перестроенное ядро NeXus 2024.2 — быстрее на GPU и коллизии с анимированной геометрией](../../recipes/2024-04-25_feature-notes-nexus-2024-2-speed-collisions.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-04-02 · [Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-03-19 · [Неспокойная, закручивающаяся вода (nxVorticity на PBD и SPH)](../../recipes/2024-03-19_nxvorticity-choppy-water.md)
- 2024-03-05 · [Смешивание густых красок (nxFluids SPH + nxConstraints Viscosity + nxBlend)](../../recipes/2024-03-05_nxblend-paint-mix.md)
- 2024-02-20 · [Слои жидкостей разной плотности (density в nxFluids tag для SPH / радиус для PBD)](../../recipes/2024-02-20_nxfluids-mixed-density.md)
- 2024-01-09 · [Живые частицы как точки, управляющие Displacer (XP Editing + C4D Fields Delay)](../../recipes/2024-01-09_xp-editing-particles-drive-deformers.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-28 · [Гладкий меш жидкости с сохранением тонких усиков (xpOpenVDBMesher Point Radius, Voxel Size, фильтры Curvature + Offset)](../../recipes/2023-11-28_openvdb-mesher-detail-filters.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-07 · [Плавающий / тонущий объект в жидкости NeXus (тег xpDynamics + плотность в nxFluids tag на эмиттер)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-10-31 · [Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-10-17 · [Динамическая карта намокания там, где жидкость бьёт в стену (слой X-Particles в xpVertexMap, Fade then Add)](../../recipes/2023-10-17_xpvertexmap-fluid-wet-map.md)
- 2023-09-12 · [Запуск сима жидкости переносом частиц в новую группу (nxQuestion Field + Random math, Set Group)](../../recipes/2023-09-12_nxquestion-field-group-switch-random.md)
- 2023-09-05 · [Тягучая жидкость в меше с переносом цветов частиц (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-07-05 · [Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-07-03 · [Обзор функций: переработанный nxQuestion и Data Mapping в NeXus (Fused 2023.3)](../../recipes/2023-07-03_feature-notes-nxquestion-data-mapping.md)
- 2023-06-12 · [Быстрая вязкая струя шоколада/мёда (xpFluidPBD + xpConstraints Viscosity, эмиссия Hexagonal)](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-16 · [Песочный logo reveal, где симулируются только «геройские» гранулы (nxFluids SPH Granular + статичный разброс по vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-07 · [Снежная скульптура, которая рассыпается (гексагональная упаковка в режиме Shot + nxFluids SPH Granular: friction, substeps, stability, cohesion)](../../recipes/2023-03-07_nexus-sph-granular-snow-sculpture.md)
