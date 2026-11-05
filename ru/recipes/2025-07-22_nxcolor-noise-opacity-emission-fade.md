# Прячем жёсткое кольцо эмиссии шумной маской прозрачности (слои nxColor + сплайн birth rate)

- Источник: Top Tip Tuesday — Noisy Particle Emission — https://www.youtube.com/watch?v=PyCCkH-nxfw (2025-07-22)
- Хост / поколение: NeXus (слои nxColor, шум nxTurbulence типа Boron/Curl) + аддитивные частицы в Redshift
- Задача: органичные завихрения, в которых круглый край эмиттера больше не читается как форма.

## Исходная сцена
Эмиттер Circle, Ring Only, cone 90°, rate 2000/F (50 000 в продакшене), life 90, speed 100, radius 3; **nxTurbulence** в режиме шума Boron; аддитивный материал частиц Redshift (цвет → opacity).

## Шаги
1. Слой 1 **nxColor** — *Gradient by Parameter* чёрный→белый, управляется **Random field** (Luka noise, scale ~800, animation speed ~40) → анимированный ч/б шум. [▶ 1:52](https://youtu.be/PyCCkH-nxfw?t=112)
2. Слой 2 (выше) — тот же градиент, привязанный к **Age** (чёрный при рождении, быстро белеет), blend **Multiply** → частицы рождаются невидимыми, затем шум их проявляет. [▶ 3:22](https://youtu.be/PyCCkH-nxfw?t=202)
3. Слой 3 (сверху) — копия слоя по возрасту, blend **Add** → старые частицы полностью белые; двигаем узлы градиента, чтобы пропустить больше шума. [▶ 4:15](https://youtu.be/PyCCkH-nxfw?t=255)
4. Цвет управляет opacity в Redshift → шумное, рваное проявление у эмиттера. [▶ 8:03](https://youtu.be/PyCCkH-nxfw?t=483)
5. Эмиттер ▸ Emission ▸ **Birth Rate spline**: рампа от 0 до максимума в начале (без выброса "лепестками цветка"). [▶ 5:39](https://youtu.be/PyCCkH-nxfw?t=339)
6. Вариация lifespan ~25 кадров → частицы не умирают все разом. [▶ 6:34](https://youtu.be/PyCCkH-nxfw?t=394)

## Как сейчас (новые инструменты)
2026.1 beta: слоёные модификаторы nxColor + 16 режимов falloff дают то же самое без полей; falloff эмиссии на nxEmitter.
