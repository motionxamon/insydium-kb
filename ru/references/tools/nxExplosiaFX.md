# nxExplosiaFX — карточка инструмента

Встречается в **37** рецептах · 2023-03-29 → 2026-11-03 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Применение: nxExplosiaFX → Sources → плоскость; для Smoke, Temperature и Fuel поставьте **Weight by: Tag** и привяжите vertex map. Для маскированной эмиссии нужны значения повыше: поднимите Fuel (например, 3) и **Burn Rate**, чтобы всё топливо сгорало. [▶ 12:29](https://youtu.be/qv6TE9WtFhg?t=749) — *[2026-11-03](../../recipes/2026-11-03_nexus-falloffs-animated-vertex-maps.md)*
- **Огонь (Blender):** nxExplosiaFX, сфера во вкладке Sources, воксель покрупнее, Temperature Dissipation 3. Границы варпа = домен или чуть больше. Bend 90/180/360°; Twist ~800°. [▶ 20:52](https://youtu.be/WJwIek6M8z8?t=1252) — *[2026-10-30](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)*
- nxExplosiaFX: замените хайполи в **Sources** и **Colliders** на прокси; отключите hierarchy options → симуляция и кэширование намного быстрее. [▶ 12:04](https://youtu.be/C0P7UtWroDo?t=724) — *[2026-10-27](../../recipes/2026-10-27_mocap-sim-proxy.md)*
- Отключите nxExplosiaFX и кэш; добавьте Maxon **Volume Loader** и подключите **первый кадр VDB** — он находит density, temperature, vel_x / vel_y / vel_z. [▶ 2:56](https://youtu.be/qZyBMJaN6ak?t=176) — *[2026-09-29](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)*
- nxExplosiaFX → **Dynamics ▸ Particle Advection** → перетащите туда эмиттер. [▶ 1:27](https://youtu.be/1ERTCdQAoF0?t=87) — *[2026-09-01](../../recipes/2026-09-01_efx-advection-data-questions.md)*
- EFX: тор внутри более высокого **nxExplosiaFX**, добавлен как source; voxel size **0.02**; Simplex noise length scale **5**, strength **50**. [▶ 12:08](https://youtu.be/s5JA_AADBnY?t=728) — *[2026-06-29](../../recipes/2026-06-29_blender-data-mapping-basics.md)*
- **nxExplosiaFX ▸ Object ▸ Sources**: добавьте Сюзанну. Каналы по умолчанию излучают temperature 1000, fuel 0.2, pressure, smoke 0 — дым всё равно появляется, потому что горящее топливо его выделяет. [▶ 2:02](https://youtu.be/RH6ukNvt-No?t=122) — *[2026-06-25](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)*
- Стена (куб) — **collider** для nxExplosiaFX, чтобы дым поднимался по ней. [▶ 0:24](https://youtu.be/kGTKDlTTyxE?t=24) — *[2026-04-07](../../recipes/2026-04-07_soot-damage-vertex-map.md)*
- nxExplosiaFX: домен побольше → **Voxel 6**; Buoyancy **Gravity 0** (флюид остаётся на орбите). [▶ 4:14](https://youtu.be/iPYPQGaz7zQ?t=254) — *[2026-03-24](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)*
- nxExplosiaFX **вкладка Solver → включаем канал Color** (по умолчанию выключен ради экономии памяти). [▶ 1:26](https://youtu.be/KimysoJRI9I?t=86) — *[2026-03-10](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)*
- nxExplosiaFX → Sources: перетащите **анимированный сплайн логотипа** (принимаются сплайны, полигоны и частицы). **Voxel Size 2.7**. [▶ 0:33](https://youtu.be/irQZ4OI7Bhk?t=33) — *[2026-02-10](../../recipes/2026-02-10_upscale-fire-from-spinning-spline.md)*

## Подводные камни
- В 2026.1 beta появился автоматический Redshift-материал дыма по умолчанию, когда VDB-вывод nxExplosiaFX выставлен на render/live — проверьте его, прежде чем собирать материал вручную. — *[2026-09-29](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)*

## Все рецепты (37)
- 2026-11-03 · [Анимированные vertex maps из GPU-фоллоффов NeXus → управление эмиссией nxExplosiaFX](../../recipes/2026-11-03_nexus-falloffs-animated-vertex-maps.md)
- 2026-10-30 · [Формируем частицы, дым и FLIP варпами (nxWarp Scroll / Bend / Helix / Twist — режимы Deform, Guide, Flow)](../../recipes/2026-10-30_nxwarp-deform-guide-flow-modes.md)
- 2026-10-27 · [Живой лоупольный прокси для симуляции на мокап-персонаже (огонь / коллизии)](../../recipes/2026-10-27_mocap-sim-proxy.md)
- 2026-09-29 · [nxExplosiaFX → OpenVDB → Redshift с векторным motion blur](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)
- 2026-09-01 · [Частицы-языки пламени по данным адвекции nxExplosiaFX (kill и цвет по температуре)](../../recipes/2026-09-01_efx-advection-data-questions.md)
- 2026-07-21 · [Материал Redshift для nxExplosiaFX, совпадающий с viewport](../../recipes/2026-07-21_redshift-explosiafx-material.md)
- 2026-07-09 · [Дымчатый point cloud, адвектированный взрывом (nxExplosiaFX Particle Advect, Fast-адвекция скорости, силы с привязкой ко времени, Cycles)](../../recipes/2026-07-09_blender-efx-blast-particle-advection.md)
- 2026-07-07 · [Аддитивно светящиеся частицы в Octane (1 M против 10 M частиц)](../../recipes/2026-07-07_octane-additive-particle-glow.md)
- 2026-06-29 · [Основы Data Mapping: гравитация по возрасту/радиусу/яркости, циклические импульсы fuel/smoke в EFX (вкладка Mapping, Particle Console, Document Time + Cycle)](../../recipes/2026-06-29_blender-data-mapping-basics.md)
- 2026-06-25 · [Огонь с горением топлива и дым с живым рендером в Cycles (источники nxExplosiaFX, силы, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-16 · [Рендер nxExplosiaFX в Cycles 4D (Principled Volume)](../../recipes/2026-06-16_cycles4d-explosiafx-material.md)
- 2026-05-26 · [Подводные пузыри от всплеска (адвекция EFX + nxMesher + дымка из частиц)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-05-12 · [Рендер nxExplosiaFX в Octane через OpenVDB](../../recipes/2026-05-12_octane-explosiafx-vdb.md)
- 2026-04-21 · [Адвекция текста взрывом давления с 10 M частиц (nxExplosiaFX)](../../recipes/2026-04-21_pressure-blast-advection.md)
- 2026-04-07 · [Копоть на стенах от дыма nxExplosiaFX (xpVertexMap + Redshift)](../../recipes/2026-04-07_soot-damage-vertex-map.md)
- 2026-03-24 · [Огонь испускают только быстрые (или крупные) частицы — маппинг источника EFX](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)
- 2026-03-10 · [Цветной дым от анимированного цвета частиц (канал цвета nxExplosiaFX → Redshift)](../../recipes/2026-03-10_colored-smoke-from-particle-color.md)
- 2026-02-10 · [Огонь от вращающегося сплайна логотипа + Upscaling для детализации](../../recipes/2026-02-10_upscale-fire-from-spinning-spline.md)
- 2026-01-27 · [Дымчатый шлейф частиц за бегущим mocap-персонажем (EFX advection)](../../recipes/2026-01-27_gpu-particle-advection-running-character.md)
- 2026-01-13 · [Направляем turbulence/vorticity в EFX на fuel или temperature (маппинг сил)](../../recipes/2026-01-13_efx-forces-mapping.md)
- 2025-12-30 · [Бегущий горящий человек (nxExplosiaFX: наследование движения, топливо с весом по нойзу, бюджет на апскейл)](../../recipes/2025-12-30_man-on-fire.md)
- 2025-12-22 · [Пламя свечи в реальном масштабе (настройки nxExplosiaFX для мелкого масштаба)](../../recipes/2025-12-22_candle-flame-real-scale.md)
- 2025-11-25 · [Детализированный огонь вокруг вращающегося логотипа (первый туториал по GPU nxExplosiaFX)](../../recipes/2025-11-25_detailed-fire-noise-weighted-fuel.md)
- 2025-11-11 · [Дым сухого льда, стекающий по логотипу (отрицательная плавучесть nxExplosiaFX)](../../recipes/2025-11-11_dry-ice-sinking-smoke.md)
- 2025-10-16 · [Обзор функций: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2025-03-18 · [Motion blur частиц в Redshift (custom shutter, Frame Position для умирающих частиц)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2024-04-16 · [Изгибаем прямую симуляцию огня по спирали (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-02-13 · [Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-23 · [Текстовый сплайн, раздуваемый взрывом (xpDynamics на сплайне + адвекция xpExplosiaFX)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-08-15 · [Миллионы частиц, адвектируемых дымом, с аддитивным рендером (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Показать меш только там, где сквозь него проходит дым (Point Density в Cycles 4D на меше, эмиттеры xpExplosiaFX со сдвигом)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
