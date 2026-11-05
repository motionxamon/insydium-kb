# xpFlowField — карточка инструмента

Встречается в **7** рецептах · 2023-03-29 → 2025-10-28 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpFlowField** по размеру контейнера: — *[2025-10-28](../../recipes/2025-10-28_liquid-countdown-flowfield.md)*
- **xpFlowField** по размеру вокруг него: удалите слой Random по умолчанию → слой **To Spline**, cell size 10, режим **Velocity 300**, falloff выкл. [▶ 4:13](https://youtu.be/D8XcG_EuvG8?t=253) — *[2025-07-15](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)*
- X-Particles ▸ Dynamics ▸ **xpFlowField**; растяните его границы на весь сплайн (частицы реагируют только внутри). [▶ 0:41](https://youtu.be/zA6fTkWvwwI?t=41) — *[2023-10-03](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)*
- Dynamics ▸ **xpFlowField**: подогнать bounds под текст; Display Arrow (voxels, чтобы видеть все); **Cell size 15**. [▶ 1:07:33](https://youtu.be/uS_zr-Jf178?t=4053) — *[2023-09-27](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)*
- **xpFlowField**: flow **Along Spline**, линкуем splines, **falloff выкл.**, cell size 40 → ~17–18 см, **Strength ~40** (по умолчанию слишком слабо, частицы не долетают до «1»). [▶ 32:05](https://youtu.be/OKRG2FUtXjc?t=1925) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- **xpExplosiaFX ▸ Modifiers**: добавляем xpFlowField, чтобы и сам дым толкало вдоль сплайнов. Траектории можно поджать, масштабируя точки сплайна внутрь. [▶ 38:54](https://youtu.be/OKRG2FUtXjc?t=2334) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Изоляция: System EFX ▸ **Only Modifiers in Same System** вкл. Эмиттер гранул ▸ Modifiers ▸ **Exclude** — xpFlowField (адвекцию от EFX он видеть должен). [▶ 42:18](https://youtu.be/OKRG2FUtXjc?t=2538) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Spawn-эмиттер ▸ Modifiers: переключить **Exclude → Include** и оставить только xpExplosiaFX + xpFlowField (позже xpScale) — сам spawn-модификатор не включаем, чтобы не было рекурсивного спавна. [▶ 46:01](https://youtu.be/isCt2UKxPtM?t=2761) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*
- Сходящиеся векторы давали тонкую линию дыма по −Z → **xpFlowField Falloff ▸ Box field** в центре, Remapping **Invert**, чтобы потоки проходили сквозь друг друга. [▶ 26:41](https://youtu.be/isCt2UKxPtM?t=1601) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*

## Все рецепты (7)
- 2025-10-28 · [Жидкий обратный отсчёт: жидкость течёт по анимированным сплайнам цифр (xpFlowField + nxFoam)](../../recipes/2025-10-28_liquid-countdown-flowfield.md)
- 2025-07-15 · [Песок, который собирается в форму сплайна (гранулярный SPH + слой To-Spline в xpFlowField)](../../recipes/2025-07-15_dynamic-sand-flowfield-spline.md)
- 2023-10-03 · [Частицы, органично текущие вдоль сплайна (слои xpFlowField Along Spline + Curl + To Spline)](../../recipes/2023-10-03_xpflowfield-along-spline-curl.md)
- 2023-09-27 · [«Живой» shatter-обратный отсчёт (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-29 · [Показать меш только там, где сквозь него проходит дым (Point Density в Cycles 4D на меше, эмиттеры xpExplosiaFX со сдвигом)](../../recipes/2023-03-29_cycles4d-point-density-smoke-reveal.md)
