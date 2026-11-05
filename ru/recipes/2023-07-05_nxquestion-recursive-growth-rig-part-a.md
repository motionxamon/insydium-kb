# Рекурсивный рост по полю через спавн в nxQuestion (nxQuestion Neighbors + Spawn, nxPush, nxTurbulence с mapping)

- Источник: INSYDIUM LIVE! — July 2023 – NeXus, Taiao, TerraformFX & MeshTools — https://www.youtube.com/watch?v=6WjDq_87uck (2023-07-05)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (Fused 2023.3: переработанный **nxQuestion**, новая вкладка Mapping) — всё на GPU
- Задача: рост наподобие коралла, который прорастает с края блока частиц там, где его касается поле, закручивается по векторному полю и замирает после заданной дистанции.

## Исходная сцена
xpEmitter, заполняющий бокс/сетку статичными **чёрными** частицами (цвет только для отображения; логика вопросов читает цвет).

## Шаги
1. **nxQuestion** ▸ Question 1: Particle Data ▸ **Field** + маленькое **Spherical field**, поставленное на блок. [▶ 13:47](https://youtu.be/6WjDq_87uck?t=827)
2. Дочерний вопрос (оператор **And**): Particle ▸ **Neighbors** — меньше **45** в пределах **10 cm** (40 даёт один ряд по краю, 45 — два ряда) → Action **Set Color white**, value 100%. Итог: белеют только краевые частицы внутри поля. [▶ 15:01](https://youtu.be/6WjDq_87uck?t=901)
3. Через Ctrl добавить соседний вопрос ниже (стек выполняется сверху вниз): Color ▸ **Brightness ≥ 1** → Action **Spawn** в новый spawn-эмиттер; **Inherit Parent off**; Speed **0**, Radius **2**, Distance **1**. [▶ 15:44](https://youtu.be/6WjDq_87uck?t=944)
4. **nxPush**: режим Particle Radius, Strength **100** → заспавненные бусины расталкиваются, и рост идёт рекурсивно. [▶ 17:17](https://youtu.be/6WjDq_87uck?t=1037)
5. Отображение spawn-эмиттера: Circles filled, градиент по Age, пресет **Heat**, первый узел белый — новорождённые белые, поэтому шаг 3 снова срабатывает на них (петля рекурсии). [▶ 17:36](https://youtu.be/6WjDq_87uck?t=1056)
6. Трюк с порядком: nxPush **над** вопросом = пухлый, «блобовый» рост; **под** ним = тоньше, ветвление как у щупалец. [▶ 18:22](https://youtu.be/6WjDq_87uck?t=1102)
7. **nxTurbulence** Curl, Strength **1**, Scale **250**, Frequency **0** (статичное поле, в которое растём). Вкладка Mapping ▸ **Color Brightness → Strength**: чёрные частицы блока силу не получают, белый рост получает полную. [▶ 19:45](https://youtu.be/6WjDq_87uck?t=1185)
8. Заморозка старого роста: ещё один вопрос внизу, **Distance Traveled within 50–150** → **Set Speed 0** (с небольшим демпфированием). Рекурсия продолжается от белых кончиков. [▶ 20:15](https://youtu.be/6WjDq_87uck?t=1215)
9. Двигайте/анимируйте поле, чтобы запускать рост в других местах — на GPU всё интерактивно (демо на RTX 3080 Ti / 2080). [▶ 21:04](https://youtu.be/6WjDq_87uck?t=1264)

## Как сейчас (новые инструменты)
2026.1 beta: **nxBioLogic** (differential growth, coral, Physarum) — специальный солвер роста; **nxSpawn** (On Age/Instant, 8 под-слоёв) заменяет action Spawn в nxQuestion; nxDendrite — для ветвящихся сетей. Подход через nxQuestion по-прежнему работает в Fused 2025.4 и 2026.1 beta.
