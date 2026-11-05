# Вязкая складывающаяся лента (FLIP из тонкого вращающегося emitter)

- Источник: Top Tip Tuesday — Viscous Folding — https://www.youtube.com/watch?v=uadAsfGPo1Y (2025-12-16)
- Хост / поколение: C4D, Fused 2025.4 (новый GPU FLIP + nxMesher) + Redshift
- Задача: разноцветная лента густой жидкости, складывающаяся сама на себя, как мёд.

## Шаги
1. xpEmitter **Rectangle width 0** (тонкая полоска), анимация вращения; **Rate 1000**, speed 0, радиус **1.4**; цвет — градиентным **shader** в Display.
   (Нарушает обычное FLIP-правило «равномерно частиц на voxel», но солвер справляется.)
2. **nxFluids FLIP**, Voxel **2**, **FLIP Fraction 35** (дефолтные 95 = шумная поверхность; меньше = глаже). **nxGravity**.
3. Stepping → Project Settings **Subframe Steps 5** (с 10 чище; маленьким сценам нужно больше).
4. **Viscosity 30** + Solver Accuracy **Min/Max substeps 3/5** → лента закручивается кольцами.
5. Сохраняем складки: nxGravity **Mapping ▸ Age** → сила на максимуме до 80 F, спадает до 0 к 105 F.
6. Cache (~3 мин).
7. **nxMesher**: radius **0.8**, Polygon Size **0.2** (убирает артефакты на складках); Smoothing **Gaussian** (Influence Range **0.8**, а не дефолтные 5 cm — слишком медленно), strength на максимум; второй слой **Mean Curvature** 5–10 итераций (убирает фасетки/полосы, проверьте, что складки уцелели). **Transfer Color**.
8. Redshift: Vertex Attribute (color map) → **Subsurface color**.
