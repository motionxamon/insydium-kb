# Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)

- Источник: Top Tip Tuesday — Dynamic Sand Simulation — https://www.youtube.com/watch?v=D8XcG_EuvG8 (2025-07-15)
- Хост / поколение: NeXus nxFluids **SPH Granular** + CPU **xpFlowField** + nxSpeed
- Задача: контур логотипа/цветка из дрейфующих песчаных гребней.

## Исходная сцена
Плоскость пола 1000×1000 с xpCollider (bounce 0, friction 12). Круглый эмиттер r 200, поднят на 1 см, rate 1000 (25 000 для финала), lifespan 100 ± 50, speed 0, radius 0.5.
- Ctrl+D: **симуляция на 60 fps, рендер с интерпретацией в 30** → воспроизведение на половинной скорости. После смены fps перепроверьте lifespan (он пересчитывается).

## Шаги
1. **nxGravity 400**; **nxFluids ▸ SPH Granular**, substeps побольше, **Check Density** вкл. (частицы рождаются с перекрытием), friction / stability / cohesion низкие (без слипания в комки). [▶ 1:53](https://youtu.be/D8XcG_EuvG8?t=113)
2. Сплайн-цветок 50/150 см, поднят по Y на 12 см. [▶ 2:32](https://youtu.be/D8XcG_EuvG8?t=152)
3. **xpFlowField** по размеру вокруг него: удалите слой Random по умолчанию → слой **To Spline**, cell size 10, режим **Velocity 300**, falloff выкл. [▶ 4:13](https://youtu.be/D8XcG_EuvG8?t=253)
4. **nxSpeed**: Incremental +0, **Max speed ~65** (успокаивает). [▶ 4:24](https://youtu.be/D8XcG_EuvG8?t=264)
5. Вариативность: flowfield Fields ▸ **Random field** scale 1000, anim speed 100%, кривая Remapping Contour → резкие пятна вкл/выкл. [▶ 4:50](https://youtu.be/D8XcG_EuvG8?t=290)
6. Шейдинг в Redshift; для цвета по маскам см. "Advanced Color Animation" (2025-08-19).

## Как сейчас (новые инструменты)
Fused 2025.4/2026.1: **nxDirection** / потоки в духе nxFollowSpline и GPU flow field в NeXus; в 2026.1 beta — **nxMPM** для песка и снега.
