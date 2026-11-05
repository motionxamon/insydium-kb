# Гладкий меш жидкости с сохранением тонких усиков (xpOpenVDBMesher Point Radius, Voxel Size, фильтры Curvature + Offset)

- Источник: Top Tip Tuesday — nxFluids Detailed Meshes — https://www.youtube.com/watch?v=vbolWCL3KgY (2023-11-28)
- Хост / поколение: C4D; sim G2 nxFluids PBD, меширование через **CPU xpOpenVDBMesher** (до nxMesher); рендер в Cycles 4D
- Задача: гладкий, «скользкий» меш жидкости без потери мелких усиков из симуляции частиц.

## Исходная сцена
Сферический эмиттер, **Shot – Hexagonal**, speed 0, radius **1 cm**; **nxTurbulence** Voronoi strength **9**; **nxFluids PBD**, substeps **5**, External Pressure **100** (усиливает усики), Attraction **40**, Repulsion **80**. Кэш за ~17 с.

## Шаги
1. **xpOpenVDBMesher**, General ▸ перетащите закэшированный эмиттер. По умолчанию результат «пузырчатый»: **Point Radius 10 = оболочка 10 × радиус частицы**. [▶ 2:05](https://youtu.be/vbolWCL3KgY?t=125)
2. Опустите **Point Radius** до **~1.5**; уменьшите **Voxel Size до 1**, чтобы маленькие оболочки успевали семплироваться. [▶ 2:35](https://youtu.be/vbolWCL3KgY?t=155)
3. Filters: стандартный **Median** сглаживает, но с ростом итераций съедает тонкие перемычки — удалён. [▶ 3:47](https://youtu.be/vbolWCL3KgY?t=227)
4. Вместо него добавьте фильтр **Curvature** и поднимите итерации (~4): убирает бугры, сохраняя объём. [▶ 4:14](https://youtu.be/vbolWCL3KgY?t=254)
5. Немного потеряли объём → Point Radius **1.5 → 1.7**, затем ещё чуть сгладьте через Curvature. [▶ 4:54](https://youtu.be/vbolWCL3KgY?t=294)
6. Верхний фильтр **Offset** — чтобы стянуть поверхность обратно к частицам; по умолчанию он слишком сильный, снижайте strength, пока меш не перестанет пропадать. [▶ 5:49](https://youtu.be/vbolWCL3KgY?t=349)
7. Назначьте SSS-шейдер random walk; рендер в Cycles 4D. [▶ 6:32](https://youtu.be/vbolWCL3KgY?t=392)

## Подводные камни
- Маленький Point Radius без уменьшения вокселей — и части меша исчезают.
- Порядок фильтров важен: Curvature для сглаживания, Offset последним для подтяжки.

## Как сейчас (новые инструменты)
**nxMesher** (Fused 2025.4, GPU) — без мерцания, с **layered smoothing**; в 2026.1 добавлено сглаживание **Detail Aware**, сделанное как раз для сохранения тонких деталей.
