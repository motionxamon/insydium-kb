# Процедурная ветвящаяся молния с искрами (mtSplineFX + xpSplineMesher + xpSpawn)

- Источник: Top Tip Tuesday — mtSplineFX Lightning — https://www.youtube.com/watch?v=sctuPLrOw60 (2024-01-16)
- Хост / поколение: C4D; MeshTools **mtSplineFX** + CPU X-Particles (xpSplineMesher, xpSprite, xpJoin, xpSpawn, xpGravity)
- Задача: электрические дуги от сферы к плоскости, с ответвлениями и падающими искрами.

## Исходная сцена
Emitter Start (синий, на сфере) и Emitter End (оранжевый, на маленькой плоскости), оба в режиме **Pulse**, частицы прилипают к своим объектам-источникам.

## Шаги
1. **mtSplineFX**: Start = стартовый эмиттер, End = конечный эмиттер, тип соединения **to points** → каждая стартовая частица соединяется с ближайшей конечной. [▶ 0:46](https://youtu.be/sctuPLrOw60?t=46)
2. **xpSplineMesher**: Joins выкл., Vertex Colors выкл., spline = mtSplineFX, размер ~1 см, scaling spline сужается в точку на конце; эмиссионный материал. [▶ 1:15](https://youtu.be/sctuPLrOw60?t=75)
3. mtSplineFX ▸ Motion ▸ **Large noise**: amplitude 150, scale 500, animation speed 350 → бешеная молния. [▶ 2:06](https://youtu.be/sctuPLrOw60?t=126)
4. Connections ▸ добавьте слой **Fork** (по умолчанию 2 ответвления на сплайн). Отредактируйте **distribution curve**, чтобы она была в нуле у основания и на конце — тогда ответвления растут из середины сплайна. [▶ 2:32](https://youtu.be/sctuPLrOw60?t=152)
5. Ответвления могут целиться только в геометрию: **xpSprite** (Cube) на конечном эмиттере внутри **xpJoin**; слой Fork ▸ connect to **Custom Object** = этот join. Скройте join и частицы. [▶ 4:24](https://youtu.be/sctuPLrOw60?t=264)
6. Ctrl-перетаскиванием скопируйте слой Fork **дочерним** к первому → ответвления второго уровня. [▶ 4:42](https://youtu.be/sctuPLrOw60?t=282)
7. Искры: **xpSpawn**, исключите его на вкладке Modifiers стартового эмиттера; новый spawn-эмиттер: lifespan 10 (var 5), speed 200 (var 150), отображение **Lines**, тонкие, оранжевые; spawn 60 (var 20) за кадр, направление по умолчанию сферическое. [▶ 5:56](https://youtu.be/sctuPLrOw60?t=356)
8. **xpGravity** с уменьшенной силой; Draw Emitter выкл. Двигайте сферу, чтобы управлять разрядами. [▶ 6:45](https://youtu.be/sctuPLrOw60?t=405)

## Как сейчас (новые инструменты)
**nxSpawn** (2026.1 beta) для дочерних частиц-искр; mtSplineFX по-прежнему основной инструмент для молний.
