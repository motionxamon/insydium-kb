# nxColor — карточка инструмента

Встречается в **47** рецептах · 2023-04-20 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxWarp Scroll** по размеру так, чтобы охватить все частицы (тяните за хэндлы); Radius 8, Spacing 1, потом увеличьте Radius и Roll; отрицательный Direction. По желанию: масштаб по Y 15–40% для глубины, затем поднимите высоту варпа (по умолчанию 1 cm), чтобы всё влезло. **nxColor** — градиент по Speed. [▶ 10:34](https://youtu.be/WJwIek6M8z8?t=634) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **Поток по трубе (C4D):** Disc-эмиттер r 15 cm, rate 15,000, life 300, + nxTurbulence + nxColor. **nxWarp Bend** повернуть на 90° навстречу потоку, Angle 90°. [▶ 11:17](https://youtu.be/WJwIek6M8z8?t=677) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **FLIP-спираль (Blender):** высокий домен nxFluids FLIP; сферический nxEmitter внизу, **Match Solver Resolution** → FLIP, направление +Z, скорость 2.5; nxColor по Speed; nxTurbulence strength 16. [▶ 30:13](https://youtu.be/WJwIek6M8z8?t=1813) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **nxColor** (группа 2): градиент по параметру (Magma), маппинг по направлению Y. [▶ 8:44](https://youtu.be/yOPa8oM_KXE?t=524) — *[2026-10-20](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)*
- **nxColor**: градиент Magma, параметр **Distance** (пройденное расстояние), max ~**5 m** (Speed 0–3.5 тоже работает; разверни градиент для перехода тёмный→светлый). [▶ 6:05](https://youtu.be/I2ERiN8Vk2Q?t=365) — *[2026-08-25](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)*
- Цвет на частицу (например, градиент nxColor по Speed, 0–300 cm/s) **не** отображается при **Multi-Instance** (всё считается одним объектом) → переключаем xpGenerator на **Render Instances** (медленнее). [▶ 5:49](https://youtu.be/OFx-ALGOlAU?t=349) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- **nxColor** в режиме Speed всего с двумя цветами (красный — быстрые / синий — медленные), max ~2 — работает только в режиме Velocity. [▶ 19:09](https://youtu.be/m2jeYLxuRog?t=1149) — *[2026-07-09](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)*
- В GN уберите связь радиуса и задайте радиус точек вручную (~0.001). Шейдер: перенесите цвет частиц в **Emission** (strength 10), смешайте с шейдером **Transparent** для аддитивного вида; нода **Hue/Saturation/Value** приглушает насыщенные цвета, не трогая nxColor. [▶ 27:32](https://youtu.be/m2jeYLxuRog?t=1652) — *[2026-07-09](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)*
- **nxColor** Gradient by Parameter (speed), подстройте min/max. [▶ 11:53](https://youtu.be/P9O1SJhPeik?t=713) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- Третья группа + **nxGravity** с Groups Affected = group 3. Новое условие (используйте **Outdent**, чтобы оно не было дочерним): **Distance Travelled > 5 m, variation 1 m** → Set Group 3 (при проверке через цветовое действие отключите nxColor — он перекрывает цвет). [▶ 15:49](https://youtu.be/P9O1SJhPeik?t=949) — *[2026-06-22](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)*
- **Cycles**: точки автоматически рендерятся чистыми сферами. Новый материал («color sphere»); в GN добавьте **Set Material**; в shader’е — нод **Attribute** «Color» → Base Color. Вживую: правки градиента nxColor сразу обновляют рендер. [▶ 10:04](https://youtu.be/Hx0g1V9-HqM?t=604) — *[2026-06-15](../../recipes/2026-06-15_blender-particle-color-to-render.md)*
- **xpColor** (CPU) с **Noise shader** Maxon: **Cell Voronoi**, global scale ~330, сильный low/high clip → пятнистый чёрно-белый цвет на частицах. (CPU-модификатор взят потому, что он сэмплит шейдеры Maxon в полном 3D; у nxColor GPU-нойзы.) [▶ 1:18](https://youtu.be/zyN7ERz7yuw?t=78) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- Анимируем цвет частиц: слой **nxColor** **Distance from Object** → анимированный Null; градиент, например, оранжевый (дальше 300 cm) → жёлтый → зелёный → синий (вблизи). [▶ 4:36](https://youtu.be/KimysoJRI9I?t=276) — *[2026-03-10](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)*
- **nxColor** Gradient (Parameter) → **Neighbor**: radius 40 cm, диапазон 0–8000 соседей; пресет чёрный→белый (цвет — позже в рендере). [▶ 2:45](https://youtu.be/-GELMnDapCc?t=165) — *[2025-12-02](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)*

## Подводные камни
- Порядок важен: nxColor → nxQuestion (группа) → силы → speed-clamp question последним; push перед kill. — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*

## Все рецепты (47)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-20 · [Распад объёма частиц снаружи внутрь (nxQuestion Neighbors → Set Group, силы с маппингом по скорости)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-09-15 · [Рендер данных частиц NeXus в Octane (цвет, радиус → стекло)](../../recipes/2026-09-15_octane-particle-data.md)
- 2026-08-25 · [Шлейфы «взрыв-цветок» с толщиной от скорости и цветом по вершинам (nxTrail, nxScale + маппинг скорости в nxTurbulence)](../../recipes/2026-08-25_nxtrail-speed-mapped-thickness-color.md)
- 2026-08-04 · [Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-09 · [Дымчатый point cloud, адвектированный взрывом (nxExplosiaFX Particle Advect, Fast-адвекция скорости, силы с привязкой ко времени, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-06 · [Усики из слоёной curl-турбулентности (слои nxTurbulence Curl + FBM + Voronoi, привязка к возрасту по слоям, ограничение nxSpeed, плавное появление через nxScale)](../../recipes/2026-07-06_blender-layered-curl-turbulence-tendrils.md)
- 2026-06-30 · [Запуск/остановка зацикленной анимации nxQuestion через action Break](../../recipes/2026-06-30_nxquestion-action-break.md)
- 2026-06-22 · [Запуск модификаторов переключением групп частиц (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-15 · [Цвет частиц в рендере Cycles и Eevee (экспорт Point Cloud из nxEmitter + атрибуты Geometry Nodes)](../../recipes/2026-06-15_blender-particle-color-to-render.md)
- 2026-06-09 · [Случайная ориентация при рождении + повторяемые обороты на 360° (nxSpin + сброс возраста)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-06-02 · [Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2026-03-31 · [Выброс частиц с плавной органичной остановкой (nxSpeed Range + curl-турбулентность)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2026-03-17 · [Управляемая тягучая струя жидкости (PBD + nxDirection + nxMesher)](../../recipes/2026-03-17_nxdirection-art-directed-liquid-stream.md)
- 2026-03-10 · [Цветной дым от анимированного цвета частиц (канал цвета nxExplosiaFX → Redshift)](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)
- 2026-02-24 · [Убивать частицы по пройденному расстоянию (сброс age в nxQuestion + Set Life)](../../recipes/2026-02-24_custom-lifespan-by-distance.md)
- 2026-02-17 · [Перекраска закэшированных частиц через nxColor (и ограничение скорости по цвету)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-12-02 · [Абстрактная жидкость с цветными полосами по числу соседей (поиск соседей в nxColor → mesh → стеклянная рампа)](../../recipes/2025-12-02_neighbor-search-color-glass-mesh.md)
- 2025-11-04 · [Частицы, распускающиеся в щелях геометрии (соседи в nxQuestion + поле)](../../recipes/2025-11-04_neighbor-search-crevice-growth.md)
- 2025-10-14 · [Огни города, расползающиеся по рёбрам зданий (nxInfectio + группы)](../../recipes/2025-10-14_city-lights-edge-infection.md)
- 2025-09-11 · [Обзор функций: переписанное GPU-ядро NeXus, GPU falloffs + Data Mapping на каждом слое, вариации в nxQuestion и поиск соседей](../../recipes/2025-09-11_nexus-core-falloffs-mapping-question-variations.md)
- 2025-08-26 · [Частицы → rigid body в C4D с цветом от nxColor (xpGenerator + теги Simulation + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-07-24 · [Обзор функций: слои nxSpin, Noise/Neighbor-градиент в nxColor, Direction Force в nxDirection (превью Fused 2025, часть 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-07-22 · [Прячем жёсткое кольцо эмиссии шумной маской прозрачности (слои nxColor + сплайн birth rate)](../../recipes/2025-07-22_nxcolor-noise-opacity-emission-fade.md)
- 2025-05-27 · [Детализированный взрыв по полю через upres (nxUpres position + velocity, nxExplode, переключение групп через nxQuestion)](../../recipes/2025-05-27_upres-explode-position-velocity-blend.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2025-03-11 · [Точные диапазоны mapping по живым данным частиц (min/max из xpConsole → nxColor / Mapping)](../../recipes/2025-03-11_xpconsole-exact-mapping-ranges.md)
- 2025-02-20 · [Бесшовный бесконечный луп из отрендеренной симуляции частиц (After Effects: дубликат + кроссфейд по opacity)](../../recipes/2025-02-20_seamless-particle-render-loop-after-effects.md)
- 2025-02-18 · [Послойное растворение объёма (nxQuestion Neighbor Count → Group → nxWind/nxColor)](../../recipes/2025-02-18_neighbor-search-surface-dissolve.md)
- 2024-12-10 · [Шлейфы, толщина которых следует за радиусом частиц (xpTrail Thickness: Use Radius Variable → кривые Redshift)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-11-04 · [Рендер пены с цветом по скорости как аддитивного свечения в Redshift, ACEScg в After Effects + speed ramps (Color User Data → Ramp → Geometry Opacity)](../../recipes/2024-11-04_redshift-additive-foam-aces-after-effects-part-2.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-09-17 · [Непересекающиеся ветки из частиц внутри меша (Taiao toTree volume points → spline emitter, nxQuestion Spawn, nxPush, nxScale)](../../recipes/2024-09-17_taiao-volume-branch-particle-network.md)
- 2024-09-10 · [Многослойный ч/б цвет → перекрашенное аддитивное пламя (nxColor Age × Heading × Pitch, Redshift Color User Data)](../../recipes/2024-09-10_nxcolor-blended-layers-redshift-additive.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-07-23 · [Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)](../../recipes/2024-07-23_neighbor-spawn-volume-network.md)
- 2024-07-16 · [Лава, которая застывает и снова плавится (цвет от анимированного поля Random → замапленные сила nxWind + максимальная скорость nxSpeed, nxFluids)](../../recipes/2024-07-16_lava-flow-color-mapped-wind-speed.md)
- 2024-06-04 · [Трейлы с цветом по вершинам, аддитивный рендер в Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-05-21 · [Турбулентное появление текста из частиц (nxCover Edges + слабая сила слоя + удержание Spring, nxColor по Direction)](../../recipes/2024-05-21_nxcover-turbulent-spline-reveal.md)
- 2024-05-14 · [Дымчатая жидкость, ползущая по тору (nxFollowGeo с FOV 360° + friction, nxTurbulence, nxFluids)](../../recipes/2024-05-14_nxfollowgeo-surface-fluid.md)
- 2024-04-22 · [Обзор функций: nxFollowGeo, слоёный nxColor и nxCover (NeXus 2024.2)](../../recipes/2024-04-22_feature-notes-nxfollowgeo-nxcolor-nxcover.md)
- 2024-03-12 · [Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-09-27 · [Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-08-29 · [Частицы растут и меняют цвет внутри поля, а снаружи возвращаются обратно (nxQuestion Field question, Set Color / Set Radius, Else)](../../recipes/2023-08-29_nxquestion-field-color-radius.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
