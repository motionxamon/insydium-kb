# Эмиссия только с самых быстро движущихся частей меша (слой Vertex Speed в xpVertexMap + эмиссия по текстуре)

- Источник: Top Tip Tuesday — Vertex Speed Emission — https://www.youtube.com/watch?v=iWET6SJpDhw (2023-03-28)
- Хост / поколение: C4D; CPU X-Particles (xpEmitter, xpVertexMap, xpTurbulence)
- Задача: лёгкие дымные частицы, срывающиеся с вибрирующей капсулы, только когда она быстро движется.

## Исходная сцена
Примитив Capsule с тегом C4D **Vibrate** (позиция + вращение). xpEmitter в режиме Object на капсуле, скорость 0, **lifespan 30**.

## Шаги
1. INSYDIUM ▸ X-Particles ▸ Utilities ▸ **xpVertexMap**; добавьте капсулу в его список Objects — работает с примитивами и генераторами (например, клонами MoGraph), а не только с полигональными объектами. [▶ 0:07](https://youtu.be/iWET6SJpDhw?t=7)
2. Удалите слой Polygon по умолчанию; добавьте слой **Vertex Speed**. Опции: weight 0 при мировой скорости 0, полный вес при **300 cm/s** по умолчанию — для быстрого объекта поднимите максимум сильно выше, а **Min Speed** поднимите, чтобы статичные части оставались в нуле. [▶ 2:19](https://youtu.be/iWET6SJpDhw?t=139)
3. Emitter ▸ вкладка Object: поставьте сгенерированную vertex map в **Selection**; поднимите **Threshold**, чтобы излучали только быстрые вершины (отпустите, если слишком редко). [▶ 3:02](https://youtu.be/iWET6SJpDhw?t=182)
4. Emission ▸ **Motion Inheritance** вкл, ~**60%**. [▶ 3:35](https://youtu.be/iWET6SJpDhw?t=215)
5. **xpTurbulence** (Modifiers ▸ Motion): noise **FBM**, масштаб крупнее, Strength **~24** → лёгкий дымок. [▶ 4:02](https://youtu.be/iWET6SJpDhw?t=242)
6. Текстура: материал C4D с noise **Luka** в Color (scale **600%**) на капсуле. Emitter ▸ Emit from **Texture**, привяжите этот тег текстуры: эмиссия идёт по светлым участкам канала Color, и частицы берут из него цвет. [▶ 4:44](https://youtu.be/iWET6SJpDhw?t=284)

## Как сейчас (новые инструменты)
G2/G3: эмиссия nxEmitter с nxFalloff (falloff по Attribute / vertex map, 2026.1 beta) и motion inheritance; nxTurbulence (Curl Add/Blend ≈ наследование).
