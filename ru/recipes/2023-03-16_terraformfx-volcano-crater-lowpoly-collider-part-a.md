# Вулканический кратер + низкополигональный коллайдер (TerraformFX noise/gradient/erosion/curve, snow vertex map, mtRemesh)

- Источник: INSYDIUM LIVE! — March 2023 - NeXus, TerraformFX & Taiao — https://www.youtube.com/watch?v=OVUcKWkhUFY (2023-03-16)
- Хост / поколение: C4D; TerraformFX (операторы tfTerrain) + MeshTools mtRemesh; готовим землю для гранул NeXus из part-b
- Задача: вулкан с плоским дном кратера для песочного logo reveal, плюс лёгкий коллайдер и vertex map для статичного разброса.

## Исходная сцена
- Логотип (экструдированный сплайн) анимирован ключами — поднимается из-под земли и в конце чуть **отыгрывает назад**, чтобы стряхнуть гранулы.
- Viewport: у tfTerrain отключён градиент отображения, свой тёмно-серый цвет; свет C4D с **soft shadows**, density ~80%, чтобы читался рельеф.

## Шаги
1. **tfTerrain**: удаляем дефолтные операторы эрозии, оставляем noise; тип шума **Stupl** (завихрения, округлые формы) вместо Turbulence. [▶ 11:25](https://youtu.be/OVUcKWkhUFY?t=685)
2. Добавляем **tfGradient** (radial): поднимаем в пик, затем **falloff curve** (Ctrl-клик — новый узел) формируем в гребень с провалом в центре = кратер. [▶ 12:08](https://youtu.be/OVUcKWkhUFY?t=728)
3. Добавляем **Erosion filter ▸ Hydraulic**, быстрый **2D** солвер (есть и полный 3D на X-Particles). По умолчанию 10,000 частиц живут 30 F; Filter: дождь **Above ~50 см**, чтобы размывались только вершины. [▶ 13:32](https://youtu.be/OVUcKWkhUFY?t=812)
4. Ctrl-перетаскиванием дублируем эрозию; второй проход (**30,000** частиц) стекает по каналам первого и оставляет плоские наносы. [▶ 15:05](https://youtu.be/OVUcKWkhUFY?t=905)
5. Выравниваем кратер: **tfCurve** — linear spline, оба конца тянем вниз и вместе поднимаем (постоянная высота); **Masking ▸ Cylinder field** по размеру кратера; уменьшаем **Blend** оператора, чтобы вернуть часть исходной детализации. [▶ 17:00](https://youtu.be/OVUcKWkhUFY?t=1020)
6. Ещё один **Erosion filter ▸ Snow**: снег ложится в бороздки (меньше radius = меньше снега); включаем **output erosion map** → vertex map на террейне для статичных частиц. [▶ 19:40](https://youtu.be/OVUcKWkhUFY?t=1180)
7. **Current State to Object**, Ctrl-перетаскиванием переносим тег vertex map, tfTerrain выключаем. Дублируем: одна копия для рендера, другая для коллизий. [▶ 20:03](https://youtu.be/OVUcKWkhUFY?t=1203)
8. **mtRemesh** на копии для коллизий: Features Angle **180** (только триангуляция, рёбра не трогает), ровные треугольники Делоне; при Edge Length **16** форма всё ещё держится. **C** — сделать редактируемым. [▶ 21:27](https://youtu.be/OVUcKWkhUFY?t=1287)
9. Режим полигонов, кистью выделяем кратер, **U ▸ I** (инверсия), удаляем → крошечный коллайдер только на кратер. Коллайдер логотипа опускаем, чтобы на старте был скрыт. [▶ 22:36](https://youtu.be/OVUcKWkhUFY?t=1356)

## Как сейчас (новые инструменты)
В Fused 2024.2 у TerraformFX появились Advanced Terrain Shader, канал curvature и tfDistribute (tfDistribute — альтернатива разбросу по snow vertex map). Для коллайдера в бете 2026.1 вместо тега xpCollider — объект **nxCollider**.
