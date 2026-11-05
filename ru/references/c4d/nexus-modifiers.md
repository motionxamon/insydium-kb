# NeXus (C4D) — справочник по модификаторам

Источник: docs.insydium.ltd/nexus/modifiers/* (Fused 2025, проверено 2026-11-03). Пересказ.
У всех nx-модификаторов есть общие вкладки: **Groups Affected**, **Mapping** (управление любым параметром через данные частиц), вкладка **Fields**; у большинства есть **стек слоёв, который обрабатывается снизу вверх** с Blend-режимами и falloff для каждого слоя (Box/Linear/Sphere/Noise или объект nxFalloff).

## Движение
- **nxTurbulence** — многослойный noise (Simplex/Curl/Turbulence/Wavy/VoroNoise/FBM/Cubic). Curl Blend/Curl Add = смешивание с velocity от других модификаторов. Axis Direction Scale — для плоского noise. Octaves по умолчанию 1. Подробности в nexus-dynamics-logic.md.
- **nxAttract** — притягивает к объектам. Type **Velocity** (по умолчанию, перебивает другие модификаторы скорости) или **Acceleration** (работает вместе с остальными). Force 30, Acceleration, Speed Limit, Object Select (Nearest/Furthest/Average/Index/Random). Пустой список Attractors = никакого эффекта.
- **nxAvoid** — уводит частицы от объектов; On Detection: Change Direction / Freeze / Die. Detection Distance должна быть больше, чем частица пролетает за кадр. Отступ Object Shell. Freeze можно отменить через Action или xpNegate.
- **nxCover** — частицы садятся на объекты и покрывают их. Object Mode Sequence (морфинг между объектами!) / Nearest / Furthest / Index / Random; Operation Polygon Area / Points / Edges / Volume / Texture (Resolution 128); Speed Mode Use Speed / **Time to Target** (прибытие точно к нужному кадру); Holding Free / Spring / Stick / Attract; Hold Time; Cycle (только для Sequence). Применение: частицы складываются в логотип/форму, морфинги.
- **nxDirection** — многослойный: Direction Force (Direction/Twist/Attract ±100%), Circular (emitter на Y+, Y-Axis Kick), Ring (Loop на 360°)… Force Mode Velocity.
- **nxDrag** — среда Air (по умолчанию)/water/mercury/Custom density, Drag Coefficient по форме, Strength Multiplier. Зависит от скорости, радиуса и массы частиц.
- **nxExplode** — разлёт наружу; Timing Always On / at Scene Time / at Particle Age; Timing Mode Equals (срабатывает один раз) / ≥ / ≤; Time 30 F; From Particle Mass Center или This Modifier; Speed, Variation; Unstick if Necessary (включено).
- **nxFlock** — поведения Cohesion / Separation / Alignment / Chaos / Swarming (нужно ≥2 эмиттеров/групп), угол обзора Periphery; Reactions (дочерние объекты): Pursuit / Flee / Arrive / Orbit с режимами тайминга; Avoidance Soft/Hard; Min/Max Speed, Natural Limits (максимальный угол поворота). Применение: птицы, рыбы, насекомые, эффекты погони.
- **nxFollowGeo** — один объект для следования по поверхности, рёбрам и сплайнам. Surface: Pull/Push/Offset/Distance/Friction/FOV, Release None (по умолчанию — частицы никогда не отрываются!) / Texture / Selection / Falloff / Time. Edge: плотность прилегания к ребру, Smoothing. Spline: Guide (%) или Force (по расстоянию), Activate Range 2 m, Attract 10%, Follow 40%, Align; Extended Data **Offset / Twists / Twist Radius / Radius Along Length** (спирали и трубки вдоль сплайнов); Release Spline End / Falloff / Time / Selection с On Release Loop/Reverse/Kill/Change Group; поддержка многосегментных сплайнов. В NeXus заменяет xpFollowSurface + xpFollowSpline + xpSplineFlow.
- **nxGravity** — Strength (−Y; отрицательное значение = вверх), Variation на частицу или на кадр (дрожание), **Effect Towards** объект = точечная гравитация.
- **nxLimit** — ограничивает velocity/position/scale/rotation/speed/radius/mass/user value в каждом слое.
- **nxPush** — расталкивает частицы на Distance (Absolute 10 cm или режим Particle Radius), Strength, Iterations 5, Only Same Group. Против слипания, для равномерного распределения. Гораздо быстрее xpPushApart.
- **nxRotate** — вращает весь поток вокруг оси (а не отдельные частицы). Force (по умолчанию, раскручивает по спирали наружу; Attraction стягивает) или Velocity (плотно, но перебивает turbulence). Escape Velocity.
- **nxSpeed** — Incremental (добавляет каждый кадр внутри falloff — держите значения совсем маленькими) / Absolute / Acceleration / Range (Time Mode Birth/Particle/Frame).
- **nxSpin** — вращение каждой частицы: Rotate, Facing (Face Camera), Range (по возрасту), Incremental.
- **nxSticky** — прилипание к полигональным объектам (параметрику сделайте редактируемой; сплайны не подходят). Probability, Range, Tolerance (держите низким), Outside Only, Custom Offset/Distance, Sticky Time + Falloff (очень большое время = навсегда).
- **nxVorticity** — усиливает завихрения во флюидах по velocity соседей. Radius (маленький = мелкая быстрая детализация, >100% = крупные вихри), Strength (накопительный — при больших значениях симуляция нестабильна), **Force Limit**, Exclude Emitters.
- **nxWind** — Standard или **Von Karman** (реалистичные порывы: Friction Velocity, Scale Length), Strength, Variation, Turbulence по осям, Local/World, Frequency.

## Данные частиц
- **nxBlend** — соседние частицы смешивают Color (включено по умолчанию), Radius, Mass, Scale, Rotation в пределах Distance; Blend-режимы; Strength; **Max Blend** (номер кадра, на котором смешивание останавливается); Weighting по эмиттерам (например, эмиттер A 100% доминирует над B 0%). Классика: два цветных эмиттера смешиваются, как краска.
- **nxColor** — многослойная перекраска; Change on Birth Only; Change Rate Instant / Frame Time (плавный переход) / Custom; Threshold = случайная вероятность; слои Noise / Gradient / Texture Tag (для текстуры нужны UV-данные + UV Emission Data в Extended Data эмиттера). Shader запекается в GPU-текстуру (ограничено разрешением).
- **nxInfectio** — рост/распространение от **Seed Object** (Add Seed Object — обязательно). Состояния uninfected → incubating → infected; Color Mode Fixed / Gradient / Use Groups / none; Search Radius, Max Infected (скорость распространения), Infected Lifespan (1 кадр = частица гибнет при заражении → проявления «отслаиванием/растворением»), Search for Nearest Once (выключайте для движущихся частиц); Incubation по Color частицы (чёрные никогда не заражаются) / Rate / Radius / Mass; Immunity.
- **nxKill** — Outside Bounds (по умолчанию — делайте бокс с запасом!) / Inside / Objects / Outside Camera FOV (Widen FOV) / Clamp to Max Particles; Only Born.
- **nxScale** — многослойные radius/scale/mass: Range, Noise, Set Value, Set by Falloff, по скорости/ускорению. Timing по умолчанию On Birth.

## Утилиты
- **nxUpres** — интерполирует Source-эмиттер с малым числом частиц на Destination-эмиттер с большим (например, 2 k → 80 k). Сила по каждому свойству (Position, Radius, Color, Velocity, Mass, Group), Max Count (больше = плавнее/медленнее), Limit Distance, **Push** для сохранения объёма. Workflow: дешёвая sim, cache, затем upres.
