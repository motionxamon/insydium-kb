# Психоделические плоские паттерны расталкивания (nxPush + фиксация скорости через nxQuestion + nxScale по полю)

- Источник: Top Tip Tuesday — NeXus Push Particles — https://www.youtube.com/watch?v=IuaZtmg5O8o (2024-04-09)
- Хост / поколение: C4D; NeXus GPU (nxPush, nxQuestion, nxScale, nxTurbulence) на xpEmitter; C4D Random field
- Задача: частицы на плоскости расталкивают друг друга в 2D, пока их радиусы анимируются шумом.

## Исходная сцена
Эмиттер-плоскость (Object, polygon area), Rate 20, радиус 6, скорость 0. Display Circles, Gradient Parameter с маппингом на **Radius**.

## Шаги
1. **nxPush**: режим Distance **Particle Radius**, Strength 100%.
2. Фиксация на плоскости: **nxQuestion** с прямым **Action ▸ Set Velocity**, X/Y/Z = 0 (вопрос не нужен). Работает на любой плоскости, выровненной с шагом 90°.
3. **nxScale**: операция **Set by Falloff**, clamping выкл.; Fields ▸ **Random field** — жёлтый = радиус 0, красный = максимальный радиус эмиттера (6).
4. Random field: noise **Gaseous**, scale 500, добавьте скорость анимации (потом поднимите ещё). Remapping ▸ Contour **Curve** — кривая контраста. Скройте отображение поля.
5. Display **Squares** на 100%, чтобы все частицы рисовались одним размером независимо от радиуса (читается лучше).
6. Rate 100 → 200, display Dots.
7. **nxTurbulence** **ниже** nxQuestion: обнулите компонент **Y**, чтобы фиксация держалась; тип Curl, больше strength/scale, ниже frequency, уменьшите Blend.

## Подводные камни
- Любая дополнительная сила с компонентом Y ломает 2D-фиксацию, если её не обнулить.
- Если выключить турбулентность, получится другой вид расталкивания — «рост наружу».

## Как сейчас (новые инструменты)
В NeXus 2026 те же модификаторы; nxFalloff (16 режимов, включая Noise) может заменить C4D field в nxScale.
