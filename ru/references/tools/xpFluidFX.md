# xpFluidFX — карточка инструмента

Встречается в **5** рецептах · 2023-03-29 → 2026-10-11 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Добавить **xpFluidFX**; гранулярный режим включается на эмиттере: **Extended Data ▸ Fluid Data ▸ Fluid Type: Granular** → остаются только Friction, Stability, Cohesion (все влияют друг на друга). [▶ 9:38](https://youtu.be/SMO0CZcHa3k?t=578) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- xpFluidFX **Accuracy Fast → High** — granular нужно много substeps/итераций, иначе комки не становятся жёсткими. [▶ 15:01](https://youtu.be/SMO0CZcHa3k?t=901) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- Ключом выключаем чекбокс **Enabled у xpFluidFX** ровно в момент старта взрыва (~F77–78) — два солвера скоростей на одних частицах конфликтуют. [▶ 53:37](https://youtu.be/OKRG2FUtXjc?t=3217) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Ключами выключить **xpGravity** на том же кадре, что и xpFluidFX (75 вкл, 76 выкл) — иначе песок проседает, как только жидкостный солвер останавливается. [▶ 1:38](https://youtu.be/isCt2UKxPtM?t=98) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*

## Все рецепты (5)
- 2026-10-11 · [Высокие кучи песка с auto-sleep, пробуждением от столкновения и хрупким блоком (nxMPM Materials + Auto Sleep + каналы отображения)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Дымовой взрыв по сплайнам, который адвектит живые гранулы (xpExplosiaFX Advection + xpFlowField Along Spline + falloff эмиттера)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
