# Светящаяся инопланетная лилия из одного лепестка (слои Taiao Flower + emission в Cycles 4D с маской по Facing)

- Источник: INSYDIUM LIVE! — November 2023 – X-Particles, NeXus, Taiao, MeshTools & Cycles 4 — https://www.youtube.com/watch?v=qaso-gPGBnI (2023-11-16)
- Хост / поколение: C4D; Taiao (объект Flower); рендер Cycles 4D. Часть A из 3 (сегмент Майка Бэтчелора из разбора Black Friday-ролика)
- Задача: лилия с одним лепестком в духе «Аватара», с рисованными текстурами, у которой светятся края и точки.

## Шаги — моделинг
1. Insydium ▸ Taiao ▸ **Flower**. Удалите слой **Sepal** (у лилии один лепесток прямо от стебля); на время формовки скройте Stamen + Petal. [▶ 14:00](https://youtu.be/qaso-gPGBnI?t=840)
2. **Pistil** width/height ~2, **Receptacle** width 2, чтобы они сливались, затем height ~3; тангенсом сделайте форму капли; Subdivision 1 на обоих. Бросьте на каждый материал стебля; если швы не сходятся, переключите проекцию материала UV **+V → −V**. [▶ 14:59](https://youtu.be/qaso-gPGBnI?t=899)
3. **Petal**: Count **1**. Geometry: Width 10, Height 25, Segments 10 × 20, Subdivision 1; небольшая Thickness, сужающаяся сплайном **Depth** у толщины (толще у основания). Profile: тяните ручки, чтобы кончик сходился в точку. **Edge Noise 200%**. [▶ 17:11](https://youtu.be/qaso-gPGBnI?t=1031)
4. Orientation angle 90, чтобы работать с лепестком вертикально. Modifiers (у каждого слоя свой стек): **Fold** (уже стоит на лепестках) — сильный fold, поднимите Shape, чтобы края перекрывались, **Offset Fold** для шва, затем раскройте через **Bias** + кривую bias tangent (добавьте точку, чтобы подвернуть нижний шов). [▶ 18:31](https://youtu.be/qaso-gPGBnI?t=1111)
5. **Furling** с bias, чтобы лепесток провис, второй Furling, чтобы приподнять кончик (форма лодочки), **Turbulence** для неровности — сдвиньте её bias, чтобы не искажался кончик. [▶ 20:03](https://youtu.be/qaso-gPGBnI?t=1203)
6. **Stamen**: Count 1, снимите **Fit to Pistil** (иначе он следует нормалям пестика и наклоняется), увеличьте scale, удалите две ручки shape для конуса, больше сегментов, добавьте Furling + Turbulence; материал стебля. [▶ 20:38](https://youtu.be/qaso-gPGBnI?t=1238)
7. Ориентацию лепестка исправьте через **Layer Rotation 90** у слоя petal, затем angle / radius / position, чтобы посадить его в стебель. [▶ 22:04](https://youtu.be/qaso-gPGBnI?t=1324)
8. Положите цветок в слот **Custom Object** растения Taiao, чтобы разместить его на растении. [▶ 1:00:08](https://youtu.be/qaso-gPGBnI?t=3608)

## Шаги — материал Cycles 4D (Object material = Principled)
9. Перетащите рисованные текстуры (diffuse нарисован в Procreate, normal сделан в Photoshop). Color → Base Color; нода Normal Map в **Non-Color Data** → Normal. [▶ 25:38](https://youtu.be/qaso-gPGBnI?t=1538)
10. **Mix Shader** (Principled + **Emission** с цветовой текстурой). Простой микс 50% выглядит грязно, поэтому Factor управляется **Layer Weight ▸ Facing** → **Color Ramp** (поджат); emission strength ~3 → светящиеся края. [▶ 27:09](https://youtu.be/qaso-gPGBnI?t=1629)
11. Второй Mix Shader с белым Emission, замаскированным рисованной **альфой точек**, strength 8 → светящиеся крапинки. [▶ 29:10](https://youtu.be/qaso-gPGBnI?t=1750)

## Подводные камни
- Текстуры можно рисовать где угодно (Substance, Procreate…), потому что Taiao сам генерирует UV.

## Как сейчас (новые инструменты)
По-прежнему Taiao — в поздних версиях добавились венация toLeaf + пресеты (2024.2); см. рецепты 2025-10-23 (кувшинка) и 2024-05-28 (тычинки). В Redshift та же идея — Fresnel/facing-рампа, смешивающая эмиссионный слой.
