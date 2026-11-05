# xpShatter — карточка инструмента

Встречается в **7** рецептах · 2023-03-29 → 2023-09-27 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Generators ▸ **xpShatter**, plane дочерним объектом. Display: выключить Draw Cut Edges, временно включить **Draw Shatter Points** (одна точка на осколок). [▶ 1:02:10](https://youtu.be/uS_zr-Jf178?t=3730) — *[2023-09-27](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)*
- X-Particles Generators ▸ **xpShatter**; сделай волка его дочерним объектом и **перенеси тег Bullet наверх, на xpShatter** → динамические осколки. [▶ 1:14](https://youtu.be/oY_h7s9RyVI?t=74) — *[2023-07-25](../../recipes/2023-07-25_xpshatter-recursive-bullet.md)*
- UV: перенеси материал на xpShatter; Selections ▸ создай **выделение полигонов внешних граней**, перетащи этот тег в поле Selection материала → снаружи сохраняется UV-развёртка, внутренние грани получают свой материал. [▶ 2:06](https://youtu.be/oY_h7s9RyVI?t=126) — *[2023-07-25](../../recipes/2023-07-25_xpshatter-recursive-bullet.md)*
- **xpSystem**, эмиттер по умолчанию удалить. Generators ▸ **xpShatter**, логотип — дочерний. Display: цвет рёбер почти чёрный. [▶ 21:34](https://youtu.be/U8zISIlBq90?t=1294) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*
- xpShatter ▸ Tags ▸ **xpDynamics** → динамические частицы в каждой вершине. Включите **Push**, Strength **на максимум** → осколки расталкивают друг друга. Точность: Distribution **Vertices + polygon midpoints**, Surface или Volume (медленнее). Выбран вместо Bullet, чтобы модификаторы X-Particles и spawn работали с теми же частицами; считается почти в реальном времени. [▶ 28:39](https://youtu.be/U8zISIlBq90?t=1719) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*
- Материалы: сначала чёрный на xpShatter, потом леденцовый; вкладка Selections ▸ создать polygon selection **outer faces** → в поле Selection леденцового материала. [▶ 29:30](https://youtu.be/U8zISIlBq90?t=1770) — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*
- Эмиттер осколков: xpShatter General ▸ **Auto Particle Radius выкл.** → у всех радиус эмиттера **2 см** (на анимацию не влияет). Extended Data ▸ Physical: **Temperature 1, Fuel 1**. [▶ 2:31](https://youtu.be/EAtbWdajZ4E?t=151) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- Геометрия для эмиссии: дублируйте xpShatter, удалите у копии тег кэша и ссылку на эмиттер (статичная), переименуйте в "Shatter Advection Particles", **Shatter Selections ▸ Inner Faces** → тег выделения полигонов. [▶ 11:29](https://youtu.be/EAtbWdajZ4E?t=689) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- Коллизии: положите закэшированный xpShatter под **xpJoin**, повесьте на join **xpCollider tag**, **Bounce 0**, немного Friction → частицы больше не просачиваются сквозь ещё не разрушенную геометрию. [▶ 17:38](https://youtu.be/EAtbWdajZ4E?t=1058) — *[2023-04-14](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)*
- xpSystem; удалите эмиттер по умолчанию. Generators ▸ **xpShatter**; Inset — дочерний. Слой Voronoi + Point Generator (по умолчанию 40 точек; Display ▸ Draw Shatter Points показывает их). [▶ 2:38](https://youtu.be/75GHeuPO3rU?t=158) — *[2023-04-13](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)*
- xpShatter General ▸ **Add Emitter** → эмиттер в режиме control-only, по одной частице на осколок; **Auto Particle Radius** подгоняет размер под осколок. Выключите Draw Emitter и Show Particles. [▶ 8:25](https://youtu.be/75GHeuPO3rU?t=505) — *[2023-04-13](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)*
- Цифра 4 (xpShatter): для сравнения снять **Display ▸ Draw Cut Edges**; удалить cache tag только у 4, задать **Offset 0.3 cm** — зазор между осколками (тени в швах в духе AO + видно внутренний цвет), затем xpCache **Build Cache ▸ Continue**, чтобы перекэшировать только недостающий объект. С тройкой так НЕ делать. [▶ 20:40](https://youtu.be/j453vKa_ay4?t=1240) — *[2023-03-29](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)*

## Подводные камни
- xpShatter нормально кэшируется через xpCache. — *[2023-04-19](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)*

## Все рецепты (7)
- 2023-09-27 · [«Живой» shatter-обратный отсчёт (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)](../../recipes/2023-09-27_xpshatter-countdown-flowfield-particles-part-c.md)
- 2023-07-25 · [Рекурсивное разрушение при ударе (слои Voronoi в xpShatter с триггером Collision, твёрдые тела Bullet)](../../recipes/2023-07-25_xpshatter-recursive-bullet.md)
- 2023-06-26 · [Обзор функций: новые модификаторы NeXus — nxUpres, nxInfectio, nxWave, nxAvoid, nxFlock, режимы nxBlend, nxFoam на кэшах, nxWind Von Karman (Fused 2023.3)](../../recipes/2023-06-26_feature-notes-nexus-modifiers-2023-3.md)
- 2023-04-19 · [Логотип раскалывается по времени, раскалывается повторно от удара и выпускает обломки и пыль (слои xpShatter + xpDynamics Push + Spawn коллайдера + xpMultiSpawn)](../../recipes/2023-04-19_xpshatter-recursive-dynamics-spawn-debris-part-b.md)
- 2023-04-14 · [Струйки частиц, вырывающиеся из разрушающегося кристалла (cached xpShatter, xpExplosiaFX Source tag, Advection, эмиссия с внутренних граней, xpJoin collider)](../../recipes/2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.md)
- 2023-04-13 · [Кристалл, который осыпается по осколку (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)](../../recipes/2023-04-13_crystal-shatter-xpshatter-question-driven-breakup-part-a.md)
- 2023-03-29 · [Сборка закэшированных сцен в один мастер-файл (xpCache Hold/Offset, скорость Alembic, PolyFX + слоёные поля)](../../recipes/2023-03-29_combining-cached-scenes-retime-offsets.md)
