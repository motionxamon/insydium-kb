# X-Particles — xpEmitter (все вкладки)

Источник: docs.insydium.ltd/x-particles/xpemitter/* (Fused 2025, проверено 2026-11-03). Пересказ своими словами.

Всё в X-Particles начинается с **xpEmitter** (обычно он лежит внутри **xpSystem** с папками Emitters / Modifiers / Generators — создаётся автоматически). Эмитить можно из встроенных форм, любого объекта, генератора или сплайна.

## Вкладка Object
- **Emitter Shape:** Rectangle (по умолчанию, плоскость Z+), Circle, Ellipse, Sphere, Box (эмиссия Random или **Grid**), Cylinder, Torus, **Object**, **Defined Emission** (Inline / Circular / 3D Grid / Fragmenter List — точные раскладки, Static Mode = всё на одном кадре), **Instance** (клонирует настройки другого эмиттера).
- Опции формы: Width/Height, H/V Angle (разброс), Cone Angle, Edges/Ring/Surface/Faces Only, переключатель 3D, Offset X&Y (выкл + Z+ = один луч), **Offset Origin** (отрицательный = только внутрь, положительный = только наружу), **Retiming** (100%; 0 = ничего не эмитится).
- **Режим Object — Emit From:** Polygon Center (по умолчанию), Polygons, Polygon Area, Points, Edges (для сплайнов: Even Distribution/Spacing, Emission Point Position %, Spread, Segments), N-gon Center, **Texture**, **Object Color**, **Illumination** (от источников света), Object Position (по одной на каждый дочерний объект — отлично для MoGraph/клонеров), **Object Volume**, **Voxel Grid** (Size, заполнение Random/Ordered вдоль оси, Stop on Grid Full). **Threshold** для vertex color / vertex map.
  - Selection tag / vertex map ограничивают зону рождения. Particle Direction: Normal / Phong / Random / по оси; Invert; Perpendicular to Normal; кривая Random Blend.
  - **Stick Particle to Source Object** (+ Persist While Stuck) — частицы едут вместе с анимированным мешем.
  - **One Particle Per Source Element** (+ Multiplier) — ровно одна частица на точку/полигон, Birthrate игнорируется.
  - Set Radius By Polygon Size. Object Chain для нескольких объектов (Connect Objects — для кривизны).
- Вкладка Texture (Emit From Texture): Texture Tag или Shader; каналы Emit / Color / Radius / Speed / Offset / Scale; Mode — яркость или R/G/B; Invert; Contrast; Max Samples. Проекции Frontal/Camera не поддерживаются.
- Вкладка Topology: ограничения по Height и **Slope** (min/max + сплайн) и эмиссия по **Curvature** (Ray Angle 80°, Number of Rays 100) — например, снег только на плоских верхушках, мох в расщелинах.
- Вкладка Initial State: **Set State** = зафиксировать текущий кадр как стартовый (pre-roll симуляций), Load/Save state (.prt Partio).
- Вкладка Falloff: Infinite / Box / Sphere — должен пересекать поверхность.

## Вкладка Emission
- Режимы: **Rate** (по умолчанию), **Pulse** (Length, Interval, Pulse Spline), **Shot** (Random/Regular/Hexagonal, Shot Time, Duration, Count, Per Frame), **Regular / Hexagonal** (плотное заполнение объёма для флюидов; Jitter, Spacing), **Trigger** (чекбокс Pull Trigger / экшен Change Emitter), **Controlled Only** (эмитит только когда в него спаунят — ставится автоматически для целей спауна).
- **Mode:** Simulate (Legacy, по умолчанию — первая эмиссия на кадре 1), **Simulate** (эмитит на базовом кадре — как клонер), **Motion** (переэмитит каждый кадр — выглядит статично, но velocity есть).
- Emit all Frames / Start–End Emit, Full Lifespan, Lifespan + Variation, Birthrate (по умолчанию в секунду или за кадр) + Variation + Birthrate Spline + управление шейдером.
- **Subframe Emit** (вкл — убирает полосы), No Intersection при рождении, Speed, **Radius** (используется коллизиями/флюидами), Scale (используется xpGenerator/xpSprite/xpFragmenter), список Actions при смерти.
- Вкладка **Motion Inheritance**: направление Linear / Rotational от движущегося эмиттера, Speed Blend.
- Вкладка Thinking Particles: генерировать TP параллельно (legacy-пайплайны MoGraph/TP).
- Подвох: если Shot Count меньше числа кадров Duration, ничего не эмитится.

## Вкладка Extended Data
- **Rotation:** Use Rotation (по умолчанию выкл — нужен для любой ориентированной геометрии!), режимы None / **Tangential** (по направлению движения, ось Z) / Set / Random / Face Camera / Face Object / Face Screen / Up Vector (с xpFollowSurface); Persist Orientation, Rate of Change, Up-Vector (против крена), Simple Spin. xpSpin перекрывает эти настройки.
- Прочие данные: **Rewind Data** (для xpHistory), **UV Emission Data** (нужно для сэмплинга/маппинга текстур), **Nearest Particle Data** (градиенты по P-P дистанции, plexus), **World Speed** (скорость прилипших частиц), Emission Vertex.
- **Physical:** Mass (+ Link Mass to Radius), Friction (у обеих сторон должно быть >0), Bounce (100% = отдать решение коллайдеру), Temperature/Smoke/Fuel/Burn (xpExplosiaFX), User Value.
- **Fluid** (только для xpFluidFX): Liquid/Granular, Density 1000, Viscosity, Vorticity L/S, Surface Tension, для granular — Friction/Stability/Cohesion. Держите размеры частиц примерно одинаковыми на всех эмиттерах.
- **Custom Data:** добавляйте элементы (ID или Name — никогда не оставляйте ID 0 без имени), типы Integer/Float/Matrix/String/Time/Vector, Value on Emission + Variation. Читаются/пишутся через xpCustomData, Questions, Actions.

## Вкладка Display
- Отображение во вьюпорте: Squares (по умолчанию), Dots (быстрее всего), Ticks, Axes, Box, Spheres (медленнее всего), Lines (длина по скорости/радиусу/фиксированная), Circles (Filled + контур), Cylinder, Pyramid, Arrow, Plane, None. LOD, Display Size Factor, переключатель Show Particles, **Display Constraints**.
- **Color Mode:** Icon color / Single / Random / Gradient Random / **Gradient (Parameter)** — по Age, Speed, Radius, Fluid Density, Mass, Temperature, Smoke, Fire, Fuel, Distance Traveled, Direction, P-P Distance, Rotation (Auto-диапазон или Min/Max) / Use Shader. Gradient (Parameter) перекрывает xpColor.
- HUD (ID частиц + одно значение данных), визуализация Modifier Field (векторы модификаторов движения — отлично для отладки турбулентности).
- Оранжевая иконка = активен NeXus/GPU.

## Groups, Questions, Modifiers, Editing, Advanced
- **Вкладка Modifiers:** по умолчанию каждый модификатор в сцене влияет на каждый эмиттер. **Only in Same System** = только модификаторы внутри того же xpSystem. Перетащите модификаторы в Objects и кликом переключайте жёлтую галочку (включить) / синий минус (исключить). Деформеры/эффекторы C4D работают, только если указаны здесь или вложены в эмиттер.
- Вкладка Groups: Groups to Use перекрывает отображение. Вкладка Questions: questions на уровне эмиттера.
- Advanced: Threading (вкл; выключите при странных ошибках), **Random Seed** — давайте каждому эмиттеру свой seed.
