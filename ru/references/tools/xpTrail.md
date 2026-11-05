# xpTrail — карточка инструмента

Встречается в **25** рецептах · 2023-02-14 → 2026-03-31 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Эмиттер Circle, стреляющий наружу; xpTrail на эмиттере. [▶ 0:10](https://youtu.be/HvX6qaVei1o?t=10) — *[2026-03-31](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)*
- Рендерящиеся линии: **xpTrail** → **Algorithm: Constraints → Birth** (вместо трассировки путей). [▶ 3:27](https://youtu.be/_7bYCGydqXo?t=207) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- Констрейнты — прямые от точки к точке → смягчаем: xpTrail Spline **Intermediate Points Uniform 8** + дочерний **xpTrailDeformer** (формула по Y, небольшая **Amplitude ~1 cm**, подобранная Wavelength); используйте сплайн деформера, чтобы концы не двигались (0 в начале/конце, полная в середине). [▶ 5:12](https://youtu.be/_7bYCGydqXo?t=312) — *[2025-09-16](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)*
- Пример эффекта: эмиссия 25/кадр + **xpTrail** (length 25, variation 12) → световые шлейфы за движениями. [▶ 6:23](https://youtu.be/Qd_kEHZ-4JY?t=383) — *[2025-08-12](../../recipes/2025-08-12_mocap-pla-emission.md)*
- Элементы: частицы эмиттера (щупальца) → mtRayLine пускает лучи во внутреннюю сферу → частицы в точках контакта → xpTrail. [▶ 0:54](https://youtu.be/K560tf-sU0I?t=54) — *[2025-06-03](../../recipes/2025-06-03_redshift-rayline-additive-curves.md)*
- Рендер: **xpTrail**, Algorithm **Constraints**, тип = birth springs. [▶ 6:59](https://youtu.be/PIgXQtSgnMY?t=419) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- Опционально: **xpTrail** на эмиттере для рендера переплетённых линий. — *[2025-05-06](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)*
- **xpTrail** на эмиттер. — *[2025-03-13](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)*
- xpTrail ▸ Thickness and Color ▸ **Trail Color Mode**: Particle Color перекрашивает весь шлейф сразу; **Per Vertex** прорисовывает смену цвета во времени (с Tracer в C4D так не сделать). [▶ 8:00](https://youtu.be/W8E4taTkKag?t=480) — *[2025-03-13](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)*
- **xpTrail** с эмиттером → **Redshift Object tag ▸ Curves ▸ Capsules**, thickness 200 для первого просмотра. [▶ 1:37](https://youtu.be/Lx6Sugl11TA?t=97) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Цвет: xpTrail ▸ Thickness & Color ▸ Trail Color **Per Vertex** (запоминает историю цвета); Redshift **Vertex Attribute ▸ пресет Curves ▸ Curve Color** → в transmission color стеклянного материала. [▶ 3:01](https://youtu.be/Lx6Sugl11TA?t=181) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Ширина на каждый шлейф: thickness в Redshift обратно на 1; режим xpTrail Thickness **Use Particle Current** → каждый шлейф = размер своей частицы. Mesh subdivisions **Adaptive** (гладко). [▶ 4:07](https://youtu.be/Lx6Sugl11TA?t=247) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Анимированная ширина: **nxScale** Set by Falloff с тем же random-полем; radius эмиттера 200, без вариации; xpTrail Thickness **Use Radius Variable** → ширина прорисовывается вдоль шлейфа. [▶ 5:39](https://youtu.be/Lx6Sugl11TA?t=339) — *[2024-12-10](../../recipes/2024-12-10_trail-thickness-from-radius.md)*
- Три объекта **xpTrail** (по одному на emitter, в цвет) → рендер в Redshift. — *[2024-11-12](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)*

## Все рецепты (25)
- 2026-03-31 · [Выброс частиц с плавной органичной остановкой (nxSpeed Range + curl-турбулентность)](../../recipes/2026-03-31_nxspeed-range-organic-stop.md)
- 2025-09-16 · [Тянущиеся и рвущиеся волокна (nxConstraints Birth + трейлы по констрейнтам + xpTrailDeformer)](../../recipes/2025-09-16_gpu-constraints-stretchy-fibres.md)
- 2025-08-12 · [Чистая эмиссия частиц с mocap-персонажа (xpJoin → Alembic → запекание PLA)](../../recipes/2025-08-12_mocap-pla-emission.md)
- 2025-06-03 · [Рендер лучей mtRayLine + трейлов как аддитивных градиентных кривых внутри стекла с дисплейсом (Redshift)](../../recipes/2025-06-03_redshift-rayline-additive-curves.md)
- 2025-05-20 · [Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-05-06 · [Проявление wireframe частицами (nxFollowGeo в режиме Edge + nxTurbulence + ограничение nxSpeed)](../../recipes/2025-05-06_wireframe-reveal-nxfollowgeo-edge.md)
- 2025-03-13 · [Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)](../../recipes/2025-03-13_c4d-field-force-volume-vectors-colored-trails.md)
- 2024-12-10 · [Шлейфы, толщина которых следует за радиусом частиц (xpTrail Thickness: Use Radius Variable → кривые Redshift)](../../recipes/2024-12-10_trail-thickness-from-radius.md)
- 2024-11-12 · [Распускающийся цветок из трейлов (nxTurbulence Curl Blend/Add по возрасту + сила по скорости)](../../recipes/2024-11-12_particle-trail-flower-age-mapped-curl.md)
- 2024-10-01 · [Рендер связей-пружин + стеклянная оболочка под водой (xpTrail Algorithm Constraints, xpOpenVDBMesher, туман Redshift Environment)](../../recipes/2024-10-01_render-nxconstraints-redshift-trails-glass.md)
- 2024-08-20 · [Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)](../../recipes/2024-08-20_micro-cells-pbd-surface-tension.md)
- 2024-06-04 · [Трейлы с цветом по вершинам, аддитивный рендер в Redshift (nxColor Time Dependent + xpTrail Per Vertex + Vertex Attribute)](../../recipes/2024-06-04_particle-color-trails-redshift-additive.md)
- 2024-04-23 · [Лазерные лучи от частиц внутри сферы (mtRayline + nxConstraints Forces + xpTrail)](../../recipes/2024-04-23_mtrayline-particle-lasers.md)
- 2024-03-26 · [Стилизованные линии потока аэротрубы вокруг машины (nxAvoid + nxAttract + nxDirection + xpTrail)](../../recipes/2024-03-26_nxavoid-wind-tunnel-trails.md)
- 2024-03-12 · [Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2024-02-27 · [Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)](../../recipes/2024-02-27_nxconstraints-chain-reaction.md)
- 2023-12-19 · [Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-19 · [Обзор функций: превью mtRayline (генератор сплайнов-лучей MeshTools)](../../recipes/2023-04-19_feature-notes-mtrayline-sneak-peek-part-a.md)
- 2023-04-04 · [Укорачивание трейлов до смерти частиц (xpTrailsMod через xpQuestion или action Change Trails)](../../recipes/2023-04-04_shrink-trails-on-age-xptrailsmod.md)
- 2023-02-14 · [Извивающиеся анимированные трейлы, превращённые в сужающиеся трубки (xpTrailDeformer formula/noise + xpSplineMesher)](../../recipes/2023-02-14_xptraildeformer-wiggle-spline-mesher.md)
