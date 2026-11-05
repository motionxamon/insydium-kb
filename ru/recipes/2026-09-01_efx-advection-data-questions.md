# Частицы-языки пламени по данным адвекции nxExplosiaFX (kill и цвет по температуре)

- Источник: Top Tip Tuesday — Advection Data — https://www.youtube.com/watch?v=1ERTCdQAoF0 (2026-09-01)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX GPU, nxQuestion)
- Задача: рендерить только частицы, которые несёт симуляция дыма/огня, — с цветом и гибелью по температуре, которую они берут из сетки.

## Дерево сцены
```
nxExplosiaFX (source: Torus)  — Dynamics ▸ Particle Advection: Emitters = xpEmitter, Mode Position
xpEmitter  (Object: same Torus, Polygon Area, Rate 50 000/s, speed 0, Full Lifespan)
  Display: Gradient (Parameter) = Temperature, Min 1000 / Max ~6100
nxQuestion
  If Age > 2 F  AND  Temperature < 1000  → Action: Kill
```

## Шаги
1. Эмитьте частицы с **того же объекта**, что и источник EFX, speed 0 (двигаются они только адвекцией).
2. nxExplosiaFX → **Dynamics ▸ Particle Advection** → перетащите туда эмиттер.
   - Режим **Velocity** (по умолчанию): скорость жидкости *прибавляется*; частицы, покинувшие сетку, продолжают лететь.
   - Режим **Position**: частицы точно следуют за жидкостью и останавливаются у стенок.
3. Адвекция также копирует на частицы значения вокселей **smoke, temperature, fuel**.
4. Рабочий диапазон температуры найдите через EFX Display: Flame Emit Above показывает порог пламени (здесь 1000), а если поднимать его, пока пламя не исчезнет, получите максимум (~6100).
5. Цвет: Display эмиттера → **Gradient (Parameter) → Temperature**, Min 1000 / Max 6100 (синий холодный → белый горячий).
6. Пусть частицы гаснут вместе с пламенем, а не по фиксированному lifespan: **nxQuestion** — Question *Age > 2 frames* (запас: у новорождённых частиц температура 0) **AND** дочерний Question *Temperature < 1000* → **Action Kill**.
7. Более быстрая диссипация в EFX (Simulation ▸ Dissipation ▸ Temperature) теперь автоматически укорачивает языки пламени из частиц.

## Примечания
- Дым рендерить вообще не обязательно — EFX здесь просто поле движения/данных.
- Та же идея работает со значениями Smoke и Fuel (например, рождать частицы сажи там, где дым плотный).
