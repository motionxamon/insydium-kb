# Обзор функций: набор инструментов анимации Jidou (jdDriver, jdAniMate, jdGeoRoll, jdFlowCam, jdGeoFlow)

- Источник: Jidou - Tech Preview — https://www.youtube.com/watch?v=wfxpWHxZypQ (2025-12-08)
- Хост / поколение: C4D; набор Jidou (новинка в Fused 2025.4), меню INSYDIUM ▸ Jidou; не основан на частицах
- Задача: процедурная анимация моушн-графики (драйверы параметров, твины от старта к концу, перекатывание, движения камеры и объектов по пути) без ручных keyframe.
- Совет: открепите каждый инструмент Jidou в отдельную панель — работа строится на drag-and-drop между ним и Object Manager.

## jdDriver — что угодно управляет чем угодно
- Перетащите объекты в список драйвера, затем добавьте параметры (через меню или перетащив параметр из Attribute Manager); дочерний параметр управляется родительским (например, X Pos куба → Y Pos платоника → Bank тора). Ограничения передаются по цепочке, так что перепривяжите ветку, чтобы она оставалась независимой.
- Опции для каждого параметра: **Remap** (Min/Max, Include Zero) и **Clamp** (например −150…150, −360…360). Работает на любом параметре (End Angle арочного сплайна → Strength деформера Bend с переназначением 0–360).
- Встроенные драйверы, у каждого — превью формы волны:
  - **Noise** — типы Noise, Turbulence (octaves), Wavy Turbulence, Fractal Brownian Motion; Separate Seeds для каждого параметра, Output Scale, Amplitude, Detail, Blend Loop, Auto Time.
  - **Wave** — Sine, Gaussian, Triangle, Ramp (пила), Square, Pulse; Period, Phase, Offset, Amplitude, **Decay Rate** (затухающий отскок).
  - **Value** — слайдер с Step, Unit (Integer/Percent/Meter/Float/Degrees), Range min/max → для сборки контрольных ригов (суставы роборуки с ограничением в градусах на каждый сустав).
  - **Time** — начальное/конечное значение за отрезок времени со Speed, Start Time, Auto Time и сплайном (пресеты: Linear, Gaussian = петля туда-обратно).
  - **Color** — управляет любым цветовым полем (цвет отображения объекта, цвет материала Redshift); режимы Time/Cycle/Random (Speed), два цвета или Gradient.
  - **Switch** — булевы параметры (Enable у объектов/источников света): On time, Off time, Repeat Every (поочерёдно мигающие лампы).
- Утилиты: **Merge** (собирает слайдеры Value в одну панель управления), **Sequencer** (драйверы Time как дорожки, которые можно сдвигать и растягивать; разнесение Offset Start/End).

## jdAniMate — твин от старта к концу
- Список Objects ▸ **Store Start / Store End / Clear Stored**; призрачный wireframe и превью пути; Auto Time или ручной конец (удержание в конце); сплайн тайминга для easing; отдельные **дорожки** Position/Scale/Rotation для сдвига каждого канала.
- Иерархии и Cloner: случайные/последовательные **Variations** позиции/вращения/масштаба для каждой части (сборка из деталей); **Effect Position** учитывает движение родителя → изогнутые траектории. Display ▸ **Export Spline** превращает траектории в сплайны.

## jdGeoRoll — перекатывание за хэндлы
- Список Objects (каждый получает дочерний **Handle**, Auto Size, цвет), список Colliders (по умолчанию виртуальный пол на мировом Y=0 или любая геометрия, например ландшафт), Gravity: World −Y / Local / Custom vector / **Object** (катиться по поверхности другого объекта). Store Start задаёт начальную ориентацию. Двигаете хэндл → объект катится/переваливается.

## jdFlowCam — процедурные движения камеры
- Добавьте стандартную или Redshift-камеру; режим **Connect Points**: добавляйте точки камеры; у каждой точки Focal Length, Focal Distance, ориентация, **Weight** (доля времени), Tension, Slide, Ease, **Hold**, Spring, показ конуса. Motion (покачивание с частотой), общий сплайн easing, Up Vector.
- Режим **Path**: Circle, Arc, Line (кран-шоты), Helix, Custom spline; ось выравнивания.
- **Target tag**: несколько целей с временем удержания и сплайном перехода. **Banking**: автоматический крен по кривизне пути (min/max, чувствительность, ease).
- Display: цвета пути/точек, Export Spline (живой), направляющие соотношения сторон (16:9, квадрат, мобильный; Ratio Fit или Absolute Size) для кадрирования под несколько форматов.

## jdGeoFlow — объекты по точкам потока
- Те же опции точек, что и у jdFlowCam, но для геометрии; задайте ось объекта и Align Axis на +Z, чтобы следовать по касательной; **Deform** изгибает объект вдоль пути; режим Paths и Banking; Export Spline.

## Что заменяет
Ручные keyframe, риги на XPresso/Set Driver, теги Align-to-Spline и ручные сплайны для ригов камеры. В Fused 2025.4.1 добавлены режимы воспроизведения Stop/Loop/Ping-Pong/Continue для jdFlowCam и jdGeoFlow (см. также рецепт 2026-10-13 jdGeoFlow emitter path).
