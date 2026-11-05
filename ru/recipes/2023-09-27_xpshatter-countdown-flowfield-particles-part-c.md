# «Живой» shatter-обратный отсчёт (xpShatter spline points + particle points, xpFlowField Along Spline, nxPush)

- Источник: INSYDIUM LIVE! — September 2023 – NeXus, Taiao & X-Particles — https://www.youtube.com/watch?v=uS_zr-Jf178 (2023-09-27)
- Хост / поколение: C4D; CPU xpShatter + xpFlowField + **G2** nxPush на том же эмиттере
- Задача: плоскость, расколотая вокруг анимированного текстового сплайна 5-4-3-2-1, где дрейфующие частицы добавляют лишние ячейки и осколки «текут».

## Исходная сцена
C4D **Text spline** с ключами, меняющими цифру каждую секунду; **plane** для раскола; вторая, **оранжевая plane** прямо под ней; свет с тенями.

## Шаги
1. Generators ▸ **xpShatter**, plane дочерним объектом. Display: выключить Draw Cut Edges, временно включить **Draw Shatter Points** (одна точка на осколок). [▶ 1:02:10](https://youtu.be/uS_zr-Jf178?t=3730)
2. Вкладка Object: удалить дефолтный **Point Generator** под слоем **Voronoi**; вместо него положить под Voronoi текстовый сплайн. [▶ 1:02:36](https://youtu.be/uS_zr-Jf178?t=3756)
3. Вершины сплайна дают ровные, неправильные на вид ячейки (Uniform 20 intermediate points) → переключить на **генерацию точек вдоль сплайна**, количество **500**, затем **offset** их от сплайна → осколки расходятся веером вокруг цифр; всё остаётся процедурным при смене цифры. [▶ 1:03:51](https://youtu.be/uS_zr-Jf178?t=3831)
4. Voronoi layer **Offset 3 cm** → щели; включить оранжевую plane снизу и дать осколкам тёмный материал → стилизованные светящиеся щели с тенями. [▶ 1:04:39](https://youtu.be/uS_zr-Jf178?t=3879)
5. **xpEmitter** ▸ Object = текстовый сплайн, эмиссия с **Edges**; **Shot 200**, Speed 0, Radius **2** (variation 1); Display Sphere для проверки. [▶ 1:05:54](https://youtu.be/uS_zr-Jf178?t=3954)
6. Dynamics ▸ **xpFlowField**: подогнать bounds под текст; Display Arrow (voxels, чтобы видеть все); **Cell size 15**. [▶ 1:07:33](https://youtu.be/uS_zr-Jf178?t=4053)
7. Удалить дефолтный слой Random; добавить слой **Along Spline** = текстовый сплайн; убрать его falloff 50 cm (плоская кривая) и **Strength 100**. [▶ 1:08:28](https://youtu.be/uS_zr-Jf178?t=4108)
8. Ничего не движется — Flow Field в режиме **Direction** (задаёт направление, не скорость) → у эмиттера Speed **20** + вариация → частицы текут вдоль меняющихся цифр. [▶ 1:09:12](https://youtu.be/uS_zr-Jf178?t=4152)
9. **nxPush** (дистанция Particle Radius), чтобы частицы расталкивали друг друга; Display Squares + Display Size Factor. [▶ 1:09:55](https://youtu.be/uS_zr-Jf178?t=4195)
10. Снова включить shatter + plane; на кадре, где уже есть частицы, положить **эмиттер тоже под слой Voronoi** (use object points) → количество и форма осколков теперь текут вместе с частицами. [▶ 1:11:07](https://youtu.be/uS_zr-Jf178?t=4267)
11. Рендер с скрытыми частицами (только текучие осколки), с частицами одного размера (цифровой вид) или с полным радиусом. [▶ 1:12:03](https://youtu.be/uS_zr-Jf178?t=4323)

## Подводные камни
- Извлечение линий разреза в сплайн (MeshTools edge spline с shatter внутри) на тот момент видело все внутренние рёбра полигонов, а не N-gon-контуры осколков.

## Как сейчас (новые инструменты)
2026.1 beta: **nxShatter** (GPU Voronoi/Glass/Wood/Bricks, может управляться эмиттером) и **nxFlowField** / **nxWarp Path** для потока вдоль сплайна, вместе с nxPush. В Fused 2025.4.1 заявлено, что **mtEdgeSpline handles n-gons**, — это должно решить проблему с извлечением разрезов.
