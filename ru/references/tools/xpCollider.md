# xpCollider — карточка инструмента

Встречается в **42** рецептах · 2023-02-21 → 2026-08-04 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Логотип: **xpCollider tag**, Bounce 0, Friction 0. FLIP Solver Accuracy: substeps **Min 2 / Max 4**. [▶ 2:08](https://youtu.be/brhdU9ibnow?t=128) — *[2026-01-06](../../recipes/2026-01-06_sticky-flip-object-rising.md)*
- Куб-контейнер с **xpCollider Normals: Inside**. Box-эмиттер того же размера, **Shot – Regular**, radius 3, full life. nxGravity; **nxFluids SPH** substeps 4, viscosity 4. [▶ 0:56](https://youtu.be/C_fXmAUTb2Q?t=56) — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- **Тег xpCollider** на торе: Bounce 0, немного Friction (с вариацией для разнообразия скольжения) → при расталкивании частицы отскакивают… [▶ 7:04](https://youtu.be/PTamR793O-k?t=424) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- Начните со сцены NeXus; **отключите nxGravity и nxConstraints** и xpCollider на коробке — физику берёт на себя солвер C4D. [▶ 0:51](https://youtu.be/eBnMW0v43Ac?t=51) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- Контейнер: **xpCollider** bounce/friction 0, Normals **Inside**; сделайте редактируемым и **удалите грань на выходе**. [▶ 1:31](https://youtu.be/q8Crdpa1XUw?t=91) — *[2025-07-08](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)*
- Геометрия X: xpCollider Outside, bounce 0. [▶ 7:16](https://youtu.be/u2MiqeckNaQ?t=436) — *[2025-06-10](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)*
- **xpEmitter ▸ Object**: трубка, **Polygon Area**; Emission **Shot** в режиме **Simulate** (частицы есть уже на кадре 0), скорость 0, **100,000** частиц. Тег xpCollider на трубке. [▶ 0:44](https://youtu.be/xGxf_IIIekY?t=44) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- Пол: тег **xpCollider**, bounce 0, немного трения. [▶ 16:12](https://youtu.be/V4mwAf8tcLk?t=972) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Контейнер: X-ray включён; тег **xpCollider** с нормалями **внутрь**, Bounce 0. [▶ 4:37](https://youtu.be/_W2ivetBEPo?t=277) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Дешёвые коллайдеры камней: Ctrl-перетаскиванием скопируйте null с tfRock в Utilities, спрячьте high-res набор, у копии снизьте **Subdivisions tfRock до 1** (форма та же, полигонов в разы меньше). Положите копию в **xpJoin** и повесьте на join один тег xpCollider (Bounce 0). [▶ 7:26](https://youtu.be/_W2ivetBEPo?t=446) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- Против проваливания: скопируйте бюст (без деформера/тегов), сделайте невидимым, повесьте тег **xpCollider** с выключенными Bounce и Friction. [▶ 25:00](https://youtu.be/eJXaD9gVMsE?t=1500) — *[2024-10-04](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)*
- Родительские частицы эмитятся с примитива-сферы (на сфере тег xpCollider). [▶ 0:10](https://youtu.be/LB-aA-N-2b0?t=10) — *[2024-08-27](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)*
- Тег **xpCollider** на terrain sim (Bounce 0, Friction 0). Ступени и камни — каждые в свой **xpJoin** (один тег коллайдера на join); у камней Bounce 10, Friction 5. Цвет отображения всех коллайдеров — чёрный. [▶ 6:29](https://youtu.be/t-1ZIIRF8Jg?t=389) — *[2023-11-20](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)*
- Пол: **xpCollider** tag. Добавьте вариацию отскока, немного трения с вариацией и немного **Scatter** для случайных углов отскока. [▶ 2:30](https://youtu.be/x1SAOjOSOzs?t=150) — *[2023-08-22](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)*

## Все рецепты (42)
- 2026-08-04 · [Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-01-06 · [Вода, налипающая на объект, поднимающийся из FLIP-бассейна (nxSticky)](../../recipes/2026-01-06_sticky-flip-object-rising.md)
- 2025-10-28 · [Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-26 · [Частицы → rigid body в C4D с цветом от nxColor (xpGenerator + теги Simulation + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-07-15 · [Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-07-08 · [Бесконечная река / поток жидкости (открытый с одной стороны контейнер + эмиттер подпитки + nxKill)](../../recipes/2025-07-08_continuous-fluid-stream-open-container.md)
- 2025-06-10 · [Жидкая сфера: оседает → кипит → взрывается → плещется (initial state + nxVorticity / nxWind с маппингом по возрасту)](../../recipes/2025-06-10_mograph-fluid-boil-explode-wind.md)
- 2025-05-22 · [Отслаивание с поверхности, как у краски (группы nxInfectio + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-05-13 · [Коллизии частиц между собой с импульсными «световыми» выбросами (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-25 · [Песок + вода в одной симуляции (nxFluids SPH Granular + тег nxFluids на эмиттере, stability через age)](../../recipes/2025-03-25_sand-and-water-granular-liquid-mix.md)
- 2025-03-20 · [Разрезание мягкого тела коллайдером-ножом (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-10-04 · [Органический рост складок, ползущий по статуе (отталкивание в nxConstraints Forces + xpDeformer, группы nxQuestion по vertex map)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-09-03 · [Пружинящие ленты и рассыпчатые гранулы по цвету (nxConstraints Birth connections, Break через маппинг на Color Brightness)](../../recipes/2024-09-03_nxconstraints-break-mapped-to-color.md)
- 2024-08-27 · [Самопрорастающие усики по полю (nxQuestion Variable + Spawn + Set Age/Life, nxPush по радиусу)](../../recipes/2024-08-27_nxquestion-spawning-particle-tendrils.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-07-02 · [Эмиссия со сплайна, спроецированного на волнующуюся поверхность (mtSplineSample + mtPointProject + кэш Jiggle)](../../recipes/2024-07-02_projected-spline-emission-animated-surface.md)
- 2024-05-07 · [Реалистичные листья на порывистом ветру (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2024-03-19 · [Неспокойная, закручивающаяся вода (nxVorticity на PBD и SPH)](../../recipes/2024-03-19_nxvorticity-choppy-water.md)
- 2024-02-27 · [Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-02-20 · [Слои жидкостей разной плотности (density в nxFluids tag для SPH / радиус для PBD)](../../recipes/2024-02-20_nxfluids-mixed-density.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-07 · [Плавающий / тонущий объект в жидкости NeXus (тег xpDynamics + плотность в nxFluids tag на эмиттер)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-08-22 · [Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-06-20 · [Распад модели полигон за полигоном под управлением частиц (xpFragmenter Faces Polys, xpWind с linear field, xpTurbulence с маппингом на пройденную дистанцию)](../../recipes/2023-06-20_xpfragmenter-wind-disintegration.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Логотип раскалывается по времени, раскалывается повторно от удара и выпускает обломки и пыль (слои xpShatter + xpDynamics Push + Spawn коллайдера + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-19 · [Обзор функций: превью mtRayline (генератор сплайнов-лучей MeshTools)](../../recipes/2023-04-19_feature-notes-mtrayline-sneak-peek-part-a.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-16 · [Вулканический кратер + низкополигональный коллайдер (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)](../../recipes/2023-03-16_terraformfx-volcano-crater-lowpoly-collider-part-a.md)
- 2023-03-16 · [Песочный logo reveal, где симулируются только «геройские» гранулы (nxFluids SPH Granular + статичный разброс по vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-07 · [Снежная скульптура, которая рассыпается (гексагональная упаковка в режиме Shot + nxFluids SPH Granular: friction, substeps, stability, cohesion)](../../recipes/2023-03-07_nexus-sph-granular-snow-sculpture.md)
- 2023-02-21 · [Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
