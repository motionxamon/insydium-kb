# nxWind — карточка инструмента

Встречается в **22** рецептах · 2023-06-20 → 2026-08-11 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Движение по желанию: **nxWind** ▸ **Von Karman**, strength ~2.5, побольше вариативности, поднимите Turbulence ▸ Friction Velocity. [▶ 1:36](https://youtu.be/vglrHSL-uc4?t=96) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Любой модификатор ▸ **Groups Affected**: nxWind только на группу 2 (галочка = включить, минус = исключить/инвертировать). [▶ 7:12](https://youtu.be/P9O1SJhPeik?t=432) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **nxWind** в режиме **Von Karman**, диагональное направление, Strength ~3500 с высокой вариацией, турбулентность пониже, добавьте Friction Velocity. [▶ 5:25](https://youtu.be/zyN7ERz7yuw?t=325) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **Вкладка Mapping** у nxWind: Wind Strength ← **Color (Brightness)**, Range Min 0.5 → полная сила на 0.9 → сдуваются только светлые пятна, тёмные остаются. [▶ 6:05](https://youtu.be/zyN7ERz7yuw?t=365) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **nxWind** в режиме von Kármán, strength 800–1200, turbulence выключена; **тег Vibrate** rotation 360° по всем осям, frequency 5; Mapping ▸ Age ступенька 150 → 151 (выключено, затем включено). [▶ 5:46](https://youtu.be/u2MiqeckNaQ?t=346) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **nxWind**, направленный вверх, **Groups Affected = group 2** → сдувает только заражённые частицы. [▶ 4:04](https://youtu.be/xGxf_IIIekY?t=244) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxWind**, **Groups Affected = group 1**, H −95°, P 55°; режим **Von Karman**, strength **625**, **Variation 190%** (>100% даёт часть отрицательных обратных порывов), частота турбулентности 40, Friction Velocity **0.13**. [▶ 14:43](https://youtu.be/V4mwAf8tcLk?t=883) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxWind**; Taiao Plant ▸ Forces ▸ **Direction from Object** = этот ветер, чтобы у дерева и частиц было одно направление. [▶ 3:03](https://youtu.be/zG0XcLByiG4?t=183) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- nxWind: режим **Von Karman**, сильный, turbulence ~50, friction velocity **2.3**; Groups Affected = **group 2**. [▶ 3:20](https://youtu.be/zG0XcLByiG4?t=200) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- **nxWind** и **nxColor** (цвет по направлению) ▸ Groups Affected = **группа 2** — пока ничего не происходит. [▶ 1:54](https://youtu.be/35Yxc9a2QOU?t=114) — *[2025-02-18](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)*
- **nxWind**, повёрнутый по направлению потока, режим **Von Karman**, strength **250**, турбулентность ветра пока выключена. [▶ 0:57](https://youtu.be/bslBFptQSSM?t=57) — *[2024-07-16](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)*
- nxWind ▸ **Mapping ▸ Color Brightness** → **Wind Strength**, диапазон 0 (чёрный) → 1 (белый): на чёрных ветра нет. [▶ 2:50](https://youtu.be/bslBFptQSSM?t=170) — *[2024-07-16](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)*
- **nxWind** направлен вдоль цветка, отображение вентилятора выключено, **strength 2** (частицы крошечные). [▶ 4:39](https://youtu.be/ZgUIL-udXks?t=279) — *[2024-05-28](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)*
- Режим nxWind Standard → **Von Karman** (реалистичные вихри даже на дефолтах). [▶ 1:55](https://youtu.be/RRKxOyJVrO8?t=115) — *[2024-05-07](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)*

## Все рецепты (22)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-06-22 · [Запуск модификаторов переключением групп частиц (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-02 · [Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2026-04-28 · [Заспавненные частицы, которые органично растут и исчезают (кривая nxScale Range + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-02-17 · [Перекраска закэшированных частиц через nxColor (и ограничение скорости по цвету)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-10-16 · [Обзор функций: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-06-10 · [Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-22 · [Отслаивание с поверхности, как у краски (группы nxInfectio + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-04 · [Листья, сорванные ветром с дерева Taiao (листья-эмиттер Taiao + nxWind Von Karman + nxQuestion Field/Random + xpSpin с маппингом на Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2025-02-18 · [Послойное растворение объёма (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2024-07-16 · [Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-05-28 · [Пыльца с кончиков тычинок цветка Taiao (custom object в tiPlant, xpJoin, выделение слоя, nxWind)](../../recipes/2024-05-28_taiao-flower-stamen-pollen-emission.md)
- 2024-05-07 · [Реалистичные листья на порывистом ветру (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-12-12 · [Отслаивание, управляемое заражением (nxInfectio Use Groups + nxWind/nxTurbulence на группе заражённых + разрыв nxConstraints Distance)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-10-31 · [Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-07-03 · [Обзор функций: переработанный nxQuestion и Data Mapping в NeXus (Fused 2023.3)](../../recipes/2023-07-03_feature-notes-nxquestion-data-mapping.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-06-20 · [Распад модели полигон за полигоном под управлением частиц (xpFragmenter Faces Polys, xpWind с linear field, xpTurbulence с маппингом на пройденную дистанцию)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
