# Пыльца с кончиков тычинок цветка Taiao (custom object в tiPlant, xpJoin, выделение слоя, nxWind)

- Источник: Top Tip Tuesday — Taiao Particles Emission — https://www.youtube.com/watch?v=ZgUIL-udXks (2024-05-28)
- Хост / поколение: C4D; Taiao (tiPlant, tiFlower) + xpEmitter + NeXus (nxWind, nxTurbulence)
- Задача: крошечные частицы пыльцы разлетаются только с утолщённых кончиков тычинок.

## Шаги
1. Слой trunk в **tiPlant** = стебель; перетаскиваем **tiFlower** в слот **Custom Object** у trunk, чтобы цветок сидел на стебле (модификатор Furling изгибает всё вместе). [▶ 1:09](https://youtu.be/ZgUIL-udXks?t=69)
2. **xpJoin** с растением и цветком в качестве дочерних; у xpEmitter Object = join, **Polygon Area**. [▶ 1:58](https://youtu.be/ZgUIL-udXks?t=118)
3. Эмиссия: lifespan 120 (var 70), birth rate 300, speed 0, **radius 0.1**. [▶ 2:21](https://youtu.be/ZgUIL-udXks?t=141)
4. tiFlower ▸ Flower Layers ▸ кнопка слоя **Stamen** создаёт **полигональное выделение** → кидаем его в поле выделения эмиттера. [▶ 2:48](https://youtu.be/ZgUIL-udXks?t=168)
5. Только кончики: дублируем слой тычинок (Ctrl-перетаскивание). На **излучающем** правим кривую **Profile**, чтобы осталась только головка (удаляем точку, одну опускаем в 0). На копии очищаем выделение и оставляем её как видимую полную тычинку. [▶ 3:41](https://youtu.be/ZgUIL-udXks?t=221)
6. **nxWind** направлен вдоль цветка, отображение вентилятора выключено, **strength 2** (частицы крошечные). [▶ 4:39](https://youtu.be/ZgUIL-udXks?t=279)
7. Отображение **Dots**, Gradient by Parameter (пресет Flame без красного/чёрного) по **Speed**, диапазон **Auto**. [▶ 5:12](https://youtu.be/ZgUIL-udXks?t=312)
8. **nxTurbulence** Voronoi, strength **0.1**, scale **4%**.
