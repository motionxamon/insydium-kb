# Логотип раскалывается по времени, раскалывается повторно от удара и выпускает обломки и пыль (слои xpShatter + xpDynamics Push + Spawn коллайдера + xpMultiSpawn)

- Источник: INSYDIUM LIVE! — April 2023 - X-Particles, NeXus & MeshTools — https://www.youtube.com/watch?v=U8zISIlBq90 (2023-04-19)
- Хост / поколение: C4D; G1 CPU (xpShatter, xpDynamics, xpCollider, xpDrag, xpMultiSpawn)
- Задача: экструдированный логотип разбивается на кадре 30, анимированный куб, пролетая сквозь него, разбивает осколки ещё раз, а удары порождают куски и мелкую пыль.

## Исходная сцена
Сплайн логотипа в Extrude (всё процедурно). Заранее анимированный ключами **Cube**, проходящий сквозь логотип (сначала скрыт). Два материала: тёмный внутри, «леденцовый» снаружи.

## Шаги
1. **xpSystem**, эмиттер по умолчанию удалить. Generators ▸ **xpShatter**, логотип — дочерний. Display: цвет рёбер почти чёрный. [▶ 21:34](https://youtu.be/U8zISIlBq90?t=1294)
2. Вкладка Object: стек слоёв **Voronoi** + Point Generator (40 точек) → **13** точек, перебор Seed. [▶ 22:18](https://youtu.be/U8zISIlBq90?t=1338)
3. Вкладка General ▸ Emitter ▸ **Add** → «emitter shatter»: по частице на осколок, радиус по размеру осколка (видно в Display **Circles**). Любой модификатор на этих частицах двигает осколки. [▶ 24:31](https://youtu.be/U8zISIlBq90?t=1471)
4. xpShatter ▸ Tags ▸ **xpDynamics** → динамические частицы в каждой вершине. Включите **Push**, Strength **на максимум** → осколки расталкивают друг друга. Точность: Distribution **Vertices + polygon midpoints**, Surface или Volume (медленнее). Выбран вместо Bullet, чтобы модификаторы X-Particles и spawn работали с теми же частицами; считается почти в реальном времени. [▶ 28:39](https://youtu.be/U8zISIlBq90?t=1719)
5. Материалы: сначала чёрный на xpShatter, потом леденцовый; вкладка Selections ▸ создать polygon selection **outer faces** → в поле Selection леденцового материала. [▶ 29:30](https://youtu.be/U8zISIlBq90?t=1770)
6. Dynamics tag ▸ Properties: добавьте эмиттер («emitter dynamics») для большего контроля; радиус задаётся в теге (эмиттер обновится сам). [▶ 30:14](https://youtu.be/U8zISIlBq90?t=1814)
7. Первый слой Voronoi ▸ Trigger **Time = 30 F**. [▶ 34:07](https://youtu.be/U8zISIlBq90?t=2047)
8. Добавьте второй слой **Voronoi**, **11** точек, Trigger **Collision**: particle-particle выкл, Bullet выкл, **particle-polygon вкл**. [▶ 33:21](https://youtu.be/U8zISIlBq90?t=2001)
9. Cube ▸ **xpCollider** tag с **Bounce on Collision выкл** — фиксирует попадания, не расталкивая осколки. [▶ 32:36](https://youtu.be/U8zISIlBq90?t=1956)
10. Collider tag ▸ вкладка **Spawn**: включить, добавить spawning emitter (в систему). В точке столкновения, Direction **Source Particle** + spread, Speed **Relative**, Number **1**, spawn **один раз** на частицу. У spawning emitter Speed **0**. [▶ 37:18](https://youtu.be/U8zISIlBq90?t=2238)
11. **xpDrag**, Density **Water** (заодно успокаивает осколки). [▶ 38:12](https://youtu.be/U8zISIlBq90?t=2292)
12. Generate ▸ **xpMultiSpawn**; исключите его для эмиттеров shatter и dynamics (перетащите модификатор в их список исключений). [▶ 39:29](https://youtu.be/U8zISIlBq90?t=2369)
13. Spawning emitter ▸ Groups: Ctrl+Alt-клик по Create Group дважды; режим **Use First Group Only** (группа 1). Слой xpMultiSpawn → **группа 2**, Count **3**, на возрасте 0 в течение 1 кадра, Direction relative с большим spread, Speed **inherit source**. Группа 2 — display **Dots**; вариация радиуса в обеих группах, чтобы drag их разводил. [▶ 41:09](https://youtu.be/U8zISIlBq90?t=2469)
14. Тёмный Sky, камера Physical с маленьким f-stop для малой глубины резкости (DOF). Cache на 200 F, по словам ведущих, около 3–4 мин. [▶ 42:32](https://youtu.be/U8zISIlBq90?t=2552)

## Подводные камни
- Слой Voronoi с Trigger **Always** раскалывает сразу — сначала задайте Time/Collision.
- Осколки проходят друг сквозь друга = мало динамических частиц; увеличьте Distribution.
- xpShatter нормально кэшируется через xpCache.

## Как сейчас (новые инструменты)
**nxShatter** (NeXus 2026.1 beta, GPU): Voronoi/Glass/Wood/Bricks с sub-fracture и триггерами; многоуровневые обломки через **nxSpawn** (On Collision, 8 sub-layers). GPU-твёрдые тела пока только анонсированы, поэтому в стабильном Fused 2025.4 оставляйте xpShatter с xpDynamics/Bullet, как в видео.
