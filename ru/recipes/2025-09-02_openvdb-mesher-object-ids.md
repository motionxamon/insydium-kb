# Один меш — свой материал для каждого эмиттера (xpOpenVDBMesher Object IDs → Redshift)

- Источник: Top Tip Tuesday — Particle Mesh IDs — https://www.youtube.com/watch?v=e49Ob7tPXfc (2025-09-02)
- Хост / поколение: C4D, CPU **xpOpenVDBMesher** + закэшированная вязкая симуляция NeXus + Redshift
- Задача: три цветные слизи из трёх эмиттеров, объединённые в один меш, но с раздельным шейдингом.

## Шаги
1. **xpOpenVDBMesher** с 3 эмиттерами; **Voxel 1.5**; **Point Radius 4** (по умолчанию 10 = ×10 радиуса частиц, слишком комковато). [▶ 1:22](https://youtu.be/e49Ob7tPXfc?t=82)
2. Filters: уберите Median, **Curvature** ×7 итераций («в 99 % случаев для жидкостей»). [▶ 1:53](https://youtu.be/e49Ob7tPXfc?t=113)
3. Для каждого эмиттера в списке мешера: **Object ID** (vertex map) + **Smoothing 7** (размывает швы). [▶ 3:57](https://youtu.be/e49Ob7tPXfc?t=237)
4. Redshift: три SSS Standard материала (розовый / зелёный / оранжевый, SSS scale ~10) → **Material Blender**: base — розовый; Layer 1 = зелёный с Blend Color = **Vertex Attribute (ID map 1)**; Layer 2 = оранжевый с Blend Color = Vertex Attribute (ID map 2) (Ctrl-клик, чтобы вывести входы слоёв). [▶ 7:41](https://youtu.be/e49Ob7tPXfc?t=461)

## Как сейчас (новые инструменты)
В **nxMesher** кнопки Export Tags ▸ **Emitter ID** делают то же самое на GPU (см. "nxMesher Export Tags").
