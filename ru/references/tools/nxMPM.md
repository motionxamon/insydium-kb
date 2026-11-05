# nxMPM — карточка инструмента

Встречается в **32** рецептах · 2023-03-07 → 2026-10-21 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxMPM** с доменом (необязательно — sparse, — но домен даёт более точный контроль и быстрее считается). Display ▸ Draw Grid (Back), чтобы видеть воксели. [▶ 10:23](https://youtu.be/-QzOnmifveY?t=623) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- Эмиттер ▸ **Match Solver Resolution** → nxMPM; радиус теперь задаётся солвером. Resolution 40 → ~600 частиц; **150** → ~30k (для демо, не для продакшена). [▶ 11:50](https://youtu.be/-QzOnmifveY?t=710) — *[2026-10-21](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)*
- **nxMPM** (создаёт домен); поднимите его на +200 по Y, чтобы он стоял на полу. Границы не обязательны (MPM object ▸ **Use Bounds** выкл. = разреженный режим), но с доменом проще и легче. [▶ 2:39](https://youtu.be/UT9_Aht5waE?t=159) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- nxEmitter: Sphere, радиус ~14–17, направление −Y, Rate, скорость 30 см; **Match Solver Resolution** → nxMPM. Добавьте **nxGravity**; длинный таймлайн (8000 F). [▶ 3:36](https://youtu.be/UT9_Aht5waE?t=216) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **nxEmitter** (Box) + Dynamics ▸ **nxMPM** + Modifiers ▸ **nxGravity**. Emitter ▸ **Match Solver Resolution** → MPM (автоматический радиус + упаковка по сетке). Emission **Shot** для одного сгустка. [▶ 2:35](https://youtu.be/jItRyLgdjPg?t=155) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*

## Все рецепты (32)
- 2026-10-21 · [Идущий персонаж рассыпается в песок (nxBind + отрыв по фоллоффу + nxMPM brittle)](../../recipes/2026-10-21_nxbind-crumbling-character-mpm.md)
- 2026-10-11 · [Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-08 · [Струя воды размывает комковатый песок (nxFluids SPH Granular + жидкость в Mixer, цвет nxBlend → mapped-настройки granular)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-04 · [Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-07-28 · [Слипающийся песок / снег через SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-06-12 · [Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2026-06-02 · [Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2025-07-15 · [Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2025-05-14 · [Вода размывает снежную скульптуру (nxFluids SPH granular + liquid tag, nxGravity с маппингом по Age, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-15 · [Upres гранулярной симуляции с сохранением формы (кэш в низком разрешении + смешивание velocity через nxUpres)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2025-04-01 · [Как спрятать гексагональную сетку в сыпучих симуляциях (Jitter эмиттера + nxPush на один кадр + Initial State)](../../recipes/2025-04-01_jitter-grid-push-apart-initial-state.md)
- 2025-03-25 · [Песок + вода в одной симуляции (nxFluids SPH Granular + тег nxFluids на эмиттере, stability через age)](../../recipes/2025-03-25_sand-and-water-granular-liquid-mix.md)
- 2025-03-20 · [Разрезание мягкого тела коллайдером-ножом (nxConstraints Birth + Breaking Threshold)](../../recipes/2025-03-20_cutting-nxconstraints-breaking-collider.md)
- 2024-06-11 · [Статуя рассыпается в песок по мере распространения заражения (группы nxInfectio + nxFluids SPH Granular + nxSpeed Max Speed 0)](../../recipes/2024-06-11_granular-crumble-infectio-groups.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-06 · [Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2024-01-30 · [Металлическая табличка с вмятинами от пуль (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-11-07 · [Плавающий / тонущий объект в жидкости NeXus (тег xpDynamics + плотность в nxFluids tag на эмиттер)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-07-25 · [Рекурсивное разрушение при ударе (слои Voronoi в xpShatter с триггером Collision, твёрдые тела Bullet)](../../recipes/2023-07-25_xpshatter-recursive-bullet.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
- 2023-04-16 · [Взрывающаяся планета: эмиссия с текстуры, зависящая от скорости вращения, и слипающиеся обломки (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-16 · [Песочный logo reveal, где симулируются только «геройские» гранулы (nxFluids SPH Granular + статичный разброс по vertex map)](../../recipes/2023-03-16_nexus-granular-logo-reveal-static-scatter-part-b.md)
- 2023-03-07 · [Снежная скульптура, которая рассыпается (гексагональная упаковка в режиме Shot + nxFluids SPH Granular: friction, substeps, stability, cohesion)](../../recipes/2023-03-07_nexus-sph-granular-snow-sculpture.md)
