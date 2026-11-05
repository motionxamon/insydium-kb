# Кристалл, который осыпается по осколку (xpShatter + emitter, xpQuestion Inside Volume, mapped xpSpeed/xpRotator/xpSpin, xpFreeze)

- Источник: NAB 2023 - INSYDIUM Training — Crystal Shatter - Part 1 — https://www.youtube.com/watch?v=75GHeuPO3rU (2023-04-13)
- Хост / поколение: C4D; CPU X-Particles (xpShatter, xpExplode, xpSpeed, xpRotator, xpSpin, xpFreeze, xpQuestion) + MeshTools Inset; только viewport
- Задача: маленький гранёный кристалл (~14 см) разрушается постепенно — осколки вылетают, кружат по орбите и кувыркаются, а одна область остаётся целой. Во второй части добавляются частицы с адвекцией: см. 2023-04-14_crystal-shatter-explosiafx-advection-particles-part-b.

## Исходная сцена: модель кристалла
1. C4D **Platonic**, Type **Octa**, уменьшите; сделайте редактируемым (C) и вытяните по Y, чтобы он стал продолговатым.
2. INSYDIUM ▸ MeshTools ▸ **Inset** (Platonic — дочерний): **Amount 100%** сводит каждую грань в точку, **Offset** выдвигает эти точки наружу. Положите это во второй **Inset** только с небольшим Offset.
3. Верхний Inset ▸ Advanced ▸ **Optimize** (убирает дубли точек и битые полигоны) перед разрушением.

## Шаги
1. xpSystem; удалите эмиттер по умолчанию. Generators ▸ **xpShatter**; Inset — дочерний. Слой Voronoi + Point Generator (по умолчанию 40 точек; Display ▸ Draw Shatter Points показывает их). [▶ 2:38](https://youtu.be/75GHeuPO3rU?t=158)
2. Point Generator: Points **100 → 300**, Distribution **Normal (Gaussian)** со **Standard Deviation** — получается смесь крупных и мелких осколков; если выключить **Object Volume** (вместо объёма — bounding box) и поднять отклонение, разлом выйдет менее равномерным. [▶ 3:33](https://youtu.be/75GHeuPO3rU?t=213)
3. Рваные внутренние грани: слой Voronoi ▸ **Details** вкл. Значения по умолчанию рассчитаны на объекты ~200 см, так что всё уменьшаем: **Edge Length 2 → 0.5**, Noise **Electric**, **Global Scale ~1%**, **Strength ~0.1** (держите scale и strength примерно в соотношении 10 к 1). [▶ 6:34](https://youtu.be/75GHeuPO3rU?t=394)
4. xpShatter General ▸ **Add Emitter** → эмиттер в режиме control-only, по одной частице на осколок; **Auto Particle Radius** подгоняет размер под осколок. Выключите Draw Emitter и Show Particles. [▶ 8:25](https://youtu.be/75GHeuPO3rU?t=505)
5. **xpExplode** (Motion): разбрасывает частицы от центра масс; strength снизьте до **~5 см** под этот масштаб. [▶ 11:45](https://youtu.be/75GHeuPO3rU?t=705)
6. Триггер: скопируйте с Ctrl исходный Platonic, отмасштабируйте его (режим Object), чтобы он едва охватывал кристалл, поставьте ключ Scale на F0 и гораздо меньший масштаб ближе к концу (таймлайн 300 F; сдвиньте последний ключ раньше — разлом пойдёт быстрее). Скройте его. [▶ 18:00](https://youtu.be/75GHeuPO3rU?t=1080)
7. Emitter ▸ Questions ▸ **Particle Position ▸ Inside Volume**, режим **outside**, Object = анимированный Platonic, действие **activate modifiers** → xpExplode. Если часть осколков срывается сразу, увеличьте Platonic на F0. [▶ 22:43](https://youtu.be/75GHeuPO3rU?t=1363)
8. Случайность: **Sub-question ▸ Other ▸ Random Probability**; 100% = как раньше, низкое значение (~1%) отпускает осколки по несколько штук. [▶ 17:08](https://youtu.be/75GHeuPO3rU?t=1028)
9. Project Settings (Ctrl+D) ▸ X-Particles ▸ **Subframe Steps 2** (мелкий масштаб + точный контроль скорости). [▶ 20:37](https://youtu.be/75GHeuPO3rU?t=1237)
10. **xpSpeed**: Operation **Absolute**, **25 см/с** (потом 35); добавьте его в список модификаторов того же question. Mapping ▸ Speed по **Distance Travelled**, диапазон **0–30 см**, кривая: резкий подъём, провал, затем снова разгон. [▶ 21:51](https://youtu.be/75GHeuPO3rU?t=1311)
11. **xpRotator** после xpSpeed, повёрнут на **90°** на нужную ось; Mode **Force** (Velocity перебивает другие модификаторы), **Attraction 0**, **Rotate Speed ~50°**; замапьте Rotate Speed на Distance Travelled с плавным входом (ease-in), чтобы вращение по орбите начиналось после вылета. Порядок: explode → speed → rotator. [▶ 27:07](https://youtu.be/75GHeuPO3rU?t=1627)
12. **xpSpin**: нужно включить Emitter ▸ Extended Data ▸ General ▸ **Rotation**, **Tangential**, **Persist Orientation выкл.** Spin: affect Rotation, Absolute, Time-oriented выкл., **1000°** по каждой оси; замапьте на Distance Travelled (**0–100 см**) и опустите кривую, чтобы она никогда не доходила до полного значения. [▶ 30:44](https://youtu.be/75GHeuPO3rU?t=1844)
13. Часть оставить целой: **xpFreeze** (Control) + небольшое **Spherical field** над областью, которая не должна двигаться. [▶ 33:44](https://youtu.be/75GHeuPO3rU?t=2024)
14. Облегчённый меш для симуляции/кэша и вид битого стекла: Details **Edge Length 1 см**, **Strength 0.3**, **Smooth Normals выкл.** (жёсткие рёбра). [▶ 37:50](https://youtu.be/75GHeuPO3rU?t=2270)

## Подводные камни
- Всё в уменьшенном масштабе (объект 14 см): noise в Details, strength у xpExplode и скорости — всё должно быть намного меньше значений по умолчанию.
- Мелкий Edge Length в Details даёт красивый noise, но очень тяжёлые осколки; перед кэшем сделайте сетку грубее.

## Как сейчас (новые инструменты)
**nxShatter** (бета 2026.1: Voronoi/Glass, sub-fracture, триггеры, управление от эмиттера или MPM damage) заменяет xpShatter; логику отрыва — через **nxQuestion** (CPU questions ненадёжно управляют GPU-эмиттерами) и **nxFalloff** вместо масштабируемого Platonic; nxSpeed / nxRotate / nxSpin с NeXus Mapping. Стабильный C4D (Fused 2025.4): xpShatter, как в видео.
