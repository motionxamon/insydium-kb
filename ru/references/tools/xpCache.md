# xpCache — карточка инструмента

Встречается в **33** рецептах · 2023-03-29 → 2026-09-29 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpCache** (INSYDIUM ▸ Cache): **EFX Format → OpenVDB**; включите **Density, Temperature, Velocity** (velocity обязательна для blur); Fuel можно пропустить. Соберите (≈15 мин на 200 кадров в демо). [▶ 2:14](https://youtu.be/qZyBMJaN6ak?t=134) — *[2026-09-29](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)*
- **xpCache** → EFX Format **OpenVDB**; только каналы **Smoke (density) + Temperature**. Velocity — только если нужен motion blur или адвекция (≈3× размер файлов). [▶ 1:18](https://youtu.be/gfcEhBMSgkI?t=78) — *[2026-05-12](../../recipes/2026-05-12_octane-explosiafx-vdb.md)*
- Кеш мешей: xpCache ▸ Build ▸ **Continue** (не Overwrite) — читает закешированные частицы и добавляет меши (~1 ч 20 мин); затем скройте оба эмиттера. [▶ 53:45](https://youtu.be/Siw3tkJepaU?t=3225) — *[2025-05-14](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)*
- Продакшн: Radius **0.4** → чуть меньше 3 M частиц (для песка в таком кадре автор советует ~6 M). xpCache (compress on build): ~27 мин / 100 F. С теми же настройками взрыв теперь слишком сильный и дробит слишком мелко. [▶ 18:45](https://youtu.be/fxJI8py9BzU?t=1125) — *[2025-05-07](../../recipes/2025-05-07_granular-collapse-sand-snow.md)*
- **xpCache** с **Compress Cache on Build**: 500 F заняли ~20 мин (оценка сначала в часах, но к ~F200 большинство зёрен уже мертвы). Viewport: Dots, Level of Detail **1%**. [▶ 43:57](https://youtu.be/V4mwAf8tcLk?t=2637) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- Если просто уменьшить радиус до 1, детали появятся, но sim будет совсем другим — поэтому вместо этого **закэшируйте sim с радиусом 2** (xpCache ▸ Build Cache). [▶ 2:28](https://youtu.be/GU37kEW507c?t=148) — *[2025-04-15](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)*
- Выпадающие группы: оторвите меню INSYDIUM (клик по его верхней полосе) и перетащите целое подменю — например **MeshTools** или X-Particles ▸ **NeXus** — в палитру; маленькая стрелка значит, что внутри подкоманды. Добавьте и частые одиночные элементы (**xpEmitter**, **xpCache**). [▶ 4:09](https://youtu.be/jzFk-veno5U?t=249) — *[2025-02-27](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)*
- **xpCache**: внешние файлы, сжатие при сборке → Build (2000 F ≈ 1.5 мин в этом примере). [▶ 0:40](https://youtu.be/dA4cn2wx47A?t=40) — *[2024-12-03](../../recipes/2024-12-03_duplicate-particle-caches.md)*
- Перемещение закэшированного эмиттера ничего не меняет → xpCache ▸ **Playback ▸ Local Coordinates** → кэш следует за эмиттером; в режиме Object его можно **масштабировать** (даже неравномерно) и вращать. [▶ 1:40](https://youtu.be/dA4cn2wx47A?t=100) — *[2024-12-03](../../recipes/2024-12-03_duplicate-particle-caches.md)*
- Таймлайн **800** кадров; **xpCache** во внешние файлы со сжатием (~5 мин). [▶ 25:04](https://youtu.be/_W2ivetBEPo?t=1504) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- **xpCache ▸ Build Cache ▸ Continue** (НЕ Overwrite) → симулируется только незакэшированный эмиттер пены, существующий кэш жидкости не трогается (~35 мин, на пике 3M+ частиц пены). [▶ 35:05](https://youtu.be/_W2ivetBEPo?t=2105) — *[2024-11-01](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)*
- xpCache ▸ Playback ▸ Retiming **Time (seconds)**: ключ 0 s на кадре 0 и 500/30 = **16.6 s** на последнем кадре; кривая **Linear**. [▶ 0:52](https://youtu.be/SiDN-95Yk88?t=52) — *[2024-10-29](../../recipes/2024-10-29_retime-cached-meshes.md)*
- **xpCache ▸ Build Cache** (по умолчанию, 200 F). [▶ 3:49](https://youtu.be/c-JysAVC__w?t=229) — *[2024-10-15](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)*
- xpCache ▸ Playback ▸ **Custom**: отметьте только **Velocity** и **Color** — **Radius** оставьте выключенным. [▶ 4:22](https://youtu.be/c-JysAVC__w?t=262) — *[2024-10-15](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)*

## Подводные камни
- xpShatter нормально кэшируется через xpCache. — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*

## Все рецепты (33)
- 2026-09-29 · [nxExplosiaFX → OpenVDB → Redshift с векторным motion blur](../../recipes/2026-09-29_explosiafx-motion-blur-redshift.md)
- 2026-05-26 · [Подводные пузыри от всплеска (адвекция EFX + nxMesher + дымка из частиц)](../../recipes/2026-05-26_underwater-splash-advection.md)
- 2026-05-12 · [Рендер nxExplosiaFX в Octane через OpenVDB](../../recipes/2026-05-12_octane-explosiafx-vdb.md)
- 2026-02-17 · [Перекраска закэшированных частиц через nxColor (и ограничение скорости по цвету)](../../recipes/2026-02-17_recolor-after-cache.md)
- 2025-05-14 · [Вода размывает снежную скульптуру (nxFluids SPH granular + liquid tag, nxGravity с маппингом по Age, xpOpenVDBMesher)](../../recipes/2025-05-14_snow-sculpture-water-sph-granular-liquid.md)
- 2025-05-07 · [Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)](../../recipes/2025-05-07_granular-collapse-sand-snow.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2025-04-15 · [Upres гранулярной симуляции с сохранением формы (кэш в низком разрешении + смешивание velocity через nxUpres)](../../recipes/2025-04-15_upres-granular-sim-nxupres-velocity.md)
- 2025-03-18 · [Motion blur частиц в Redshift (custom shutter, Frame Position для умирающих частиц)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2025-02-27 · [Пристыкованные палитры для инструментов INSYDIUM (C4D Command Manager, отрывные подменю, Lock Icon)](../../recipes/2025-02-27_custom-tool-palettes-c4d.md)
- 2024-12-03 · [Наполняем сцену из одного кэша частиц (локальные координаты xpCache, Copy Tag Data, сдвиг на каждом теге)](../../recipes/2024-12-03_duplicate-particle-caches.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-10-29 · [Рампа замедления на мешированной жидкости (ретайм кэша частиц, затем кэш мешера из ретаймленных частиц)](../../recipes/2024-10-29_retime-cached-meshes.md)
- 2024-10-15 · [Одинаковый размер на рендере при симуляции, завязанной на радиус (каналы xpCache Custom Playback, сферы частиц в Redshift)](../../recipes/2024-10-15_xpcache-custom-playback-uniform-radius.md)
- 2024-09-24 · [Плавные speed ramp в слоу-мо на закэшированных частицах (xpCache Playback Scale / Offset / Retiming Time in seconds)](../../recipes/2024-09-24_xpcache-retime-speed-ramp.md)
- 2024-09-10 · [Многослойный ч/б цвет → перекрашенное аддитивное пламя (nxColor Age × Heading × Pitch, Redshift Color User Data)](../../recipes/2024-09-10_nxcolor-blended-layers-redshift-additive.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2024-02-13 · [Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-30 · [Металлическая табличка с вмятинами от пуль (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-07-11 · [Апрез закешированного сима с малым числом частиц в плотный (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
- 2023-04-19 · [Логотип раскалывается по времени, раскалывается повторно от удара и выпускает обломки и пыль (слои xpShatter + xpDynamics Push + Spawn коллайдера + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Показать меш только там, где сквозь него проходит дым (Point Density в Cycles 4D на меше, эмиттеры xpExplosiaFX со сдвигом)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
