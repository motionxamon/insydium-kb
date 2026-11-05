# xpDynamics — карточка инструмента

Встречается в **5** рецептах · 2023-04-19 → 2024-02-06 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Отключите MeshTools; на сферу добавьте **xpDynamics tag ▸ add Emitter** (по частице на вершину). [▶ 3:02](https://youtu.be/3YmhMKdK0o4?t=182) — *[2024-02-06](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)*
- Текстовый сплайн ▸ **xpDynamics tag** → по частице на каждую промежуточную точку. В теге **добавьте Emitter** («emitter dynamic») — для адвекции нужны настоящие частицы emitter-а. [▶ 2:54](https://youtu.be/2YkjQgmo8Ic?t=174) — *[2024-01-23](../../recipes/2024-01-23_xpdynamics-spline-advection.md)*
- На торе: Tags ▸ X-Particles ▸ **xpDynamics** — рождает динамические частицы на каждой вершине. [▶ 2:20](https://youtu.be/3cWjs6bgjBI?t=140) — *[2023-11-07](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)*
- xpDynamics ▸ Properties ▸ **Add Emitter** → переименовываем в "emitter dynamic", Display ▸ Draw Emitter выключаем, прячем его частицы; Ctrl-перетаскиванием копируем на него тег nxFluids. [▶ 4:41](https://youtu.be/3cWjs6bgjBI?t=281) — *[2023-11-07](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)*
- xpShatter ▸ Tags ▸ **xpDynamics** → динамические частицы в каждой вершине. Включите **Push**, Strength **на максимум** → осколки расталкивают друг друга. Точность: Distribution **Vertices + polygon midpoints**, Surface или Volume (медленнее). Выбран вместо Bullet, чтобы модификаторы X-Particles и spawn работали с теми же частицами; считается почти в реальном времени. [▶ 28:39](https://youtu.be/U8zISIlBq90?t=1719) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*

## Все рецепты (5)
- 2024-02-06 · [Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)](../../recipes/2024-02-06_meshtools-xpdynamics-soft-body.md)
- 2024-01-23 · [Текстовый сплайн, раздуваемый взрывом (xpDynamics на сплайне + адвекция xpExplosiaFX)](../../recipes/2024-01-23_xpdynamics-spline-advection.md)
- 2023-11-16 · [Астероиды на орбитах планет + расползающееся свечение (nxAttract Force/Speed Limit, xpColor с полями из частиц, nxBlend Addition)](../../recipes/2023-11-16_nxattract-planet-orbits-color-infection-part-b.md)
- 2023-11-07 · [Плавающий / тонущий объект в жидкости NeXus (тег xpDynamics + плотность в nxFluids tag на эмиттер)](../../recipes/2023-11-07_xpdynamics-floating-object-nxfluids-tag.md)
- 2023-04-19 · [Логотип раскалывается по времени, раскалывается повторно от удара и выпускает обломки и пыль (слои xpShatter + xpDynamics Push + Spawn коллайдера + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
