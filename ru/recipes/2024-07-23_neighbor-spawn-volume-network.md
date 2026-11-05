# Самопорождающиеся сети частиц внутри объёма (поиск соседей в nxQuestion + Spawn, удаление по объёму)

- Источник: Top Tip Tuesday — Particle Neighbor Spawn — https://www.youtube.com/watch?v=nC1YyRrwY2g (2024-07-23)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxQuestion, nxSpeed, nxScale, nxColor, nxPush, nxTurbulence)
- Задача: дюжина частиц-«семян» внутри текста порождает ветвящиеся сети, которые заполняют буквы движением, похожим на жидкость.

## Исходная сцена
Примитив Text внутри **xpJoin**, тег xpCollider настроен удерживать частицы внутри, friction 35%. xpEmitter: Object = join, **Volume**, Shot **12** частиц, speed 0.

## Шаги
1. **nxQuestion** Q1: **If Particle Neighbors** в пределах **4 cm** **меньше 9** → **Action Spawn**, distance **0.2**, **новый spawn-эмиттер**, Inherit parent off, speed 25, radius 1. [▶ 1:33](https://youtu.be/nC1YyRrwY2g?t=93)
2. **nxSpeed** Incremental **−50** с вариацией → порождённые частицы замедляются до остановки. [▶ 2:06](https://youtu.be/nC1YyRrwY2g?t=126)
3. Q2 (новый вопрос ниже, поиск по всем частицам): соседей в несколько большем радиусе **меньше ~270** → Spawn, distance 0.2, свой новый spawn-эмиттер (speed 25, другой цвет). Подстраивай оба порога, чтобы менять форму сети. [▶ 2:38](https://youtu.be/nC1YyRrwY2g?t=158)
4. Оба радиуса spawn поставь в **0**; отображение — залитые круги по радиусу. **nxScale** change-over-time (медленно), вариация 5%, **Clamp to radius limit** + **within range**, max **1 cm**. [▶ 4:12](https://youtu.be/nC1YyRrwY2g?t=252)
5. Удаление сбежавших: Q3 **Document ▸ Object Distance**, измерение **Volume** у объекта текста; **> 0 = снаружи** (< 0 внутри) → **Kill**. [▶ 4:49](https://youtu.be/nC1YyRrwY2g?t=289)
6. **nxColor** gradient by parameter (пресет purple/magenta), замапленный на **Age**. [▶ 5:48](https://youtu.be/nC1YyRrwY2g?t=348)
7. Движение: **nxPush** Particle Radius, **nxTurbulence** Voronoi strength 10 → движение меняет число соседей, а это меняет порождение. Перекрась по **Speed** для другого вида. [▶ 7:02](https://youtu.be/nC1YyRrwY2g?t=422)

## Как сейчас (новые инструменты)
**nxSpawn** в NeXus 2026.1 (Rate/Burst/Pulse, подслои) заменяет action Spawn в nxQuestion; удержание внутри объёма — через nxFalloff с 16 режимами (режим Object) на слое kill.
