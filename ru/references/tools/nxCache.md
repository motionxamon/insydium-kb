# nxCache — карточка инструмента

Встречается в **13** рецептах · 2023-03-29 → 2026-10-07 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxCache** на res 120 (~2 мин в демо). — *[2026-10-07](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)*
- **nxCache** ▸ Build Cache (здесь ~40 s), затем отключите солверы/модификаторы. [▶ 5:29](https://youtu.be/M2yxZlZQBec?t=329) — *[2026-10-06](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)*
- **Вкладка Render ▸ VDB Output: Live** → временная VDB-последовательность, автоматический объект Blender Volume, подключённый ко всем каналам, пресетный материал огня/дыма; сим остаётся живым (cache не нужен). Альтернативы: nxCache или экспорт VDB + импорт volume в Blender. [▶ 22:11](https://youtu.be/RH6ukNvt-No?t=1331) — *[2026-06-25](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)*
- Таймлайн 300 F, **nxCache** по умолчанию ▸ Build Cache (~20–30 s), затем отключите живые объекты. [▶ 15:28](https://youtu.be/na6NGPw4XWM?t=928) — *[2026-06-18](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)*

## Все рецепты (13)
- 2026-10-07 · [Вода, резиновые мармеладки и песок в одном solve, с мешингом и рендером (nxMPM Materials + nxMesher + point cloud, Cycles)](../../recipes/2026-10-07_nxmpm-water-rubber-sand-mix.md)
- 2026-10-06 · [Убираем гексагональную сетку в закэшированной сыпучей симуляции (Create Point Cloud + jitter в Geometry Nodes)](../../recipes/2026-10-06_granular-grid-jitter-geometry-nodes.md)
- 2026-06-25 · [Огонь с горением топлива и дым с живым рендером в Cycles (источники nxExplosiaFX, силы, Adaptive Bounds, VDB Output Live)](../../recipes/2026-06-25_blender-explosiafx-fire-live-vdb-render.md)
- 2026-06-18 · [Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)](../../recipes/2026-06-18_blender-follow-curve-pbd-liquid-motion-blur.md)
- 2025-03-18 · [Motion blur частиц в Redshift (custom shutter, Frame Position для умирающих частиц)](../../recipes/2025-03-18_redshift-particle-motion-blur-frame-position.md)
- 2024-11-01 · [Бурлящая закрученная вода, видимая только через пену (nxFluids + nxVorticity с Force Limit + анимированный nxRotate → nxFoam с цветом по скорости)](../../recipes/2024-11-01_nxvorticity-swirling-fluid-nxfoam-part-1.md)
- 2024-04-30 · [Органичный рой частиц-trail'ов из низкополигонального кэша (nxConstraints + nxTurbulence → nxUpres)](../../recipes/2024-04-30_nxupres-stylised-particle-trails.md)
- 2024-03-15 · [Песок, сдуваемый ветром с дюны (дюна через TerraformFX tfSpline + nxWind Von Karman, nxAvoid, nxTurbulence в ограниченной зоне)](../../recipes/2024-03-15_desert-dunes-nxwind-sand-particles.md)
- 2023-11-20 · [Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)](../../recipes/2023-11-20_nxfluids-sph-art-directed-particle-splash.md)
- 2023-11-16 · [Кристаллы, прорастающие вдоль замерших путей частиц (xpFollowSurface + xpAvoid Freeze, nxQuestion Spawn, nxScale age mapping, Cycles 4D instances)](../../recipes/2023-11-16_crystal-spawn-trails-nxquestion-cycles4d.md)
- 2023-07-11 · [Апрез закешированного сима с малым числом частиц в плотный (xpCache + nxUpres Velocity / Position / Push)](../../recipes/2023-07-11_nxupres-cached-low-res-sim.md)
- 2023-03-29 · [Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)](../../recipes/2023-03-29_hq-explosiafx-swap-cycles4d-render-setup.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
