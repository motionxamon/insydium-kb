# Точки MoGraph Matrix как движущиеся цели притяжения (nxAttract в режиме Object + nxPush + age map в nxScale)

- Источник: Top Tip Tuesday — Matrix Particle Attract — https://www.youtube.com/watch?v=nJpItCX8GlY (2024-07-30)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxPush, nxScale, nxAttract, nxTurbulence) + C4D MoGraph Matrix
- Задача: частицы с контура текста пульсируют и роятся вокруг ближайшей из нескольких точек Matrix, которые скользят по внутреннему сплайну.

## Исходная сцена
xpEmitter в режиме Object, текстовый сплайн, **Edges**; Rate, lifespan 150, **2000/s**, speed 0. Внутри буквы — замкнутый сплайн с **Uniform** intermediate points 100.

## Шаги
1. **nxPush** в режиме **Particle Radius**, больше итераций. [▶ 1:09](https://youtu.be/nJpItCX8GlY?t=69)
2. **nxScale** (под nxPush — порядок важен): **Set Value** radius 3, **Mapping ▸ Age** 0→80 F на радиус; кривая быстро растёт от 0 до максимума, затем уменьшается к 80 F. [▶ 1:41](https://youtu.be/nJpItCX8GlY?t=101)
3. Ставим радиус эмиттера в **0**, чтобы размером целиком управлял nxScale (иначе частицы появляются сразу с 3 cm). [▶ 1:52](https://youtu.be/nJpItCX8GlY?t=112)
4. **MoGraph Matrix** в режиме **Object** на внутреннем сплайне; анимируем его **Rate** (например, 2%), чтобы точки ехали по сплайну. [▶ 3:42](https://youtu.be/nJpItCX8GlY?t=222)
5. **nxAttract** под nxScale, режим **Object**, кидаем туда Matrix → каждая точка Matrix становится отдельной целью; каждая частица летит к **ближайшей** точке. Отображение цели выключаем. [▶ 4:28](https://youtu.be/nJpItCX8GlY?t=268)
6. Усмиряем: **Acceleration 100**, **Speed Limit 25**. [▶ 4:43](https://youtu.be/nJpItCX8GlY?t=283)
7. Matrix **Count ~7** = медленные волнообразные/пульсирующие переходы между точками; большие значения = чёткие шипы. Прячем Matrix и сплайн. [▶ 5:36](https://youtu.be/nJpItCX8GlY?t=336)
8. **nxTurbulence** в самом низу, Voronoi, масштаб поменьше, умеренная сила — для дрейфа. [▶ 5:54](https://youtu.be/nJpItCX8GlY?t=354)

## Подводные камни
- Matrix можно также посадить на вершины/поверхности и анимировать Effectors — всё это тоже двигает цели.
