# Металлическая табличка с вмятинами от пуль (xpClothFX plasticity + damping)

- Источник: Top Tip Tuesday — xpCloth Dents — https://www.youtube.com/watch?v=tGkpVuhTQCE (2024-01-30)
- Хост / поколение: C4D; CPU X-Particles (xpClothFX, xpConstraints, xpGravity, xpCache)
- Задача: частицы, выпущенные в низкополигональную табличку, оставляют постоянные вмятины, а не пружинящую рябь.

## Исходная сцена
Редактируемая плоскость "sign" с выделением точек по периметру; эмиттер-«пушка», стреляющий частицами сквозь неё.

## Шаги
1. Выделите табличку ▸ X-Particles ▸ Dynamics ▸ ClothFX ▸ **Create Cloth** → cloth tag, constraints object (столкновения P-P), gravity, cloth modifier, cloth emitter (по одной частице на вершину). [▶ 0:57](https://youtu.be/tGkpVuhTQCE?t=57)
2. Включите отображение cloth-частиц кругами: по умолчанию они перекрываются. Cloth tag ▸ Advanced ▸ **Set Particle Radius off** → используется радиус эмиттера (по умолчанию 3 см) — частицы почти касаются, идеально для вмятин. [▶ 1:52](https://youtu.be/tGkpVuhTQCE?t=112)
3. Advanced ▸ **Pin** вкл., перетащите выделение периметра. [▶ 2:23](https://youtu.be/tGkpVuhTQCE?t=143)
4. Cloth emitter ▸ вкладка Modifiers: **исключите gravity**, чтобы табличка не провисала. [▶ 2:49](https://youtu.be/tGkpVuhTQCE?t=169)
5. Cloth options ▸ **Plasticity** (threshold 1.1): пружины, растянутые сверх порога, не возвращаются → вмятины. [▶ 3:13](https://youtu.be/tGkpVuhTQCE?t=193)
6. Энергия разбегается рябью, как по тонкой фольге → поднимите **Damping** до ~34%. [▶ 4:09](https://youtu.be/tGkpVuhTQCE?t=249)
7. **xpCache** (150 F), затем положите табличку под **Subdivision Surface**, чтобы сгладить грани после кэширования. [▶ 5:03](https://youtu.be/tGkpVuhTQCE?t=303)

## Подводные камни
- Держите ткань низкополигональной ради скорости; сглаживайте потом.

## Как сейчас (новые инструменты)
Материал metal в **nxMPM** / пресет nxMaterial Metal (2026.1 beta) на GPU; nxShatter для разрушения.
