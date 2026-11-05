# xpConstraints — карточка инструмента

Встречается в **6** рецептах · 2023-02-21 → 2024-01-30 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpConstraints ▸ Viscosity** включить (это тип соединения) — частицы связываются (проверка через Display Constraints). [▶ 1:14](https://youtu.be/rhFYjdNe2XA?t=74) — *[2023-06-12](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)*
- **xpConstraints ▸ Connections ▸ Birth Connections** включить с дефолтами → сразу получается вид сетки. [▶ 4:14](https://youtu.be/WeuXOmENNXA?t=254) — *[2023-06-12](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)*
- Решение: **xpConstraints ▸ Connections ▸ Distance** (birth connections не работают для постоянно новых частиц). Дефолты: радиус **40 cm**, до **8** связей. Для проверки включить Display Constraints. [▶ 5:42](https://youtu.be/KBktASa5O2o?t=342) — *[2023-06-12](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)*
- Включить **xpConstraints ▸ Forces**. Дефолтный радиус притяжения 20 cm слишком мал для логотипа в 400 cm → **Attraction Radius 400**, **Limit** связей **16 → 50**. [▶ 3:42](https://youtu.be/dnyn6Lrj8-A?t=222) — *[2023-06-08](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)*
- Быстрее всего: Dynamics ▸ **xpConstraints** ▸ включить вкладку **Collisions**. Одна настройка — **Stiffness**. Быстро, базово. [▶ 0:47](https://youtu.be/GGI1MyewI2g?t=47) — *[2023-02-21](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)*

## Все рецепты (6)
- 2024-01-30 · [Металлическая табличка с вмятинами от пуль (xpClothFX plasticity + damping)](../../recipes/2024-01-30_xpcloth-plastic-dents.md)
- 2023-06-12 · [Быстрая вязкая струя шоколада/мёда (xpFluidPBD + xpConstraints Viscosity, эмиссия Hexagonal)](../../recipes/2023-06-12_viscous-pour-xpconstraints-fluidpbd.md)
- 2023-06-12 · [Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)](../../recipes/2023-06-12_tearing-net-constraints-wind-change-group.md)
- 2023-06-12 · [Извивающиеся щупальца, которые держат констрейнты (xpTendril, xpConstraints Distance Connections + Collisions, xpTrail ▸ Tendrils)](../../recipes/2023-06-12_dynamic-tendrils-distance-constraints.md)
- 2023-06-08 · [Фейковая тягучая жидкость, ползущая по логотипу (xpConstraints Forces, xpCover, Data Mapping по radius/age/temperature, xpOpenVDBMesher)](../../recipes/2023-06-08_constraint-forces-blob-cover-target-mapping.md)
- 2023-02-21 · [Три способа заставить частицы сталкиваться друг с другом (xpConstraints Collisions, xpPPCollisions, xpBullet)](../../recipes/2023-02-21_particle-collisions-constraints-ppcollisions-bullet.md)
