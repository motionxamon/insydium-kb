# Меши, вытянутые по скорости, и цвет вершин (xpOpenVDBMesher Point Radius, Transfer Velocity, источник Trails)

- Источник: Top Tip Tuesday — Mesh Velocity Stretch — https://www.youtube.com/watch?v=-4wYDCnis9M (2024-11-05)
- Хост / поколение: C4D; **CPU xpOpenVDBMesher** (до nxMesher)
- Задача: прыгающие цветные частицы, превращённые мешером в капли с хвостами, вытянутыми по движению.

## Шаги
1. Частицы r 3 cm, цвет Gradient Random, гравитация + пол.
2. **xpOpenVDBMesher** с эмиттером: по умолчанию **Point Radius 10 = 10 × радиус частицы** (сферы 30 cm).
3. Точный размер: Point Radius **1** → нужны более мелкие воксели: **Voxel size 4 → 1** (иначе сферы пропадают).
4. Tags ▸ **Transfer Point Color** → тег vertex color; немного **smoothing** цвета чистит швы.
5. Tags ▸ **Transfer Velocity** → общий тег color-vertex + отдельные теги X/Y/Z (годятся и для motion blur на рендере).
6. General ▸ Source **Point Type: Trails** → хвосты пропорциональны скорости; **Velocity Factor ~4**.
7. **Trails Delta**: низкое = плавное вытягивание; высокое = видимые цепочки бусин (стилизованный / toon-лук).

## Как сейчас (новые инструменты)
**nxMesher** (Fused 2025.4) на GPU с Export Tags (color, velocity) — см. «nxMesher Export Tags».
