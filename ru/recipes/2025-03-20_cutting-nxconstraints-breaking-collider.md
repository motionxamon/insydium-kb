# Разрезание мягкого тела коллайдером-ножом (nxConstraints Birth + Breaking Threshold)

- Источник: Bite-Sized — Cutting Constraints — https://www.youtube.com/watch?v=fzMhJobCGR0 (2025-03-20)
- Хост / поколение: C4D; xpEmitter + NeXus GPU nxConstraints, nxGravity; CPU-теги xpCollider
- Задача: упругая сфера из частиц, которую анимированный куб разрезает надвое.

## Исходная сцена
Пол-диск с **xpCollider**, friction **55%**; куб-«нож» с xpCollider (без настроек bounce/friction/scatter), анимирован: опускается, проходит поперёк и уходит вверх.

## Шаги
1. **xpEmitter ▸ Object**: Emitter Shape **Sphere**, поднят над полом. [▶ 0:32](https://youtu.be/fzMhJobCGR0?t=32)
2. Emission: **Shot**, режим **Simulate** (частицы видны на кадре 0), тип shot **Regular**, скорость **0**, radius **6**. Display **Spheres**, включите отображение **Constraints**. [▶ 0:49](https://youtu.be/fzMhJobCGR0?t=49)
3. **nxConstraints** ▸ связь **Birth** → через кадр появляются жёлтые пружины. [▶ 1:32](https://youtu.be/fzMhJobCGR0?t=92)
4. **nxGravity**, скорость снижена до **150**. [▶ 1:49](https://youtu.be/fzMhJobCGR0?t=109)
5. nxConstraints: **Iterations 10** (больше = жёстче) и слой **Collision** → упругое мягкое тело вместо шлепка. [▶ 2:20](https://youtu.be/fzMhJobCGR0?t=140)
6. Связь Birth ▸ **Breaking Threshold 50% → 20%** (разрыв, когда пружина растянута на эту долю исходной длины) → нож рвёт пружины и отталкивает одну половину. [▶ 2:42](https://youtu.be/fzMhJobCGR0?t=162)

## Как сейчас (новые инструменты)
**nxMPM** из NeXus 2026.1 (материал Elastic с разрушением, поддержка коллайдеров) — GPU-путь к разрезаемым мягким телам; nxPin может закрепить части constraint-тела.
