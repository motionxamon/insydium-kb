# Рост с разной скоростью, уменьшение с возрастом, затем смерть (nxScale Clamp within Range + Age map на Upper Radius Limit + kill через nxQuestion)

- Источник: Top Tip Tuesday — nxScale Random Growth — https://www.youtube.com/watch?v=luYB_A_yV1I (2023-10-24)
- Хост / поколение: C4D; G2 NeXus внутри X-Particles (nxScale, nxQuestion, nxTurbulence) + ветер
- Задача: частицы рождаются с размером 0, растут с разной скоростью до разного максимального размера, затем уменьшаются и удаляются.

## Исходная сцена
**xpEmitter** с радиусом **0 cm**; ветер + **nxTurbulence** для движения. Дефолтный **nxScale**: **Change Value Over Time – Absolute** (+2 cm/кадр), **Clamp to Radius Limit** с **Upper 20 cm**.

## Шаги
1. Если ставить keyframe на верхний предел, уменьшатся все частицы сразу — используйте mapping. [▶ 1:37](https://youtu.be/luYB_A_yV1I?t=97)
2. nxScale ▸ Mapping ▸ map **Age**, параметр **Upper Radius Limit**, диапазон **100 → 150** кадров; кривая на максимуме до 100 и спадает до 0 к 150. [▶ 2:08](https://youtu.be/luYB_A_yV1I?t=128)
3. Вкладка Object: увеличьте изменение радиуса и добавьте **variation** → разная скорость роста. [▶ 3:29](https://youtu.be/luYB_A_yV1I?t=209)
4. Режим Clamp **Clamp within Range** → каждая частица получает случайный максимум между двумя пределами. [▶ 3:58](https://youtu.be/luYB_A_yV1I?t=238)
5. **nxQuestion**: Age **> 5** кадров **AND** Radius **= 0** → Action **Kill** (проверка возраста не даёт убить новорождённых с радиусом 0). [▶ 5:44](https://youtu.be/luYB_A_yV1I?t=344)
6. Display Spheres для финального вида.

## Как сейчас (новые инструменты)
В Fused 2025.4 **nxScale** стал слоистым; см. рецепт 2026-04-28 (nxScale range spawn fade). В 2026.1 beta логику lifespan можно также держать в nxQuestion Kill/Set Life.
