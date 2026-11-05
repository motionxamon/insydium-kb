# Обзор функций: TerraformFX 2023.3 — tfTrace, tfRiver, tfFormula, шейдер Gradient UV, солнечный риг, пресеты

- Источник: INSYDIUM Fused Release Update — July 2023 - TerraformFX Sneak Peek — https://www.youtube.com/watch?v=aPMCwaeUtvc (2023-06-19) + живое демо в INSYDIUM LIVE! July 2023 (2023-07-05)
- Хост / поколение: C4D; TerraformFX (генератор ландшафтов на height field), Fused 2023.3 — не на частицах
- Задача: обзор новых инструментов дизайна, анимации и look-dev ландшафтов.

## Новые операторы
- **tfTrace** — трассирует геометрию сцены лучами в height field (череп → остров). Лучи идут строго вверх от нулевой высоты, поэтому **нависаний не бывает** (кладите модель на бок). Затем **Blur** (Box, быстрый) над noise, чтобы сгладить ступеньки; опционально выход **Vertex Map** для отдельного текстурирования.
- **tfRiver** (фильтр) — процедурные реки: от пользовательского сплайна (**Settle Spline** в живом демо) или **Perlin Worm** (точки старта/конца, вода течёт вниз по склону; старт по умолчанию в самой высокой точке). **Create River Material**; **Secondary Rivers** (по умолчанию 5) и вторичные от вторичных; **Export Rivers** как живые сплайны (например, для частиц). Width, Depth, Deform/Wiggle/Smoothing, режимы Altitude (Downhill Flow / Project, обратное течение), Render ▸ **Edge Noise** strength/scale для размытых берегов.
- **tfFormula** — введите или вставьте формулу для абстрактных анимированных ландшафтов; переменные (например, project time) можно анимировать ключами.

## Look-dev и viewport
- Шейдер **Gradient UV** — 2D-градиент с четырьмя цветовыми входами, привязанный к U/V ландшафта; во входы можно подавать шейдеры (noise в V, шейдер **Terrain Operator** в режиме **Altitude** в U, кривая Remap) для смешивания камня и травы.
- Солнечный риг **tfTerrain**: pitch/heading солнца, тени (включите Shadows во viewport), ambient-дымка; при Make Editable ландшафта становится переиспользуемым световым ригом.
- **5 пресетов ландшафта**: Mountain, Valley, Island, Canyon, River.

## Заметки
Позже: Fused 2024.2 добавил Advanced Terrain Shader, канал curvature, tfDistribute. В C4D 2024+ Redshift по умолчанию запекает шейдеры TerraformFX в 128×128 — поднимите значение.
