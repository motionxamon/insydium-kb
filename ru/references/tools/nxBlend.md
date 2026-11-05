# nxBlend — карточка инструмента

Встречается в **13** рецептах · 2023-04-19 → 2026-09-08 · хосты: Blender, C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **nxBlend** ▸ Color, режим **Addition**, Distance **0.04 → 0.07**, Strength **500%** (может быть больше 100) → белый расползается по мокрому песку; задайте max/stop frame (148, затем **110**), чтобы остались твёрдые чёрные комки. [▶ 11:30](https://youtu.be/yp5579on6J8?t=690) — *[2026-09-08](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)*
- **nxBlend** Color, **Blend: Addition**, сила на максимум, distance ~6 cm → белый расходится на соседей (остывание) и никогда не темнеет. [▶ 5:49](https://youtu.be/VCGNxYZt21k?t=349) — *[2026-02-03](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)*
- **nxBlend**: только Color (по умолчанию), **Strength 1000%** (максимум), Distance **3 см** (10 см = грязь; 2 см = смешивание только на швах). [▶ 4:27](https://youtu.be/ldpeVYB30QA?t=267) — *[2025-09-23](../../recipes/2025-09-23_paint-mix-nxblend.md)*
- **nxBlend** Color, **Addition**, Distance 15, **Strength 1000%** → белые (горячие) частицы осветляют чёрные при контакте = повторное плавление. [▶ 6:59](https://youtu.be/_k0LatnQQJw?t=419) — *[2025-09-09](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)*
- **nxBlend**: режим Addition, только Color, radius 5, **Strength ~1000** → белое расползается по тёмным пятнам, пока всё не станет белым. [▶ 11:56](https://youtu.be/V4mwAf8tcLk?t=716) — *[2025-04-30](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)*
- **nxBlend**: по умолчанию смешивает Color (также scale, rotation, mass, radius). Стандартная сила 10% слишком слабая → **200%**; distance 10 cm; max blend duration 300 F. [▶ 4:08](https://youtu.be/IG5GdX9U4lM?t=248) — *[2024-03-05](../../recipes/2024-03-05_nxblend-paint-mix.md)*
- Сделайте заразителей белыми. **nxBlend**: режим **Addition** (передаются только более яркие значения), Distance 5, Strength 100, Color → плавное градиентное распространение. [▶ 50:51](https://youtu.be/qaso-gPGBnI?t=3051) — *[2023-11-16](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)*
- **nxBlend** (под гравитацией): Color, Distance **20 cm**, Strength **1000** (максимум), длительность **40** кадров (по умолчанию 300) → смешение синего/белого = теплообмен. Тяжёлый поиск соседей, на GPU быстро. [▶ 1:18:53](https://youtu.be/6WjDq_87uck?t=4733) — *[2023-07-05](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)*
- Распространение тепла: **nxBlend**, режим **Additive**, Distance **50**, Strength на максимум, время blend **60 → 90** кадров. [▶ 58:45](https://youtu.be/U8zISIlBq90?t=3525) — *[2023-04-19](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)*

## Все рецепты (13)
- 2026-09-08 · [Струя воды размывает комковатый песок (nxFluids SPH Granular + жидкость в Mixer, цвет nxBlend → mapped-настройки granular)](../../recipes/2026-09-08_sand-water-mix-blend-mapped-granular.md)
- 2026-04-14 · [Зацикленные цветовые волны, запускаемые касанием (переключатель-переменная в nxQuestion + nxBlend)](../../recipes/2026-04-14_nxquestion-looping-switch-color-waves.md)
- 2026-02-03 · [Расплавленный шоколад, застывающий при контакте (переменная вязкость APIC по цвету)](../../recipes/2026-02-03_chocolate-setting-variable-viscosity.md)
- 2025-11-26 · [Обзор функций: жидкости в Fused 2025 — GPU FLIP/APIC с вязкостью, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2025-09-30 · [Меширование симуляции смешивания красок и рендер цвета вершин (xpOpenVDBMesher → Redshift)](../../recipes/2025-09-30_paint-mix-meshing-vertex-color.md)
- 2025-09-23 · [Смешивание краски из трёх цветных эмиттеров (nxBlend + маппинг по скорости)](../../recipes/2025-09-23_paint-mix-nxblend.md)
- 2025-09-09 · [Горячая текучая / холодная тягучая жидкость, которая снова плавится при контакте (группы + nxBlend + mapping вязкости)](../../recipes/2025-09-09_hot-cold-variable-viscosity.md)
- 2025-04-30 · [Процедурное рассыпание песочного бюста (nxFluids SPH Granular + группы через nxColor/nxQuestion + nxWind Von Karman + зерно с mapping по дистанции)](../../recipes/2025-04-30_sand-disintegration-granular-nxquestion-groups.md)
- 2024-03-05 · [Смешивание густых красок (nxFluids SPH + nxConstraints Viscosity + nxBlend)](../../recipes/2024-03-05_nxblend-paint-mix.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-07-05 · [Горячая/холодная жидкость с переменной вязкостью на голову волка (nxFluids SPH + nxConstraints Viscosity + nxQuestion object distance + nxBlend + nxSpeed clamp с mapping по цвету)](../../recipes/2023-07-05_variable-viscosity-wolf-nxspeed-clamp-part-b.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-04-19 · [Интерактивный риг плавления / застывания на цвете частиц (mapping Clamp Max Speed в nxSpeed + nxQuestion с fields + nxBlend + mapping вязкости SPH)](../../recipes/2023-04-19_nexus-heat-cool-melt-rig-nxquestion-mapping-part-c.md)
