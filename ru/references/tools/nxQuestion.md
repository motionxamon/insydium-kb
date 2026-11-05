# nxQuestion — карточка инструмента

Встречается в **55** рецептах · 2023-03-21 → 2026-10-20 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxQuestion** ▸ вопрос **Neighbors**: дистанция поиска **0.1** (при 0.05 каждая частица считается поверхностной), **less than 30**, variation 7. Сначала протестируйте с action Set Color (жёлтый) — подсветиться должна только внешняя оболочка. [▶ 6:14](https://youtu.be/yOPa8oM_KXE?t=374) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- Финал: вытащите последнюю точку кривой за пределы домена; в flow field ▸ **Flag on Escape**; **nxQuestion**: если флаг Escaped → Action **Kill Particle** (или задайте короткий lifespan с вариацией). [▶ 17:02](https://youtu.be/I9Fq5NPENdc?t=1022) — *[2026-09-22](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)*
- Пусть частицы гаснут вместе с пламенем, а не по фиксированному lifespan: **nxQuestion** — Question *Age > 2 frames* (запас: у новорождённых частиц температура 0) **AND** дочерний Question *Temperature < 1000* → **Action Kill**. [▶ 7:31](https://youtu.be/1ERTCdQAoF0?t=451) — *[2026-09-01](../../recipes/2026-09-01_efx-advection-data-questions.md)*
- **nxQuestion** ▸ слой Question: категория Particle, **Age > 45** → дочерний **Action** (по умолчанию Set Color жёлтым для проверки) → переключите на **Set Group = group 2**. Размойте порог: **Age 55, variation 20**. [▶ 9:17](https://youtu.be/P9O1SJhPeik?t=557) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **nxQuestion**: — *[2026-05-05](../../recipes/2026-05-05_random-groups-scale-mapping.md)*
- Короткоживущие частицы «source», прилипшие к веткам → действие **Spawn** в nxQuestion без вопроса = непрерывный спавн во второй эмиттер. [▶ 2:32](https://youtu.be/THuXYZmNZjQ?t=152) — *[2026-04-28](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)*
- Цвет = температура: **nxQuestion** `Document ▸ Object Distance (mode Polygons, object = cube) < 3 cm → Set Color white` с **уменьшенным Weight** (плавно уходит в белый = постепенно остывает). [▶ 2:58](https://youtu.be/VCGNxYZt21k?t=178) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxQuestion**: Age > 0 → Action **Set Radius 5** (позже **3**), Weight ≈ **10%**, чтобы радиус нарастал плавно. [▶ 6:50](https://youtu.be/rDSSeIZUl08?t=410) — *[2025-11-06](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)*
- nxQuestion: `Particle ▸ Neighbors (40 cm) > 420` → только частицы в швах (они видят точки двух поверхностей). Число подбирайте опытным путём (300 = почти все, 400–420 = только швы). [▶ 2:30](https://youtu.be/Xe1seJC3g0k?t=150) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- Ограничение полем: добавьте Sphere field на **вкладку Fields в nxQuestion** (оно обязательно должно быть в списке!), затем `If Field > 0.5` (внутренний falloff) **AND** дочернее условие `Neighbors > 420` → actions. [▶ 3:04](https://youtu.be/Xe1seJC3g0k?t=184) — *[2025-11-04](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)*
- **nxQuestion**: `Color Brightness < 0.1 → Set Radius 0` (низкий weight = плавное уменьшение) / `> 0.7 → Set Radius 26` (низкий weight). [▶ 2:33](https://youtu.be/PTamR793O-k?t=153) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- nxQuestion: — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- **nxQuestion** → действие **Set Color чёрный** с **Weight ~7%** → плавное затухание вместо мгновенного переключения. [▶ 1:28](https://youtu.be/1ISE9D2bmeQ?t=88) — *[2025-08-19](../../recipes/2025-08-19_nxquestion-neighbors-field-sand-mask.md)*
- **nxQuestion** со **Spherical field**: `Field > 0.7 → Add to Radius` (большое значение, **низкий weight** = медленный рост); `Field < 0.3 → Set Radius 1` (низкий weight). [▶ 3:38](https://youtu.be/v63KTwt6pI4?t=218) — *[2025-06-24](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)*

## Подводные камни
- Свойства частиц группы (цвет, скорость…) применяются **только при рождении**; nxQuestion Set Group меняет лишь ID группы. — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- Порядок важен: nxColor → nxQuestion (группа) → силы → speed-clamp question последним; push перед kill. — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*

## Все рецепты (55)
- 2026-10-20 · [Распад объёма частиц снаружи внутрь (nxQuestion Neighbors → Set Group, силы с маппингом по скорости)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-09-22 · [Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)](../../recipes/2026-09-22_flowfield-fluid-along-spiral.md)
- 2026-09-15 · [Рендер данных частиц NeXus в Octane (цвет, радиус → стекло)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-09-01 · [Частицы-языки пламени по данным адвекции nxExplosiaFX (kill и цвет по температуре)](../../recipes/2026-09-01_efx-advection-data-questions.md)
- 2026-06-30 · [Запуск/остановка зацикленной анимации nxQuestion через action Break](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-23 · [Пузыри внутри вязкой FLIP-жидкости (поиск соседей)](../../recipes/2026-06-23_viscous-bubble-rig.md)
- 2026-06-22 · [Запуск модификаторов переключением групп частиц (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-09 · [Случайная ориентация при рождении + повторяемые обороты на 360° (nxSpin + сброс возраста)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-05-19 · [Пульсация скорости / размера частиц через nxQuestion Math ▸ Wave](../../recipes/2026-05-19_nxquestion-sine-wave-pulsing.md)
- 2026-05-05 · [Немного крупных, много мелких: случайные подгруппы + nxScale с маппингом по группе](../../recipes/2026-05-05_random-groups-scale-mapping.md)
- 2026-04-28 · [Заспавненные частицы, которые органично растут и исчезают (кривая nxScale Range + kill)](../../recipes/2026-04-28_nxscale-range-spawn-fade.md)
- 2026-04-14 · [Зацикленные цветовые волны, запускаемые касанием (переключатель-переменная в nxQuestion + nxBlend)](../../recipes/2026-04-14_nxquestion-looping-switch-color-waves.md)
- 2026-02-24 · [Убивать частицы по пройденному расстоянию (сброс age в nxQuestion + Set Life)](../../recipes/2026-02-24_custom-lifespan-by-distance.md)
- 2026-02-03 · [Расплавленный шоколад, застывающий при контакте (переменная вязкость APIC по цвету)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-11-06 · [Частицы, разрастающиеся по процедурному проволочному мешу (mtEdgeSpline, mtSplineFX, xpSplineMesher, xpVertexMap Seed, nxQuestion Set Radius, nxPush)](../../recipes/2025-11-06_wired-growth-spline-mesh-vertex-map.md)
- 2025-11-04 · [Частицы, распускающиеся в щелях геометрии (соседи в nxQuestion + поле)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-16 · [Обзор функций: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-09-09 · [Горячая текучая / холодная тягучая жидкость, которая снова плавится при контакте (группы + nxBlend + mapping вязкости)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-08-19 · [Динамическая ч/б маска на симуляции песка → смешивание материалов в Redshift (nxQuestion: Field AND Neighbors, Else)](../../recipes/2025-08-19_nxquestion-neighbors-field-sand-mask.md)
- 2025-07-03 · [Обзор функций: слоёный nxTurbulence, nxScale и новый nxLimit (превью Fused 2025, часть 1)](../../recipes/2025-07-03_feature-notes-layered-nxturbulence-nxscale-nxlimit.md)
- 2025-06-24 · [Самоподдерживающийся цикл частиц: рост / расталкивание / уменьшение (nxAttract + nxPush + поле в nxQuestion + nxRotate через mapping)](../../recipes/2025-06-24_self-sustaining-push-grow-cycle.md)
- 2025-05-27 · [Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-05-20 · [Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-04 · [Листья, сорванные ветром с дерева Taiao (листья-эмиттер Taiao + nxWind Von Karman + nxQuestion Field/Random + xpSpin с маппингом на Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2025-02-18 · [Послойное растворение объёма (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2025-01-14 · [Случайное растворение по полю (nxQuestion Field + Group + Math Random)](../../recipes/2025-01-14_nxquestion-random-math-dissolve.md)
- 2024-12-31 · [Искры фейерверка от рукописного текста (nxScale + убийство через nxQuestion + ограничение nxSpeed, замапленное на Radius)](../../recipes/2024-12-31_spline-particle-sparks-radius-speed-limit.md)
- 2024-12-17 · [Распад / проявление текста (nxQuestion field → смена группы → сброс возраста → задать lifespan)](../../recipes/2024-12-17_particle-reveal-field-group-switch.md)
- 2024-10-04 · [Органический рост складок, ползущий по статуе (отталкивание в nxConstraints Forces + xpDeformer, группы nxQuestion по vertex map)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-09-17 · [Непересекающиеся ветки из частиц внутри меша (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-08-27 · [Самопрорастающие усики по полю (nxQuestion Variable + Spawn + Set Age/Life, nxPush по радиусу)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-04-09 · [Психоделические плоские паттерны расталкивания (nxPush + фиксация скорости через nxQuestion + nxScale по полю)](../../recipes/2024-04-09_nxpush-2d-radius-animation.md)
- 2024-02-13 · [Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-10-31 · [Удаляем лишнюю пену за пределами контейнера произвольной формы (nxKill + инверсия Volume поля / nxQuestion Document Object Distance)](../../recipes/2023-10-31_nxkill-custom-volume-bounds-foam.md)
- 2023-10-24 · [Рост с разной скоростью, уменьшение с возрастом, затем смерть (nxScale Clamp within Range + Age map на Upper Radius Limit + kill через nxQuestion)](../../recipes/2023-10-24_nxscale-random-growth-age-mapped-shrink.md)
- 2023-09-27 · [Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-09-12 · [Запуск сима жидкости переносом частиц в новую группу (nxQuestion Field + Random math, Set Group)](../../recipes/2023-09-12_nxquestion-field-group-switch-random.md)
- 2023-08-29 · [Частицы растут и меняют цвет внутри поля, а снаружи возвращаются обратно (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-08-22 · [Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-07-05 · [Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-07-05 · [Рекурсивный рост по полю через спавн в nxQuestion (nxQuestion Neighbors + Spawn, nxPush, nxTurbulence с mapping)](../../recipes/2023-07-05_nxquestion-recursive-growth-rig-part-a.md)
- 2023-07-05 · [Электрические дуги, кабели и искры от лазерного прожига (mtSplineFX + mtRayline + nxQuestion Spawn)](../../recipes/2023-07-05_mtsplinefx-arcs-rayline-laser-sparks-part-c.md)
- 2023-07-03 · [Обзор функций: переработанный nxQuestion и Data Mapping в NeXus (Fused 2023.3)](../../recipes/2023-07-03_feature-notes-nxquestion-data-mapping.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-13 · [Кристалл, который осыпается по осколку (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
- 2023-04-04 · [Укорачивание трейлов до смерти частиц (xpTrailsMod через xpQuestion или action Change Trails)](../../recipes/2023-04-04_shrink-trails-on-age-xptrailsmod.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-21 · [Три поколения спавна из одного эмиттера (уровни xpMultiSpawn + группы для отображения)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
