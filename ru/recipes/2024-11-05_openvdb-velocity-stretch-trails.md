# Меши, вытянутые по скорости, и цвет вершин (xpOpenVDBMesher Point Radius, Transfer Velocity, источник Trails)

- Источник: Top Tip Tuesday — Mesh Velocity Stretch — https://www.youtube.com/watch?v=-4wYDCnis9M (2024-11-05)
- Хост / поколение: C4D; **CPU xpOpenVDBMesher** (до nxMesher)
- Задача: прыгающие цветные частицы, превращённые мешером в капли с хвостами, вытянутыми по движению.

## Шаги
1. Частицы r 3 cm, цвет Gradient Random, гравитация + пол. [▶ 0:27](https://youtu.be/-4wYDCnis9M?t=27)
2. **xpOpenVDBMesher** с эмиттером: по умолчанию **Point Radius 10 = 10 × радиус частицы** (сферы 30 cm). [▶ 1:17](https://youtu.be/-4wYDCnis9M?t=77)
3. Точный размер: Point Radius **1** → нужны более мелкие воксели: **Voxel size 4 → 1** (иначе сферы пропадают). [▶ 2:52](https://youtu.be/-4wYDCnis9M?t=172)
4. Tags ▸ **Transfer Point Color** → тег vertex color; немного **smoothing** цвета чистит швы. [▶ 3:29](https://youtu.be/-4wYDCnis9M?t=209)
5. Tags ▸ **Transfer Velocity** → общий тег color-vertex + отдельные теги X/Y/Z (годятся и для motion blur на рендере). [▶ 4:41](https://youtu.be/-4wYDCnis9M?t=281)
6. General ▸ Source **Point Type: Trails** → хвосты пропорциональны скорости; **Velocity Factor ~4**. [▶ 5:17](https://youtu.be/-4wYDCnis9M?t=317)
7. **Trails Delta**: низкое = плавное вытягивание; высокое = видимые цепочки бусин (стилизованный / toon-лук). [▶ 6:42](https://youtu.be/-4wYDCnis9M?t=402)

## Как сейчас (новые инструменты)
**nxMesher** (Fused 2025.4) на GPU с Export Tags (color, velocity) — см. «nxMesher Export Tags».
