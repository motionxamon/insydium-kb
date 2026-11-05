# xpGravity — карточка инструмента

Встречается в **8** рецептах · 2023-03-29 → 2026-03-24 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Частицы крутятся по орбите вокруг сферы с **xpGravity Type Newton** (сфера — аттрактор; её опция масштаба делает частицы крупнее рядом со сферой). [▶ 0:32](https://youtu.be/iPYPQGaz7zQ?t=32) — *[2026-03-24](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)*
- **xpGravity** (по умолчанию) тянет искры вниз. — *[2024-03-12](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)*
- **xpGravity** с уменьшенной силой; Draw Emitter выкл. Двигайте сферу, чтобы управлять разрядами. [▶ 6:45](https://youtu.be/sctuPLrOw60?t=405) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- **xpGravity** (Motion modifiers), вариация **150**; выключите Visible in Editor, чтобы спрятать иконку. [▶ 1:20](https://youtu.be/x1SAOjOSOzs?t=80) — *[2023-08-22](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)*
- xpGravity ▸ вкладка **Mapping** ▸ Add map. Parameter = **Gravity Strength** (можно выбрать любой параметр гравитации). [▶ 1:31](https://youtu.be/QqtVVMajP5k?t=91) — *[2023-07-04](../../recipes/2023-07-04_xp-data-mapping-gravity-strength.md)*
- **xpGravity** повернуть на 90°, чтобы тянула в +Z (от камеры); бокс **xpKill** позади сцены убирает упавшие песчинки. — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- Ключами выключить **xpGravity** на том же кадре, что и xpFluidFX (75 вкл, 76 выкл) — иначе песок проседает, как только жидкостный солвер останавливается. [▶ 1:38](https://youtu.be/isCt2UKxPtM?t=98) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*

## Все рецепты (8)
- 2026-03-24 · [Огонь испускают только быстрые (или крупные) частицы — маппинг источника EFX](../../recipes/2026-03-24_efx-emission-mapped-to-particle-data.md)
- 2024-03-12 · [Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2024-01-30 · [Металлическая табличка с вмятинами от пуль (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2024-01-16 · [Процедурная ветвящаяся молния с искрами (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-08-22 · [Риг дождя с брызгами (xpCollider Spawn при столкновении, xpJoin для нескольких коллайдеров)](../../recipes/2023-08-22_rain-rig-collider-spawn-splashes.md)
- 2023-07-04 · [Основы Data Mapping: сила гравитации от радиуса, яркости цвета или пользовательского значения (вкладка Mapping в xpGravity, Extended Data User Value)](../../recipes/2023-07-04_xp-data-mapping-gravity-strength.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
