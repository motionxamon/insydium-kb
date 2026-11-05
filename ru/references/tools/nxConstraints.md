# nxConstraints — карточка инструмента

Встречается в **37** рецептах · 2023-02-21 → 2026-10-20 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Дешёвая имитация столкновений между частицами: слой **nxConstraints ▸ Forces** — Attraction 0, Repulsion 20%, Radius 0.05, Falloff Flat, максимум ~5 соседей. Привяжите силу Repulsion к **Speed** (диапазон 0–0.5), чтобы неподвижное ядро не расталкивало. Теперь падающие песчинки скатываются по внешней поверхности, а не проваливаются сквозь неё. [▶ 13:17](https://youtu.be/yOPa8oM_KXE?t=797) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- nxConstraints со слоем **Collisions** (≥3 итераций) → частицы перестают проникать друг в друга и катятся. [▶ 1:12](https://youtu.be/OFx-ALGOlAU?t=72) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- **nxConstraints** ▸ один слой, связи **Birth** (пружины). Посмотреть можно через Display эмиттера ▸ **Display Constraints**. [▶ 1:19](https://youtu.be/QDBN_Xu_l68?t=79) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*
- **nxConstraints → Connections Birth**: Connection Limit 8, Radius ~20. Показать связи: Display эмиттера ▸ **Display Constraints**. [▶ 1:21](https://youtu.be/_7bYCGydqXo?t=81) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- **nxConstraints Mapping ▸ Color Brightness → Stiffness слоя Viscosity**: чёрный = полная жёсткость, белый ≈ 0 (резкий спад). [▶ 7:59](https://youtu.be/_k0LatnQQJw?t=479) — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- Начните со сцены NeXus; **отключите nxGravity и nxConstraints** и xpCollider на коробке — физику берёт на себя солвер C4D. [▶ 0:51](https://youtu.be/eBnMW0v43Ac?t=51) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- **nxConstraints ▸ слой Viscosity**: Connection Limit 8, Radius 20 cm, **Stiffness 40%**, **Iterations 2** (больше итераций = не только точнее, но и сильнее). [▶ 2:36](https://youtu.be/14SqrdO1c6o?t=156) — *[2025-08-05](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)*
- nxConstraints ▸ Mapping ▸ **Group map**: Category Viscosity, Parameter Stiffness, диапазон **1 → 3**. Кривая: группа 1 → ~0.06 (чуть-чуть связности), группа 2 → 0.5, группа 3 → 1. [▶ 5:49](https://youtu.be/14SqrdO1c6o?t=349) — *[2025-08-05](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)*
- Удержать вместе: **nxConstraints ▸ Distance** (не Birth — частицы уже существуют), только группа 2, **Connection Limit 50**, **Radius 250**; stiffness/breaking по умолчанию → тянущиеся отслаивающиеся лоскуты. [▶ 5:00](https://youtu.be/xGxf_IIIekY?t=300) — *[2025-05-22](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)*
- **nxConstraints «birth»**: birth springs, поиск **40 cm**, **Limit 6**, **Stiffness 90**, разрыв **None**. Emitter ▸ Display ▸ **Display Constraints**, чтобы их видеть. [▶ 1:57](https://youtu.be/PIgXQtSgnMY?t=117) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- **nxConstraints «repel»** под birth: радиус слоя Forces **80/80**, отталкивание примерно на **20% сильнее**, Groups Affected **repulsion** → частицы раздуваются по мере того, как поле переводит их в группу. [▶ 5:27](https://youtu.be/PIgXQtSgnMY?t=327) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- Слой **nxConstraints ▸ Collisions**. С настройками по умолчанию всё схлопывается → **Iterations 10**. [▶ 2:14](https://youtu.be/0JdFAE_dopk?t=134) — *[2025-05-13](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)*
- **nxConstraints** ▸ связь **Birth** → через кадр появляются жёлтые пружины. [▶ 1:32](https://youtu.be/fzMhJobCGR0?t=92) — *[2025-03-20](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)*
- nxConstraints: **Iterations 10** (больше = жёстче) и слой **Collision** → упругое мягкое тело вместо шлепка. [▶ 2:20](https://youtu.be/fzMhJobCGR0?t=140) — *[2025-03-20](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)*

## Все рецепты (37)
- 2026-10-20 · [Распад объёма частиц снаружи внутрь (nxQuestion Neighbors → Set Group, силы с маппингом по скорости)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-08-04 · [Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-14 · [Пружинистая сетка констрейнтов, отрендеренная трейлами (связи nxConstraints Birth + nxTrail в режиме Constraints)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2025-09-16 · [Тянущиеся и рвущиеся волокна (nxConstraints Birth + трейлы по констрейнтам + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-09-09 · [Горячая текучая / холодная тягучая жидкость, которая снова плавится при контакте (группы + nxBlend + mapping вязкости)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-08-26 · [Частицы → rigid body в C4D с цветом от nxColor (xpGenerator + теги Simulation + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-08-05 · [Три тягучие жидкости с тремя вязкостями (группы + nxConstraints Viscosity с mapping по Group)](../../recipes/2025-08-05_gloopy-mix-group-mapped-viscosity.md)
- 2025-07-31 · [Скиннинг крыльев летучей мыши с тканевой перепонкой (C4D Bind heat map + Cloth + Cloth Belt)](../../recipes/2025-07-31_bat-wing-skinning-c4d-cloth-belt.md)
- 2025-05-22 · [Отслаивание с поверхности, как у краски (группы nxInfectio + nxWind/nxTurbulence + nxConstraints Distance)](../../recipes/2025-05-22_particle-peeling-nxinfectio-constraints.md)
- 2025-05-20 · [Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-05-13 · [Коллизии частиц между собой с импульсными «световыми» выбросами (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2025-03-20 · [Разрезание мягкого тела коллайдером-ножом (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-10-04 · [Органический рост складок, ползущий по статуе (отталкивание в nxConstraints Forces + xpDeformer, группы nxQuestion по vertex map)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-10-01 · [Рендер связей-пружин + стеклянная оболочка под водой (xpTrail Algorithm Constraints, xpOpenVDBMesher, туман Redshift Environment)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-09-03 · [Пружинящие ленты и рассыпчатые гранулы по цвету (nxConstraints Birth connections, Break через маппинг на Color Brightness)](../../recipes/2024-09-03_nxconstraints-break-mapped-to-color.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-02 · [Эмиссия со сплайна, спроецированного на волнующуюся поверхность (mtSplineSample + mtPointProject + кэш Jiggle)](../../recipes/2024-07-02_projected-spline-emission-animated-surface.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-04-23 · [Лазерные лучи от частиц внутри сферы (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-05 · [Смешивание густых красок (nxFluids SPH + nxConstraints Viscosity + nxBlend)](../../recipes/2024-03-05_nxblend-paint-mix.md)
- 2024-02-27 · [Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-12-12 · [Отслаивание, управляемое заражением (nxInfectio Use Groups + nxWind/nxTurbulence на группе заражённых + разрыв nxConstraints Distance)](../../recipes/2023-12-12_nxinfectio-groups-peel-constraints.md)
- 2023-11-07 · [Плавающий / тонущий объект в жидкости NeXus (тег xpDynamics + плотность в nxFluids tag на эмиттер)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-10-10 · [Самоорганизующийся сгусток частиц (притяжение/отталкивание nxConstraints Forces + отталкивание по радиусу + Collisions + Friction)](../../recipes/2023-10-10_nxconstraints-forces-organic-blob.md)
- 2023-09-27 · [Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-09-05 · [Тягучая жидкость в меше с переносом цветов частиц (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)](../../recipes/2023-09-05_fluid-mesh-vertex-color-transfer.md)
- 2023-07-05 · [Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-06-12 · [Быстрая вязкая струя шоколада/мёда (xpFluidPBD + xpConstraints Viscosity, эмиссия Hexagonal)](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-17 · [Взрывающаяся планета: детальные частицы на поверхности, вращающиеся вместе со сферой (эмиссия с текстуры на смещённой геометрии, Global Transform, отступ по цвету)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Взрывающаяся планета: эмиссия с текстуры, зависящая от скорости вращения, и слипающиеся обломки (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-02-21 · [Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
