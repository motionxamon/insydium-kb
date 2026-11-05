# nxDrag — карточка инструмента

Встречается в **9** рецептах · 2023-04-16 → 2025-05-20 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- Опционально: **nxDrag** последним, Multiplier **~100,000**, чтобы всё успокоилось после взрыва. [▶ 6:07](https://youtu.be/PIgXQtSgnMY?t=367) — *[2025-05-20](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)*
- Сбросьте nxDrag на значения по умолчанию: маленькие частицы уже обгоняют большие — сопротивление зависит от радиуса. [▶ 1:28](https://youtu.be/Q5xA2nFPiIM?t=88) — *[2025-02-11](../../recipes/2025-02-11_nxdrag-realistic-air-resistance.md)*
- **nxDrag** под вопросом: плотность = морская вода, Strength **800%**, Mapping ▸ **Age** на 0–70 кадрах для множителя силы (сброс возраста из шага 8 даёт каждой зоне стартовать свободно). Итог: Strength 500%, отталкивание поднято до **50%**. [▶ 29:17](https://youtu.be/eJXaD9gVMsE?t=1757) — *[2024-10-04](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)*
- Замораживаем каплю: **nxDrag** **под nxGravity**, пресет Density — самый густой (**Mercury**): сопротивление полностью гасит гравитацию. [▶ 1:44](https://youtu.be/Tz60lfoe-hw?t=104) — *[2024-01-02](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)*
- nxDrag ▸ Groups Affected: только **группа 1**. [▶ 2:36](https://youtu.be/Tz60lfoe-hw?t=156) — *[2024-01-02](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)*
- **nxDrag** (base исключить): Density Water, Drag Coefficient **Fighter Aircraft**, strength multiplier 110 → потом **150** (Sphere в воде слишком сильно тормозит). [▶ 23:14](https://youtu.be/UQvPo7CCcIc?t=1394) — *[2023-04-19](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)*
- Новая **xpSystem** «system detail» ▸ Object: **Only Modifiers in Same System** (игнорирует nxDrag/nxConstraints из Part 1). [▶ 5:59](https://youtu.be/3Qd2e6ZCN6M?t=359) — *[2023-04-17](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)*
- **nxDrag**: Density **Water**, Strength multiplier **50**. Drag зависит от радиуса частицы (крупнее = сильнее тормозит): радиус эмиттера **2**, variation **0.5**. Display **Dots** для скорости вьюпорта. [▶ 27:54](https://youtu.be/6sdlTZsi9kQ?t=1674) — *[2023-04-16](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)*

## Подводные камни
- Порядок модификаторов важен: nxDrag после гравитации, constraints после жидкости. — *[2024-01-02](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)*
- Слишком сильный drag оставляет неподвижное «гало» частиц: уменьшите радиус на detail-эмиттере или силу nxDrag. — *[2023-04-16](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)*

## Все рецепты (9)
- 2025-05-20 · [Органичная пружинящая сеть частиц (birth springs в nxConstraints + слои Forces, переключение групп и пиннинг через nxQuestion)](../../recipes/2025-05-20_spring-network-attract-repel-forces.md)
- 2025-03-11 · [Точные диапазоны mapping по живым данным частиц (min/max из xpConsole → nxColor / Mapping)](../../recipes/2025-03-11_xpconsole-exact-mapping-ranges.md)
- 2025-02-11 · [Реалистичное сопротивление воздуха при взрыве (nxDrag: density, coefficient, radius, speed, mass)](../../recipes/2025-02-11_nxdrag-realistic-air-resistance.md)
- 2024-10-04 · [Органический рост складок, ползущий по статуе (отталкивание в nxConstraints Forces + xpDeformer, группы nxQuestion по vertex map)](../../recipes/2024-10-04_organic-growth-nxconstraints-repulsion-xpdeformer.md)
- 2024-01-02 · [Капля, тающая снаружи внутрь (удержание nxDrag + nxQuestion Neighbors → смена группы + nxConstraints Viscosity)](../../recipes/2024-01-02_nxquestion-neighbor-melt-rig.md)
- 2023-07-04 · [Основы Data Mapping: сила гравитации от радиуса, яркости цвета или пользовательского значения (вкладка Mapping в xpGravity, Extended Data User Value)](../../recipes/2023-07-04_xp-data-mapping-gravity-strength.md)
- 2023-04-19 · [Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)](../../recipes/2023-04-19_tension-fluids-floating-density-nxconstraints.md)
- 2023-04-17 · [Взрывающаяся планета: детальные частицы на поверхности, вращающиеся вместе со сферой (эмиссия с текстуры на смещённой геометрии, Global Transform, отступ по цвету)](../../recipes/2023-04-17_exploding-planet-stuck-detail-particles-global-transform.md)
- 2023-04-16 · [Взрывающаяся планета: эмиссия с текстуры, зависящая от скорости вращения, и слипающиеся обломки (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)](../../recipes/2023-04-16_exploding-planet-spin-driven-emission-nxconstraints-friction.md)
