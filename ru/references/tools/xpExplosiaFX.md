# xpExplosiaFX — карточка инструмента

Встречается в **13** рецептах · 2023-03-29 → 2025-10-16 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Размер солвера **xpExplosiaFX** **50 × 1300 × 50** (высокий, узкий). Опции контейнера: **закрыть все стороны, кроме верха**. [▶ 0:45](https://youtu.be/RkAB9dD0X5k?t=45) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- Источник топлива: сфера r 5 cm внизу + **xpExplosiaFX Source tag**: Solid выкл. (заполняет объём), Heat 200, Fuel 200, добавьте **Pressure**, чтобы газ быстрее шёл вверх. [▶ 1:35](https://youtu.be/RkAB9dD0X5k?t=95) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- На кадре 0 добавьте деформер **Spline Wrap** дочерним к объекту xpExplosiaFX, spline = Helix, ось **+Y**. Закэшированный/симулированный объём теперь следует спирали; углы Helix можно анимировать keyframe-ами. [▶ 4:22](https://youtu.be/RkAB9dD0X5k?t=262) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- Материал: Cycles 4D ▸ **xpExplosiaFX presets ▸ Burn** на домен; рендер в real-time превью Cycles. [▶ 5:56](https://youtu.be/RkAB9dD0X5k?t=356) — *[2024-04-16](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)*
- **xpExplosiaFX** по умолчанию + сфера с **xpExplosiaFX Source tag** (по умолчанию); смотрим канал Temperature. [▶ 0:24](https://youtu.be/XtaaaiKtl_w?t=24) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- Вкладка **Advection** в xpExplosiaFX активна → дым двигает частицы. [▶ 1:41](https://youtu.be/XtaaaiKtl_w?t=101) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- **Extended Data** emitter: Temperature 1, Fuel 1; добавьте **xpExplosiaFX Source tag** (по умолчанию). [▶ 1:13](https://youtu.be/2YkjQgmo8Ic?t=73) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- xpExplosiaFX ▸ Advection ▸ **Advect Particles** включить. [▶ 3:24](https://youtu.be/2YkjQgmo8Ic?t=204) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- Emitter-источник ▸ вкладка Modifiers: **исключите xpExplosiaFX** — иначе его адвектирует собственный взрыв и он дёргается. [▶ 4:05](https://youtu.be/2YkjQgmo8Ic?t=245) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- System Dynamics ▸ **xpExplosiaFX** (розовый домен). Сфера ▸ Tags ▸ INSYDIUM ▸ тег **xpExplosiaFX Source**, по умолчанию → сразу дым/огонь. [▶ 1:16](https://youtu.be/_G2CwPw4OSY?t=76) — *[2023-08-15](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)*
- Включите эмиттер обратно; xpExplosiaFX ▸ вкладка **Advection** ▸ включите **Advect Particles**. [▶ 2:35](https://youtu.be/_G2CwPw4OSY?t=155) — *[2023-08-15](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)*
- **xpExplosiaFX**: уменьшите домен ручками; Solver ▸ **Voxel Size 4 → 1 см** (частицы с топливом — 2 см). Display: Mode Temperature, вид **Grid**, LOD ~**120%** + прозрачность (Display ▸ Grid ▸ Back показывает воксели). [▶ 9:31](https://youtu.be/EAtbWdajZ4E?t=571) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- Эмиттер осколков ▸ Tags ▸ тег **xpExplosiaFX Source** (по умолчанию). Simulation ▸ **Gravity выкл.** → нет плавучести (buoyancy). [▶ 17:32](https://youtu.be/EAtbWdajZ4E?t=1052) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- xpExplosiaFX ▸ **Advection** вкл. (по умолчанию) → частицы закручиваются вместе со скрытой симуляцией. [▶ 14:43](https://youtu.be/EAtbWdajZ4E?t=883) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*

## Все рецепты (13)
- 2025-10-16 · [Обзор функций: GPU nxExplosiaFX (Fused 2025 Tech Preview)](../../recipes/2025-10-16_feature-notes-nxexplosiafx-tech-preview.md)
- 2024-04-16 · [Изгибаем прямую симуляцию огня по спирали (xpExplosiaFX + C4D Spline Wrap)](../../recipes/2024-04-16_spline-wrap-deformed-explosiafx.md)
- 2024-02-13 · [Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-23 · [Текстовый сплайн, раздуваемый взрывом (xpDynamics на сплайне + адвекция xpExplosiaFX)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-08-15 · [Миллионы частиц, адвектируемых дымом, с аддитивным рендером (xpExplosiaFX Advect Particles, X-Particles material Add blend)](../../recipes/2023-08-15_explosiafx-particle-advection-additive.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Показать меш только там, где сквозь него проходит дым (Point Density в Cycles 4D на меше, эмиттеры xpExplosiaFX со сдвигом)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
