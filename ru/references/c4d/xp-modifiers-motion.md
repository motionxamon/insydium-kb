# X-Particles — модификаторы движения (CPU, `xp*`)

Источник: docs.insydium.ltd/x-particles/modifiers/* (Fused 2025, проверено 2026-11-03). Пересказ.

**Общая схема для всех классических модификаторов:** `Mode` = **Independent** (по умолчанию — действует на любую частицу в своём field/falloff) или **Action-Controlled** (ничего не делает, пока xpAction "Affect by Modifier"/question не включит его для частицы). У каждого модификатора есть Groups (включение/исключение групп частиц), Falloff/Fields и вкладка Mapping. `Type` **Velocity** = полностью берёт движение на себя (перебивает, например, turbulence); **Force** = добавляется к другим модификаторам.
Колонка с GPU-аналогами → см. legacy-vs-nexus.md.

| Модификатор | Что делает | Ключевые настройки / значения по умолчанию | Подводные камни |
|---|---|---|---|
| **xpTurbulence** | движение по noise | Noise Standard (по умолчанию) / Turbulence / Wavy / **Curl** (Blend, Add) / FBM / Simplex (MultiOctave/Raw); Scale, Frequency (только Standard и Curl), Octaves (не в Standard), Strength; оси | Большой Scale = эффект гасится; Octaves 0 = ничего; границы для Curl — только примитивы/полигоны. → nxTurbulence |
| **xpAttractor** | притягивает к себе/объектам | Velocity (по умолчанию) / Force; Object Select Nearest / Furthest / Average / Index / Random | Ближайшая цель может смениться посреди анимации. → nxAttract |
| **xpAvoid** | уводит в сторону, либо замораживает / убивает | Detection Distance + Variation, Object Shell 1, On Detection Change Direction | Для сплайнов берётся Default Thickness; слишком малая дистанция = промахи. → nxAvoid |
| **xpCover** | прилипание к поверхности / заполнение объёма, следование за анимацией | Velocity/Force; Cover/Fill или Target; Operation All Polygons, Polygon Center, Nearest Surface Point, Visible Polygons, Vertices, Volume, Texture; Max Hit Attempts 20; Braking | В режиме Target частицы никогда не прилипают; Align to Normal требует Use Rotation. → nxCover |
| **xpDirection** | задаёт направление | Operation Absolute (по умолчанию) / Relative (непрерывно) / Spray / Circular (Y+ эмиттера) / Jitter / Ring / Use Modifier Rotation; Heading, Pitch; Use Strength | → nxDirection |
| **xpDrag** | сопротивление среды | Density Air / Custom; Drag Coefficient Sphere / Custom; Strength Multiplier | Зависит от скорости, радиуса, массы. → nxDrag |
| **xpExplode** | взрыв наружу | Timing Always On / время сцены / возраст частицы; Equals срабатывает один раз; от Mass Center; Unstick if Necessary | → nxExplode |
| **xpFollowPath** | проход через упорядоченный список замкнутых сплайнов (колец) | Get AOT From Modifier/Tag, Use Min Distance, Speed Mode | Пути должны быть замкнутыми, плоскими, с осью по центру. |
| **xpFollowSpline** | движение вдоль сплайна / xpTrail | Starting Mode Nearest Point…; At End Do Nothing / Loop / Repeat / Reverse; Speed Mode Initial / Current / **Complete Length in Time** / Set Speed; Turbulence на offset/velocity; Offset Blend 50%; Activate Range | Не может следовать по trail собственного эмиттера; нумерация вершин с 0. → nxFollowGeo (spline) |
| **xpFollowSurface** | течение по поверхностям | Pull, Offset (+ радиус частицы), Distance, Friction, Accurate | → nxFollowGeo (surface) |
| **xpGravity** | гравитация | Standard (−Y) или **Newton** (орбиты вокруг объектов-аттракторов; Attractor Mass 0 = нет, Axis Mask, Kill Distance) | Отрицательное значение = вверх. → nxGravity |
| **xpLimit** | ограничение позиции/скорости и т. п. | Limit Positions, Axis Limit % (100% фиксирует ось), ограничение по оси ±, Parameter to Limit Speed | → nxLimit |
| **xpNetwork** | пути с поворотами на 90° по сетке (вид схемы/печатной платы) | Operation Standard / Inside Volume; Change Mode Time; Change Angle 90° | Constrain Axis — только если модификатор последний; Inside Volume требует один замкнутый объект вокруг эмиттера. Использовать вместе с xpTrail. |
| **xpPushApart** | расталкивание | Absolute / Particle Radius, Distance, Strength, Iterations 5, Only Same Group | → nxPush (намного быстрее) |
| **xpRotator** | вращает весь поток вокруг оси | Velocity (по умолчанию) / Force (+ Attraction); Rotate Speed °/s; Escape Velocity | → nxRotate |
| **xpSoundDisplacement** | смещение вдоль оси по .WAV | Start Offset, Use Samples, Scale Down, Sensitivity, Return to Zero | Только WAV. |
| **xpSpeed** | меняет скорость | Incremental (за кадр!), Use Spline (Speed Max 300), Exponential | → nxSpeed |
| **xpSpin** | вращение каждой частицы (spin/rotate) | Spin (нужен Use Rotation) / Rotate; Per Frame/Second; Increment ≤45° (лучше 0.1–0.3) | Перебивает spin эмиттера. → nxSpin |
| **xpSplineFlow** | свободное, похожее на жидкость течение вдоль сплайна через хэндлы | множители Towards / Along / Rotate / Controls / Attraction (100%), настройки для каждого хэндла; 5 хэндлов автоматически | Высокий Attraction стопорит поток → поднять Along. |
| **xpSticky** | прилипание к (анимированным) объектам | Probability, Range, Tolerance (низкий), Outside Only, Sticky Time/Falloff | Не для сплайнов. → nxSticky |
| **xpStrangeAttractors** | хаотичные траектории математических аттракторов | Lorenz (по умолчанию), Rössler, Chen, Chua, Duffing, Aizawa, Rikitake; тип Velocity; Max Speed 1500; Iterations 100; Use Preset Values | С типом Force классическая форма теряется. В связке с xpTrail даёт линии «странного аттрактора». |
| **xpVortex** | закрутка-торнадо | Velocity / Force / **Helix**; Invert Rotation; ось от Object или по Z эмиттера | Helix — в самом низу стека, blend ≥80%. |
| **xpWind** | снос ветром | Strength, Turbulence (порывы), Frequency, Scale | → nxWind (порывы Von Karman) |
| **xpSpawn** *(группа Generate)* | порождает новые частицы из исходных | нужен **Spawning Emitter** (2-й эмиттер — становится Controlled Only); Position Source Particle; Direction Random; Spawn Number в секунду; Min/Max Interval | Наследование вращения требует Use Rotation на spawn-эмиттере (не Tangential/Face). На GPU — действие Spawn в nxQuestion или nxSpawn в Blender. |
