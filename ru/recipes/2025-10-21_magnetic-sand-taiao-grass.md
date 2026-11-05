# Фейковый магнитный песок / шипы феррожидкости (Taiao toGrass + приклеенные частицы)

- Источник: Top Tip Tuesday — Magnetic Sand — https://www.youtube.com/watch?v=TWZrrfN1URk (2025-10-21)
- Хост / поколение: C4D, Taiao toGrass + эмиттер X-Particles (CPU) + xpVertexMap
- Задача: шипы из железных опилок, которые встают, покачиваются и ложатся, пока движется невидимый магнит.

## Шаги
1. Plane + текстурный слой **xpVertexMap** (Maxon noise shader), маскированный **Sphere field** (круглое пятно). [▶ 0:33](https://youtu.be/TWZrrfN1URk?t=33)
2. **toGrass**: Generate on = plane, **Selection Map = vertex map** (вес управляет ещё и плотностью/длиной). Тип слоя травы — **Polygon** травинки (не сплайны), длина ~65 с вариацией, **Segments 1** (жёсткие травинки, которые только поворачиваются, без изгиба). [▶ 1:14](https://youtu.be/TWZrrfN1URk?t=74)
3. toGrass **Forces**: wind + turbulence; задайте **Direction Object** = куб (его +Z = направление ветра) с **тегом Vibrate** на вращении → движение магнита. Меньше октав = плавнее турбулентность; ниже сила/частота ветра, крупнее масштаб турбулентности → ровные спокойные зоны между «ударами» магнита. [▶ 4:06](https://youtu.be/TWZrrfN1URk?t=246)
4. Вырастание: ключи на **Blade Height** 2 cm (кадр 0) → полная (кадр 27). [▶ 5:24](https://youtu.be/TWZrrfN1URk?t=324)
5. Скройте траву; **xpEmitter** Object = toGrass, Polygon Area, **Stick Particle to Source Object**, **Shot 200 000**, скорость 0. [▶ 5:58](https://youtu.be/TWZrrfN1URk?t=358)
6. Цвет по движению: у приклеенных частиц скорость 0 → включите **Extended Data ▸ World Speed**, Display Gradient (Parameter) **Speed (World)** чёрный→белый, максимум ~200. [▶ 7:13](https://youtu.be/TWZrrfN1URk?t=433)
7. Слой земли: продублируйте эмиттер на плоскость с той же vertex map в Selection (в noise серый вместо чёрного, чтобы не было дырок). [▶ 9:10](https://youtu.be/TWZrrfN1URk?t=550)
