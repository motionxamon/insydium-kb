# xpGenerator — карточка инструмента

Встречается в **13** рецептах · 2023-02-21 → 2026-08-04 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Инстансим несферические формы через **xpGenerator** (случайные дочерние объекты, **Multi-Instance** — самый быстрый вариант). Проблема: инстансы сохраняют ориентацию и скользят. [▶ 4:58](https://youtu.be/OFx-ALGOlAU?t=298) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- Цвет на частицу (например, градиент nxColor по Speed, 0–300 cm/s) **не** отображается при **Multi-Instance** (всё считается одним объектом) → переключаем xpGenerator на **Render Instances** (медленнее). [▶ 5:49](https://youtu.be/OFx-ALGOlAU?t=349) — *[2026-08-04](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)*
- xpGenerator **Render Instances** из Platonic; Extended Data **Use Rotation → Random**. [▶ 8:50](https://youtu.be/PTamR793O-k?t=530) — *[2025-10-07](../../recipes/2025-10-07_collider-attraction-surface-push.md)*
- XP System ▸ Generators ▸ **xpGenerator** на каждый эмиттер (переименуйте в "generator main", "generator lights"); копируемая геометрия — **дочерняя** к генератору. [▶ 1:30](https://youtu.be/eBnMW0v43Ac?t=90) — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*
- Цели для ответвлений: **xpGenerator** с редактируемой Sphere (**12 segments**), привязанный к эмиттеру → сфера на каждую частицу (скройте их). [▶ 4:57](https://youtu.be/UXqS-dqsHiM?t=297) — *[2025-08-07](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)*
- Для рендера инстансите геометрию листа тегом вашего рендера или через **xpGenerator**. [▶ 0:54](https://youtu.be/zG0XcLByiG4?t=54) — *[2025-03-04](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)*
- **xpGenerator** от emitter, дочерние объекты = 4 однополигональные плоскости с материалами листьев с alpha-вырезом; **Multiple children ▸ Random**, тип клонов **Multi-Instance**. [▶ 5:02](https://youtu.be/RRKxOyJVrO8?t=302) — *[2024-05-07](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)*
- Снежинки: три сплайна Flower в объектах **Extrude** как дочерние у **xpGenerator** (эмиттер подключён), режим для нескольких детей Random, тип клонов **Multi-Instances** ради скорости во viewport. (С Redshift/Octane/Cycles 4D лучше инстансить на этапе рендера.) [▶ 5:35](https://youtu.be/RnIGtMwTpLg?t=335) — *[2023-12-26](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)*

## Подводные камни
- Для геометрии xpGenerator используйте Object Color, а не Particle Color. — *[2025-08-26](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)*

## Все рецепты (13)
- 2026-08-04 · [Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"](../../recipes/2026-08-04_rolling-particles-nxspin-roll.md)
- 2026-06-09 · [Случайная ориентация при рождении + повторяемые обороты на 360° (nxSpin + сброс возраста)](../../recipes/2026-06-09_advanced-spin-control.md)
- 2026-01-20 · [Колышущееся поле клонов: режим nxTurbulence "Direction" + nxSpin Tangential + nxLimit](../../recipes/2026-01-20_nxturbulence-direction-mode-clones.md)
- 2025-10-07 · [Пульсирующие частицы расталкивают друг друга, прижимаясь к поверхности (притяжение коллайдера)](../../recipes/2025-10-07_collider-attraction-surface-push.md)
- 2025-08-26 · [Частицы → rigid body в C4D с цветом от nxColor (xpGenerator + теги Simulation + Redshift Object Color)](../../recipes/2025-08-26_particle-rigid-bodies-nxcolor.md)
- 2025-08-07 · [Процедурный плазменный шар (nxFollowGeo + nxTurbulence на частицах, дуги mtSplineFX, ответвления от пересечений mtEdgeSpline)](../../recipes/2025-08-07_procedural-plasma-ball-mtsplinefx.md)
- 2025-07-24 · [Обзор функций: слои nxSpin, Noise/Neighbor-градиент в nxColor, Direction Force в nxDirection (превью Fused 2025, часть 2)](../../recipes/2025-07-24_feature-notes-nxspin-nxcolor-noise-nxdirection-force.md)
- 2025-03-04 · [Листья, сорванные ветром с дерева Taiao (листья-эмиттер Taiao + nxWind Von Karman + nxQuestion Field/Random + xpSpin с маппингом на Speed)](../../recipes/2025-03-04_taiao-leaves-to-particles-blow-off.md)
- 2024-05-07 · [Реалистичные листья на порывистом ветру (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)](../../recipes/2024-05-07_von-karman-gusty-wind-leaves.md)
- 2023-12-26 · [Естественный падающий снег (ограничение nxSpeed, замапленное на радиус + второй nxTurbulence Curl с Blend, замапленным на радиус)](../../recipes/2023-12-26_nxspeed-radius-mapped-snow-rig.md)
- 2023-07-05 · [Электрические дуги, кабели и искры от лазерного прожига (mtSplineFX + mtRayline + nxQuestion Spawn)](../../recipes/2023-07-05_mtsplinefx-arcs-rayline-laser-sparks-part-c.md)
- 2023-06-23 · [Обзор функций: X-Particles 2023.3 — живой spawn/foam из кэшей, multi-instances, вращение прилипших частиц, xpSplineMesher Planar (Fused 2023.3)](../../recipes/2023-06-23_feature-notes-x-particles-2023-3-cache-spawn-foam.md)
- 2023-02-21 · [Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
