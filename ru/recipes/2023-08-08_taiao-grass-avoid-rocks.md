# Клочковатая трава на ландшафте, которая исчезает у камней или обтекает их (toGrass Avoid Objects Cull/Repel, tfRock)

- Источник: Top Tip Tuesday — toGrass Avoid — https://www.youtube.com/watch?v=HiRKNNjygt0 (2023-08-08)
- Хост / поколение: C4D; Taiao (toGrass) + TerraformFX (tfTerrain с noise, tfRock)
- Задача: густая трава разной длины только на верхней поверхности 3D-ландшафта, которая держится на расстоянии от стоячих камней или огибает их.

## Шаги
1. INSYDIUM ▸ Taiao ▸ **toGrass**, перетащите **tfTerrain** как объект генерации.
2. Трава растёт и на боковых стенках, и снизу: слой травы ▸ Generation: **Slope Max 89°** (убирает вертикальные стенки), **Height Min 0.1%** (убирает низ). [▶ 0:53](https://youtu.be/HiRKNNjygt0?t=53)
3. Вкладка Geometry: Spline → **Polygon object**; Width **0.5**, высота заметно больше, чуть больше сегментов, немного **Bend variation**. [▶ 1:23](https://youtu.be/HiRKNNjygt0?t=83)
4. Верхние параметры вкладки Object: используйте **texture source** для **Length** (не для плотности) → шейдер **Noise**; поднимите Low Clip / опустите High Clip для контраста, затем замените чёрный на серый, чтобы в тёмных зонах трава была короче, но не превращалась в обрубки. [▶ 1:57](https://youtu.be/HiRKNNjygt0?t=117)
5. Density **100 → 300**. [▶ 2:46](https://youtu.be/HiRKNNjygt0?t=166)
6. Слой травы ▸ Materials: перетащите два материала → они случайно распределяются по травинкам. [▶ 3:05](https://youtu.be/HiRKNNjygt0?t=185)
7. Камни: INSYDIUM ▸ TerraformFX ▸ **tfRock**; скопируйте материал ландшафта (чуть менее коричневый); растяните размер по Y, чтобы получился стоячий камень; утопите его в землю. [▶ 3:40](https://youtu.be/HiRKNNjygt0?t=220)
8. toGrass ▸ **Avoid Objects**: закиньте tfRock; увеличьте **Distance**, чтобы расширить зазор. Для проверки выключите отображение avoid-объекта. [▶ 4:22](https://youtu.be/HiRKNNjygt0?t=262)
9. Режим **Cull** (травинки удаляются) или **Repel** (травинки по краю гнутся и обтекают камень — лучше всего с небольшой дистанцией). [▶ 5:04](https://youtu.be/HiRKNNjygt0?t=304)

## Как сейчас (новые инструменты)
В Fused 2025.x те же инструменты Taiao; в Fused 2024.2 появился scatter точек роста Taiao для большего контроля над распределением. Замены в NeXus нет.
