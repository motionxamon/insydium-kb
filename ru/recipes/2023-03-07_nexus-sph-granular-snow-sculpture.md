# Снежная скульптура, которая рассыпается (гексагональная упаковка в режиме Shot + nxFluids SPH Granular: friction, substeps, stability, cohesion)

- Источник: Top Tip Tuesday — Granular Drop — https://www.youtube.com/watch?v=1oRzCeDQjWs (2023-03-07)
- Хост / поколение: C4D; G2 NeXus — xpEmitter + **nxFluids SPH Granular** + nxGravity; теги xpCollider на плоскости и кубе
- Задача: голова волка, плотно набитая гранулами, падает и разбивается на комья (снег, песок, сахар, соль).

## Шаги
1. System ▸ Emitters ▸ новый эмиттер: форма **Object**, укажите меш волка.
2. Emission: Subframe Emit выкл.; режим **Shot**, Shot Type **Hexagonal** (сетка), speed **0**. Сделайте шаг на один кадр, скройте меш. Меньше radius = больше частиц в объёме.
3. **nxGravity** уже в сцене → частицы падают, но не держатся вместе.
4. NeXus ▸ Objects ▸ **nxFluids**: тип **SPH**, режим **Granular** (PBD гранулы не умеет).
5. Display: Gradient Parameter по значению **granular**, диапазон **Auto**.
6. Granular ▸ **Friction 100**.
7. Для настоящих комьев нужно точнее считать скорости: **Substeps 3 → 15**.
8. **Stability** = проверка скорости: гранулы, разлетающиеся быстрее этого значения, вырываются из friction. 60 → выживают крупные куски; 2 → всё разваливается; итог **25**.
9. **Cohesion** = дополнительное пружинное сцепление; обычно оставьте по умолчанию — уменьшите, если sim выглядит прыгучим/пружинистым.

## Как сейчас (новые инструменты)
Песок/снег на **nxMPM** (пресеты nxMaterial *Snow packed/sticky*, *Sand wet*) в бете 2026.1; в стабильном Fused — nxFluids SPH Granular, как здесь.
