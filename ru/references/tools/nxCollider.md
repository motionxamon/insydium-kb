# nxCollider — карточка инструмента

Встречается в **23** рецептах · 2023-03-16 → 2026-10-30 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Ctrl-drag копию, поверните на 180° и 90° → S-образный изгиб. Добавьте куб + **nxCollider** (scatter) после выхода: коллизии работают в режиме Guide, а в Deform нет (частиц там на самом деле нет). [▶ 17:44](https://youtu.be/WJwIek6M8z8?t=1064) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- **Wake Speed** 10.5 (чуть выше Sleep Speed), Wake Spread 0. Сфера + **nxCollider** (bounce/friction 0) расталкивает и будит песчинки; они снова оседают и засыпают. [▶ 14:21](https://youtu.be/UT9_Aht5waE?t=861) — *[2026-10-11](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)*
- **Use Bounds** выкл → разреженный solve, но тогда добавьте куб + **nxCollider** (friction) в качестве пола. В демо домен оставлен. [▶ 4:57](https://youtu.be/jItRyLgdjPg?t=297) — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- Большая плоскость + **nxCollider**: Bounce 0, приличный Friction. **nxGravity** по умолчанию. [▶ 3:18](https://youtu.be/M2yxZlZQBec?t=198) — *[2026-10-06](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)*
- **nxGravity**; **nxCollider** на плоскости, Bounce 0, немного Friction. [▶ 1:49](https://youtu.be/yp5579on6J8?t=109) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- Заполнить другую форму: замените объект эмиттера на UV sphere; добавьте на неё **nxCollider** с **Inside normals**, Bounce 0, Friction 0, чтобы удерживать жидкость внутри. [▶ 7:02](https://youtu.be/vglrHSL-uc4?t=422) — *[2026-08-11](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)*
- Большая скрытая плоскость + **nxCollider**: Bounce 0, Friction высокий (**80%**, до 100 для слипания). **nxGravity** по умолчанию. [▶ 0:57](https://youtu.be/rkuNbceXolQ?t=57) — *[2026-07-28](../../recipes/2026-07-28_sph-granular-clumping-sand.md)*
- Три Сюзанны (Shift+D); **nxGravity**; **nxCollider** со всеми тремя, Friction на максимум (частицы прилипают). Speed эмиттера **8**, расширьте примерно до 12, чтобы накрыть их. [▶ 3:58](https://youtu.be/QDBN_Xu_l68?t=238) — *[2026-07-14](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)*
- **nxCollider**: слой Suzanne (bounce 0, немного friction, потом меньше); плюс **куб**-пол внутри bounds отдельным слоем (bounce 0, friction) — voxel-солверам нужны объёмные коллайдеры, а не плоскости. [▶ 7:19](https://youtu.be/pz6LDGGeD5A?t=439) — *[2026-06-12](../../recipes/2026-06-12_blender-apic-viscous-slime.md)*

## Все рецепты (23)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-20 · [Распад объёма частиц снаружи внутрь (nxQuestion Neighbors → Set Group, силы с маппингом по скорости)](../../recipes/2026-10-20_surface-dissolve-neighbor-search.md)
- 2026-10-11 · [Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-09-08 · [Струя воды размывает комковатый песок (nxFluids SPH Granular + жидкость в Mixer, цвет nxBlend → mapped-настройки granular)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-08-11 · [Preset Liquid Fill с FLIP/APIC, мешем и отдельным эмиттером пены (NeXus Liquid Fill, nxFoam, nxMesher)](../../recipes/2026-08-11_liquid-fill-flip-foam-blender.md)
- 2026-07-28 · [Слипающийся песок / снег через SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)](../../recipes/2026-07-28_sph-granular-clumping-sand.md)
- 2026-07-14 · [Пружинистая сетка констрейнтов, отрендеренная трейлами (связи nxConstraints Birth + nxTrail в режиме Constraints)](../../recipes/2026-07-14_birth-constraints-rendered-trails.md)
- 2026-07-02 · [Макро-всплеск воды с тонкими плёнками (nxFluids APIC/FLIP + nxSheeter + nxMesher Zhu-Bridson, Cycles)](../../recipes/2026-07-02_blender-apic-sheeter-macro-splash.md)
- 2026-06-29 · [Основы Data Mapping: гравитация по возрасту/радиусу/яркости, циклические импульсы fuel/smoke в EFX (вкладка Mapping, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-22 · [Запуск модификаторов переключением групп частиц (nxGroup, Groups Affected, nxQuestion Set Group)](../../recipes/2026-06-22_blender-particle-groups-nxquestion-switching.md)
- 2026-06-12 · [Вязкая слизь, укладывающаяся кольцами на голове (nxFluids APIC viscosity + surface tension, nxMesher Spheres + Mean Curvature)](../../recipes/2026-06-12_blender-apic-viscous-slime.md)
- 2025-05-13 · [Коллизии частиц между собой с импульсными «световыми» выбросами (nxConstraints Collisions + subframe steps)](../../recipes/2025-05-13_particle-collisions-nxconstraints-pulse.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-25 · [Обзор функций: перестроенное ядро NeXus 2024.2 — быстрее на GPU и коллизии с анимированной геометрией](../../recipes/2024-04-25_feature-notes-nexus-2024-2-speed-collisions.md)
- 2024-04-02 · [Вода, собирающаяся в капли (поверхностное натяжение nxFluids SPH + nxGravity по возрасту)](../../recipes/2024-04-02_nxfluids-surface-tension-droplets.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-08-22 · [Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-05-30 · [Тягучая жидкость без флюидного солвера (пружины nxConstraints при рождении → алгоритм xpTrail Constraints → xpOpenVDBMesher)](../../recipes/2023-05-30_nxconstraints-gloopy-liquid-trail-mesh.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-16 · [Вулканический кратер + низкополигональный коллайдер (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)](../../recipes/2023-03-16_terraformfx-volcano-crater-lowpoly-collider-part-a.md)
