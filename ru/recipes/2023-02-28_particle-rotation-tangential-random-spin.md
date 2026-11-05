# Основы вращения частиц (Use Rotation на эмиттере: Set / Tangential / None + случайное вращение xpSpin)

- Источник: Top Tip Tuesday — Particle Rotation — https://www.youtube.com/watch?v=jdlkfgR8Zy8 (2023-02-28)
- Хост / поколение: C4D; CPU X-Particles (xpEmitter, xpTurbulence, xpSpin)
- Задача: стрелки, которые смотрят по направлению движения, или кубики, которые хаотично кувыркаются, как парящая пыль.

## Исходная сцена
**xpTurbulence** по умолчанию закручивает частицы с отображением **Arrow** — все они смотрят по +Z, как бы ни двигались.

## Шаги
1. Эмиттер ▸ Extended Data ▸ General ▸ **Use Rotation** (по умолчанию выключено ради экономии вычислений). [▶ 1:06](https://youtu.be/jdlkfgR8Zy8?t=66)
2. Режим **Set**: фиксированные Heading/Pitch/Bank (например, Pitch 90 → все смотрят вверх). Верните 0. [▶ 1:30](https://youtu.be/jdlkfgR8Zy8?t=90)
3. Режим **Tangential** → каждая частица постоянно выравнивается по направлению движения. [▶ 2:02](https://youtu.be/jdlkfgR8Zy8?t=122)
4. Случайное кувыркание: отображение **Box Filled**; Modifiers ▸ Motion ▸ **xpSpin** (операция Spin, за кадр, например 3° по каждой оси). [▶ 2:57](https://youtu.be/jdlkfgR8Zy8?t=177)
5. xpSpin ничего не делает, пока у эмиттера нет данных вращения: Use Rotation включить, режим **None** (вращением управляет не эмиттер, а модификатор). [▶ 4:08](https://youtu.be/jdlkfgR8Zy8?t=248)
6. Органичное разнообразие: величину spin верните в 0, включите **Random Spin ~2°** по каждой оси → каждая частица вращается со своей скоростью. [▶ 4:43](https://youtu.be/jdlkfgR8Zy8?t=283)

## Подводные камни
Любому эффекту вращения (spin, align, tangential) нужен включённый Use Rotation на эмиттере.

## Как сейчас (новые инструменты)
GPU: **nxSpin** / **nxRotate** (слоёный nxSpin с Fused 2025.4).
