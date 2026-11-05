# Отслаивание, управляемое заражением (nxInfectio Use Groups + nxWind/nxTurbulence на группе заражённых + разрыв nxConstraints Distance)

- Источник: Top Tip Tuesday — nxInfectio Peel — https://www.youtube.com/watch?v=Be90jYTwF0c (2023-12-12)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (xpEmitter + nxInfectio, nxWind, nxTurbulence, nxConstraints) + тег коллайдера
- Задача: органичное заражение расползается по модели; заражённые частицы сдувает, но они остаются связаны пружинами, тянутся и рвутся на куски.

## Исходная сцена
Модель с **тегом коллайдера**; **xpEmitter** Polygon Area, **Random Shot 40,000**, радиус **2 cm**, скорость 0. Display ▸ Color mode **Shader** с чёрно-белым noise (gaseous) — по белым частицам заражение идёт быстрее.

## Шаги
1. **nxInfectio** ▸ **Add Seed Object** (сферический объём) — поставьте его рядом с брюхом. Оранжевые = заражённые, синие = в инкубации. [▶ 1:34](https://youtu.be/Be90jYTwF0c?t=94)
2. Переключите color mode на **Use Groups**: добавьте **Incubating group** (группа 1) и **Infected group** (группа 2). [▶ 2:34](https://youtu.be/Be90jYTwF0c?t=154)
3. **nxWind**, повёрнутый наружу/вверх, Groups Affected **группа 2**. [▶ 3:34](https://youtu.be/Be90jYTwF0c?t=214)
4. **nxTurbulence**, Voronoi, strength **7**, Groups Affected **группа 2**. [▶ 3:56](https://youtu.be/Be90jYTwF0c?t=236)
5. **nxConstraints**: констрейнт **Distance** (не Birth), **6 связей** в пределах **40 cm**, stiffness пониже, Groups Affected **группа 2** → отслаивающиеся пласты. [▶ 4:38](https://youtu.be/Be90jYTwF0c?t=278)
6. Разрыв: рвётся при растяжении до **300%** от длины покоя → куски отрываются. [▶ 5:33](https://youtu.be/Be90jYTwF0c?t=333)
7. nxInfectio ▸ **Infected Lifespan 300 → 150** кадров, чтобы сдутые куски умирали. [▶ 5:47](https://youtu.be/Be90jYTwF0c?t=347)
8. Когда картинка устраивает, поставьте group color change на **No Color Changes** и снова покажите модель. [▶ 6:23](https://youtu.be/Be90jYTwF0c?t=383)

## Как сейчас (новые инструменты)
2026.1 beta: у каждого слоя модификатора свой список **Falloff** (включая Wet/Curvature) для дополнительного маскирования, а **nxDeformer** умеет рвать меш, управляемый частицами, если нужна оболочка, а не точки.
