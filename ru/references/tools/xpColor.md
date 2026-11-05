# xpColor — карточка инструмента

Встречается в **6** рецептах · 2023-03-29 → 2026-06-02 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpColor** (CPU) с **Noise shader** Maxon: **Cell Voronoi**, global scale ~330, сильный low/high clip → пятнистый чёрно-белый цвет на частицах. (CPU-модификатор взят потому, что он сэмплит шейдеры Maxon в полном 3D; у nxColor GPU-нойзы.) [▶ 1:18](https://youtu.be/zyN7ERz7yuw?t=78) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- Чтобы узор иногда перескакивал: ключи на **Seed** нойза (+1 каждые 2 кадра, linear, Track After: Continue) и ключи на **Enabled** у xpColor вкл./выкл. импульсами (кадры 0–2, 50, 100, 150) → перекраска только в нужные моменты. [▶ 2:42](https://youtu.be/zyN7ERz7yuw?t=162) — *[2026-06-02](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)*
- **xpColor** с шейдером Maxon **Noise (Voronoi)**, огромный масштаб, с клиппингом, animation speed ~7 → движущиеся чёрно-белые пятна. [▶ 1:04](https://youtu.be/PTamR793O-k?t=64) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- **xpColor**, режим **Immediate**, Shader **Gradient** (Spherical) с пресетом, **Turbulence 20%**. [▶ 5:24](https://youtu.be/M4z3kOU4YEw?t=324) — *[2023-12-19](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)*
- Основная система: **xpColor** (CPU) Set Color белый (не Immediate). Эмиттеры-заразители ▸ Editing ▸ **Editable**, чтобы Fields видели их как точки; перетащите их в Fields у xpColor, режим **Max**, radius 3 → 5 (больше = быстрее распространение; больше заразителей тоже ускоряет). [▶ 49:05](https://youtu.be/qaso-gPGBnI?t=2945) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*
- **xpColor** ▸ Shader = **Noise**, тип **Blistered Turbulence**, Global Scale **500%**, Animation Speed **0.3**; поднять Brightness/Contrast, чтобы белыми остались только яркие пятна — белые частицы будут расти, тёмные останутся маленькими. [▶ 20:03](https://youtu.be/uS_zr-Jf178?t=1203) — *[2023-09-27](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)*
- Цвет для рендера: **xpColor** ▸ Gradient by Parameter ▸ **3D Linear**, ось Z, Min −12.5 / Max 12.5, **Change on Birth Only**; градиент чёрный → белый, чтобы перекрасить на рендере, а в трещинах проступали светлые внутренние песчинки. [▶ 18:08](https://youtu.be/SMO0CZcHa3k?t=1088) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*

## Все рецепты (6)
- 2026-06-02 · [Гранулярный текст, который разносят порывы ветра с маппингом на анимированный цвет Voronoi](../../recipes/2026-06-02_advanced-granular-wind-gusts.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2023-12-19 · [Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)](../../recipes/2023-12-19_xptendril-trail-tip-underwater.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-09-27 · [Самоорганизующиеся «дышащие» кластеры сфер (xpColor noise → xpQuestion radius, nxPush mapped, nxConstraints Bind + Friction, Cycles 4D)](../../recipes/2023-09-27_breathing-sphere-clusters-noise-radius-part-a.md)
- 2023-03-29 · [Песочная цифра, которая рассыпается на комки (xpFluidFX Granular, Hexagonal-заполнение, анимированный falloff гравитации)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
