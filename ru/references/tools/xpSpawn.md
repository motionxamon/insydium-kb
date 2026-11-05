# xpSpawn — карточка инструмента

Встречается в **7** рецептах · 2023-03-21 → 2024-03-12 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpSpawn** ▸ Add Emitter («emitter spawn»); спаун в позиции исходной частицы, Direction **Random Spherical**, скорость спауна **Absolute** (берётся из нового эмиттера). Скорость spawn-эмиттера **100** (var 80); спаун **75** в кадр (var 15) вместо 300. [▶ 3:59](https://youtu.be/PpDwpKu8478?t=239) — *[2024-03-12](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)*
- **xpSpawn** (модификаторы Generate) ▸ **Add Emitter** → «emitter spawn»: Draw Emitter выкл., **Dots**, Gradient Parameter (фиолетовый пресет) по **Speed**, min 10 / max 200; скорость 0, lifespan 50 (вариация 25). [▶ 3:22](https://youtu.be/XtaaaiKtl_w?t=202) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- xpSpawn: спавн из позиций исходных частиц, остальное по умолчанию; количество 300 → **10/кадр**, затем **50** — заспавненные частицы адвектируются тем же закэшированным дымом. [▶ 4:23](https://youtu.be/XtaaaiKtl_w?t=263) — *[2024-02-13](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)*
- Искры: **xpSpawn**, исключите его на вкладке Modifiers стартового эмиттера; новый spawn-эмиттер: lifespan 10 (var 5), speed 200 (var 150), отображение **Lines**, тонкие, оранжевые; spawn 60 (var 20) за кадр, направление по умолчанию сферическое. [▶ 5:56](https://youtu.be/sctuPLrOw60?t=356) — *[2024-01-16](../../recipes/2024-01-16_mtsplinefx-lightning.md)*
- Отключите тег кэша у эмиттера ткани. **xpSpawn** (Generate) ▸ Add spawning emitter → "Emitter Spawn"; позиция = **Source Particle**, скорость **Absolute** при скорости эмиттера **0** (их двигает только адвекция). [▶ 3:28](https://youtu.be/xoJcz9u3c8g?t=208) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)*
- xpSpawn: **10 на кадр** (300/с по умолчанию — слишком много), **Spawn Once Only**, life Absolute → жизнь эмиттера **15 F, вариация 5**; **Groups Affected** = incubated + infected (спавн только там, где идёт горение). **Offset 2–3 см**, чтобы 10 частиц не сидели друг на друге. **Radius 1.5** у заспавненных. [▶ 6:29](https://youtu.be/xoJcz9u3c8g?t=389) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)*
- **Заполнить дыры от advection через xpSpawn**: Generate ▸ xpSpawn → создать spawn-эмиттер (на время настройки розовый). Position = исходная частица, Direction относительно источника, Speed **inherit × 0.5**, Spawn Number **10**/с. Вкладка Inherit: **Color + Radius**. [▶ 18:09](https://youtu.be/isCt2UKxPtM?t=1089) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*
- Modifiers ▸ Generate ▸ **xpMultiSpawn** (в отличие от xpSpawn ему не нужен отдельный эмиттер для спавна). Уровень по умолчанию: 10 новых на каждую исходную частицу в возрасте 0, в течение одного кадра. [▶ 0:39](https://youtu.be/XwQyDoAPNa4?t=39) — *[2023-03-21](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)*

## Все рецепты (7)
- 2024-03-12 · [Режущий лазер с искрами (эмиттер в contact points mtRayline + xpTrail + xpSpawn)](../../recipes/2024-03-12_mtrayline-cutting-laser-sparks.md)
- 2024-02-13 · [Уплотняем закэшированную адвекционную симуляцию спавном (xpCache + xpExplosiaFX Advection + xpSpawn)](../../recipes/2024-02-13_xpspawn-from-cached-advection.md)
- 2024-01-16 · [Процедурная ветвящаяся молния с искрами (mtSplineFX + xpSplineMesher + xpSpawn)](../../recipes/2024-01-16_mtsplinefx-lightning.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-03-29 · [Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)](../../recipes/2023-03-29_explosiafx-high-res-resim-from-spawned-particles.md)
- 2023-03-29 · [Дым разрывает песочную цифру без дыр (advection в xpExplosiaFX, xpFlowField, заполнение xpSpawn, xpScale + kill через Question)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
- 2023-03-21 · [Три поколения спавна из одного эмиттера (уровни xpMultiSpawn + группы для отображения)](../../recipes/2023-03-21_xpmultispawn-layered-spawning-groups.md)
