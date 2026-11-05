# Живые частицы как точки, управляющие Displacer (XP Editing + C4D Fields Delay)

- Источник: Top Tip Tuesday — Particle Deformation — https://www.youtube.com/watch?v=oVePtsodRBs (2024-01-09)
- Хост / поколение: C4D; CPU xpFollowSurface вместе с NeXus GPU nxFluids SPH + nxTurbulence; C4D Displacer, Fields, Smoothing
- Задача: частицы, ползущие по сфере, органично выдавливают её высокополигональную копию.

## Шаги
1. **xpFollowSurface** со сферой (скройте её).
2. **nxFluids SPH**, +1 substep (CPU- и GPU-модификаторы можно смешивать на одном эмиттере). [▶ 0:49](https://youtu.be/oVePtsodRBs?t=49)
3. **nxTurbulence** Voronoi, высокая strength, крупный scale. [▶ 1:12](https://youtu.be/oVePtsodRBs?t=72)
4. Частицы теряются: дистанция follow-surface 10 → **200 cm** (эмиттер уже внутри неё), **Pull 100%**, немного **Surface Friction** для успокоения. [▶ 1:48](https://youtu.be/oVePtsodRBs?t=108)
5. Эмиттер ▸ включите вкладку **XP Editing** → в режиме Point каждая частица — выделяемая точка, которую могут читать Fields. [▶ 2:31](https://youtu.be/oVePtsodRBs?t=151)
6. Скопируйте сферу, 350 сегментов, отражающий материал; дочерний **Displacer**: Shading = **Color white**, Height 10 cm (позже 30). [▶ 3:32](https://youtu.be/oVePtsodRBs?t=212)
7. Displacer ▸ Fields: перетащите **эмиттер** → бугры везде, где есть частицы. Уменьшите радиус эмиттера для более мелкой детализации. [▶ 4:39](https://youtu.be/oVePtsodRBs?t=279)
8. Добавьте слой поля **Delay** (Smooth, уменьшенный) для органичного запаздывания; при желании наложите несколько delay. [▶ 4:26](https://youtu.be/oVePtsodRBs?t=266)
9. Деформер **Smoothing** под Displacer, поднимите stiffness. [▶ 5:28](https://youtu.be/oVePtsodRBs?t=328)

## Как сейчас (новые инструменты)
**nxFollowGeo** заменяет xpFollowSurface; режим nxFalloff **Points** и только для C4D — **nxFalloffMap** (falloff → vertex maps) в бете 2026.1.
