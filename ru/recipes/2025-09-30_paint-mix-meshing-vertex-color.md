# Меширование симуляции смешивания красок и рендер цвета вершин (xpOpenVDBMesher → Redshift)

- Источник: Top Tip Tuesday — Paint Mix Meshing — https://www.youtube.com/watch?v=oHF1dIMGtUs (2025-09-30)
- Хост / поколение: C4D, sim NeXus (nxBlend) + **CPU xpOpenVDBMesher** (эпоха до nxMesher) + Redshift
- Задача: отрендерить смешанную краску из «Paint Mix Sim» с плавными цветовыми переходами.

## Шаги
1. **xpOpenVDBMesher** со всеми тремя эмиттерами. Для цвета вершин нужен плотный меш → **Voxel Size 1**; **Point Radius 2** (менее пузырчато).
2. Filters: удалите стандартный Median; **Laplacian ×2** + **Curvature ×1** (хорошая связка для жидкостей).
3. Вкладка Tags: **Transfer Point Color** → цветовая vertex map на мешере; **Smoothing iterations ~20** убирает шумные цветовые швы.
4. Redshift: SSS-материал (weight 1, scale 4) → Ctrl-клик по Subsurface Color, чтобы добавить вход → нода **Vertex Attribute** с цветовой картой.

## Как сейчас (новые инструменты)
Начиная с Fused 2025.4 используйте **nxMesher** (GPU): Export Tags ▸ Transfer Color + сглаживание цвета, Zhu-Bridson или Spheres + Mean Curvature (см. «nxMesher Export Tags»).
