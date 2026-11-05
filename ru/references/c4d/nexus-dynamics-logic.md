# NeXus (C4D) — остальная динамика, логика nxQuestion, Mapping, nxFalloff, Preferences

Источник: docs.insydium.ltd/nexus/ (Fused 2025, проверено 2026-11-03). Пересказ.

## Слои nxConstraints (продолжение; глобальные настройки — в nexus-core.md)
- **Custom connections** — как Distance, но с раздельной жёсткостью **Compression** и **Expansion**, у каждой свои Break, Rate, Falloff (Cubic), порог **Plastic** → связи сохраняют деформированную длину. Применение: металл/глина, которые гнутся и остаются согнутыми, вмятины. Expansion Break 0 = связи никогда не рвутся. Большой Connection Limit = медленно.
- **Friction** — сила Friction, Connection Limit, Radius, **Static** (% от Radius с полной жёсткостью → частицы цепляются и складываются в стопки), **Kinetic** (жёсткость при скольжении), Falloff (Cubic). Применение: кучи, складывание как у песка вместе с PBD.
- **Surface Tension** — Radius (больше = крупнее капли), Inner (не даёт схлопнуться), Tension, Falloff (Linear). Лучше всего с nxFluids PBD. При сильном натяжении поднимайте Iterations.
- **Viscosity** — Connection Limit, Radius, Stiffness. Для мёда умеренный Stiffness (<100%) + больше Iterations стабильнее, чем 100% жёсткости.

## nxFoam (пена из жидкости)
- Слои: **Surface Foam / Bubbles / Spray** (сколько угодно). У каждого слоя Spawn (Rate, Radius, Threshold, глубина Spawn Above/Below поверхности, After Age, Life, Velocity Scale, Radius) и рампы Detection (Kinetic Energy, Wave Curvature — главный драйвер для пены/брызг, Turbulence — главный для пузырей, окно Fluid Density).
- Можно назначить каждому слою отдельный xpEmitter (иначе используется эмиттер исходной жидкости) — так проще рендерить/мешить по отдельности.
- **Advection:** задайте Simulation Bounds = домен nxFluids (частицы за его пределами удаляются), Gravity = как у жидкости; Drag/Buoyancy/Rotation/Push для каждого типа; Type Transition Convert/Kill с Transition Time (убирает мерцание); **Erosion** пены.

## nxSplash
- Объект-конус с безье-хэндлами (Bottom/Top Radius → угол выброса, Height, Handle Num, Strength >100% допустимо), **Start Time + Duration** (подгоните под кадр удара), Distance (должна доставать до частиц жидкости, иначе ничего не произойдёт), кривые Falloff + Strength Falloff. Гравитация уменьшает фактическую высоту.

## nxWave
- Поле скоростей, которое прогоняет волны по жидкости. Box размера, **Speed** (cm/s, по умолчанию 100), Strength (высота волны), Noise Type, Scale X/Z (Z = длина волны, низкий X = хаос), Time Scale (0 = заморожено), Low/High Clip, Brightness (поднимает всё), Contrast (0 = плоско, отрицательный инвертирует). Display — только превью.

## nxQuestion (логика на GPU — замена цепочкам xpQuestion/xpAction для эмиттеров NeXus)
Список слоёв собирается через меню Add: **Question**, **Action**, **Folder**, **Loop**, **Variable**, **Script**. Вкладка Object: Iterations (весь список выполняется N раз за кадр), Weight (масштабирует изменения от Action, но не от Scripts).
- **Question:** цепочки If / Else If / Else (порядок важен: самый высокий порог ставьте первым). Категории:
  - Particle: Age, Color, Count, Traveled, Speed, Velocity, Position, Radius, Rotation, Mass, Life, Group, ID, **Neighbors**, Emitter, Flags (Hit Object, Hit Particle, Changed Group, Stuck, Frozen, Born), Smoke/Temperature/Fuel (из nxExplosiaFX), Fluid Density (нужен nxFluids), Field (нужно активное поле во вкладке Fields), UVW, Vertex Weight.
  - Document: Frame, Time, Camera Distance/FOV, Object Distance (Points/Position/Polygon/Volume).
  - Math: Value, Random, Spline (X = время), Variable, Wave.
  - Compare: <, ≤, =, ≠, ≥, >, Within/Not Within. **Check Once** = проверять только до первого срабатывания. Комбинируйте с дочерними вопросами: AND / AND NOT / OR / OR NOT; Action вешайте на последний.
- **Action:** Set, Add (накапливается каждый кадр!), Spawn (нужен собственный xpEmitter — кнопка Add Emitter; Count, Distance, Velocity Random/Source, Life, Inherit Parent), Kill, Break (выход из loop/script). Weight <100% = плавное изменение; **Delay + Damping** = пружинный ease (только Color, Mass, Radius, Speed); Set Once.
- **Variable:** Float / Integer / User Data (читает слайдер User Data на объекте nxQuestion — удобно, чтобы вынести контролы наружу). Доступна для записи; **Particle** = хранение на каждую частицу (расходует VRAM). Имена должны быть уникальными.
- **Script:** урезанный **GLSL**, выполняется на GPU параллельно для каждой частицы. Встроенное: `particle.{age,life,speed,color,position,velocity,radius,mass,born,random,...}`, `particles[n]` (только чтение), `index`, `doc.{time,delta,frame,fps}`, `emitter[n].create()` + `newparticle[n]` (n — обязательно литерал int), `math.random(seed)`, `print()` (оборачивайте в `if(index==0)`). `particle.neighbors()` / `particle.density` требуют nxFluids. `particle.smoke/temperature/fuel` можно использовать как свои накопители, если нет nxExplosiaFX. Функции/глобальные переменные объявляйте до использования; тестируйте на малом количестве частиц.

## Вкладка Mapping (у каждого nx-модификатора)
- Добавьте map-слой → выберите параметр → данные **Map to**: Age, Speed, Radius, Life, Mass, Distance, Color/R/G/B, Temperature, ID, Group, Vertex Weight, Shader.
- Range Min/Max (например, Age 0–60 F), Clamp Mode **Clamp** (по умолчанию) / Cycle / Continue, Weight, кривая (X = диапазон 0→1, Y = множитель).
- Классика: nxScale по Age (рост, затем уменьшение), пульсация волнистой кривой, турбулентность сильнее на высокой скорости.

## nxFalloff (GPU-объект falloff)
- Режимы Box / Linear (по умолчанию Y+) / Sphere / Noise (Simplex, Curl, Turbulence, Wavy Turbulence, Voronoise, FBM, Cubic). Invert, Weight, Scale, ремап сплайном, Blend Mode/Strength для наложения.
- Ничего не делает, пока его не перетащат в слот falloff модификатора; один nxFalloff может управлять многими модификаторами. У модификаторов также есть встроенные быстрые falloff (Box/Linear/Sphere/Noise) на каждый слой.
- Для эмиттеров NeXus предпочитайте nxFalloff, а не Fields из C4D (вкладка Fields есть, но nxFalloff — родной путь для GPU).

## Preferences
- GPU-устройство (multi-GPU), **VRAM**: Max (по умолчанию) / Balanced (оставляет место для Redshift/viewport) / Custom. Если рендер на той же видеокарте падает — переключите на Balanced.

## nxTurbulence (шаблон для большинства nx-модификаторов)
- Стек слоёв обрабатывается **снизу вверх**; у каждого слоя Blend (Normal, Add, Subtract, Multiply, Difference, Screen, Overlay, Min, Max) + Strength + свои falloff.
- Noise: Simplex (по умолчанию), Curl, Turbulence, Wavy Turbulence, VoroNoise, FBM, Cubic. **Curl Blend / Curl Add** = как curl-скорость смешивается со скоростью от других модификаторов (это ответ NeXus на наследование движения в xpTurbulence; высокий Curl Blend жёстко привязывает частицы к curl). Seed, Turbulence Strength, Offset, Scale (больше = плавнее), **Axis Direction Scale** (обнулите ось → плоская турбулентность), Persistence, Lacunarity (нет в Simplex), Frequency (скорость эволюции), Octaves (по умолчанию 1).
