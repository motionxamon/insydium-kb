# Свет и смешивание камня с восковой органикой по анимированной vertex map (Redshift Material Blender, Vertex Attribute, объёмный спот с гобо)

- Источник: INSYDIUM Training — Organic Growth - Part 2 — https://www.youtube.com/watch?v=NS32rZns-Eo (2024-10-10)
- Хост / поколение: C4D + **Redshift**; на входе — анимированный Alembic бюста с vertex map роста из первой части (в этой части инструментов частиц нет)
- Задача: каменная статуя, обрастающая органикой с эффектом подповерхностного рассеивания, с драматичным трёхточечным светом и объёмными лучами.

## Исходная сцена
Анимированный Alembic бюста с **анимированной vertex map** (0 = камень, 1 = рост). На время работы выключите его деформер сглаживания, для финала включите снова.

## Шаги — свет
1. **RS Area Light** + **Target tag**, нацеленный на бюст → ключевой свет. [▶ 0:45](https://youtu.be/NS32rZns-Eo?t=45)
2. Копии Ctrl-перетаскиванием: **Rim** с противоположной стороны (Shape увеличен по Y, отодвинут назад/вверх); **Fill** с Intensity **20 → 10** ради контраста. Проверяйте источники по одному. [▶ 3:13](https://youtu.be/NS32rZns-Eo?t=193)

## Шаги — материал камня
3. RS **Standard** material. Нода **Maxon Noise**: тип Luka, **Octaves 15** (нужно для детального бампа), Overall Scale **1200**, подберите seed. [▶ 5:12](https://youtu.be/NS32rZns-Eo?t=312)
4. Noise → нода **Bump Map** (цвет → вектор) → вход Bump у Standard; Height Scale **5**. Поднимите roughness отражений (без «мокрого» вида). [▶ 6:34](https://youtu.be/NS32rZns-Eo?t=394)
5. Тот же noise → **Scalar Ramp** (линейная; поднять точку чёрного, опустить точку белого) → Base Color для мягкой «молочной» вариации. [▶ 8:17](https://youtu.be/NS32rZns-Eo?t=497)

## Шаги — органический материал
6. Ctrl-перетаскиванием вторая нода Standard: **Transmission weight 1**, шершавые отражения, цвет transmission. [▶ 11:38](https://youtu.be/NS32rZns-Eo?t=698)
7. **Scatter color** ничего не делает, пока **Scatter Depth** > 0: 1 = непрозрачно, 80 = воск/полупрозрачно; использовано **10**. Roughness отражений задаёт мокрый или сухой вид. [▶ 12:52](https://youtu.be/NS32rZns-Eo?t=772)

## Шаги — смешивание
8. Нода **Vertex Attribute**, атрибут = анимированная vertex map → **Material Blender**: камень = Base, органика = цвет Layer 1, vertex attribute → **Layer 1 Blend Color** (чёрный = камень, белый = рост). Анимируется вместе с ростом. [▶ 16:04](https://youtu.be/NS32rZns-Eo?t=964)

## Шаги — объёмный свет
9. Скопируйте ключевой, тип **Spot**, поставьте сверху и чуть сзади. Добавьте **RS Environment** (не RS Sky) → у Spot Intensity **10,000**, Exposure **2**, Cone Angle пошире. [▶ 18:59](https://youtu.be/NS32rZns-Eo?t=1139)
10. Spot ▸ Color ▸ Texture: **гобо** из Content Browser (листья дерева; подойдёт любая ч/б картинка или noise). Details: смягчите тени, включите **softness affects gobo**, Softness **50**. [▶ 21:13](https://youtu.be/NS32rZns-Eo?t=1273)
11. Выделите key/rim/fill ▸ Details: выключите **volume contribution**, чтобы туман освещал только спот. [▶ 22:24](https://youtu.be/NS32rZns-Eo?t=1344)

## Как сейчас (новые инструменты)
Если маска роста задаётся частицами, **nxFalloffMap** из NeXus 2026.1 (C4D) запекает фоллофы в теги vertex map / vertex color для ноды Vertex Attribute; сам рост можно получить через **nxBioLogic** / nxDendrite.
