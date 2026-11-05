# X-Particles — xpSystem, xpCache, Project Settings, Questions/Actions, Data Mapping, QuickTools, xpPainter

Источник: docs.insydium.ltd/x-particles/* (Fused 2025, проверено 2026-11-03). Пересказ.

## xpSystem
- Создаётся из меню INSYDIUM; строит папки: **Emitters, Generators, Dynamics, Utilities, Modifiers (Control / Motion / Sprites / Generate), Actions**. Можно делать подпапки. По умолчанию добавляется эмиттер (отключается в INSYDIUM Preferences).
- Вкладка Object: Auto-Disable XP Objects, цвет иконки (чтобы различать системы), **Only Modifiers in Same System**, **Only Deformers in Same System**. Без них при нескольких системах каждый модификатор действует на все частицы.
- Слот Cloth Object (Create Cloth из меню Dynamics собирает setup).
- Global Transform: список эмиттеров, чьи уже выпущенные частицы должны двигаться вместе с системой.
- Trails ведут себя по-разному внутри и вне системы эмиттера.

## xpCache (кладите внутрь xpSystem)
- Иконка: зелёная = кэша нет, жёлтая = собран, но выключен, **красная = используется**.
- Cache Type: **External (Files)** по умолчанию (по файлу на кадр, безопасно для сетевого рендера) или Internal (Memory) (только для коротких тестов — раздувает .c4d). Particle Format; Scale (только для external, чтобы совпадать с другими программами); xpExplosiaFX → X-Particles или **OpenVDB** (переименование каналов). Folder / Alt Folder / Use Folders.
- Record: режим Sync (кнопка) или Playback; Auto Time или Start/Stop; Record Data All / Basic (только velocity!) / Custom. Замочек на объектах защищает от перекэширования (но не от Empty cache). Compress Cache on Build.
- Playback: Hold (замирание на последнем кадре, иначе симуляция продолжается вживую), Wrap (зацикливание), Local Coords, **Retiming** Disabled (Offset + Scale %, например 200% = скорость ×2) / Frame / Time / Custom spline (спид-рампы!). Custom Play.
- Вкладка Inclusion: какие типы объектов кэшировать; include/exclude для EFX.
- Workflow: задать диапазон → Build Cache → проверить красную иконку → проскрабить → ретайм.
- Совет для спид-рампов: закэшировать, затем Retiming → Custom spline (меши из xpOpenVDBMesher/nxMesher следуют за закэшированными частицами).

## Project Settings (Ctrl/Cmd+D → X-Particles)
- **Subframe Steps** — более мелкие шаги для коллизий, жидкостей, констрейнтов; меняет результат (повышайте постепенно). Также влияет на вязкость PBD/nx.
- **Collisions** (максимум на частицу за шаг), **Iterations** (жёсткость констрейнтов и PBD-жидкостей), **Accuracy** (ранний выход).
- Bullet: Max Steps, Gravity, World Density, Collision Algorithm GImpact (по умолчанию) / Triangle, Random Seed, **Scene Size** (под размер ваших объектов), отображение точек контакта.

## Классическая система управления: xpQuestion + xpAction (CPU)
- Вопросы добавляются во вкладке **Questions** эмиттера (один вопрос можно использовать в нескольких эмиттерах). Если частица проходит проверку → запускаются указанные **Actions** или переключаются модификаторы через **Modifiers to Activate / Deactivate** (Action не нужен).
- Категории: Particle Data (age, speed, radius…), Position, Flags (события вроде hit/collided), Fluid Data, Geometry, Physical Data (temperature, mass, bounce), Other.
- Под-вопросы комбинируются через AND / OR (создаются через Create Sub-Question; не могут содержать actions). При копировании под-вопросов связи теряются.
- Подвох: возраст частицы ≠ кадр сцены.
- Для NeXus/GPU-эмиттеров используйте **nxQuestion** (см. nexus-dynamics-logic.md).

## Data Mapping (вкладка Mapping у CPU-модификаторов)
- Слои: Parameter → Map to (~30 источников: Age, Speed, Distance Traveled, Lifespan, Radius, Scale, Mass, Temperature, Fluid Density, Custom Data, специфичные для модификатора, например Segment Length у xpFollowSpline) → Range Min/Max → кривая (Y умножает параметр). Remove удаляет без предупреждения.

## xpQuickTools (меню → докируемое окно) — самый быстрый старт
- Particle FX: Emit From Object/Selection/Texture/Vertex Map, пресеты Curl Noise, Dust, Fireworks, Simple Rain, Simple Snow.
- Fluids & Grains: Condensation, Fluid Filaments, Fluid FX Water Body.
- Smoke/Fire: EFX Basic Flame, Basic Smoke, Camp Fire, Fire From Particles (+ дым для Cycles 4D).
- Trails: Create Branches, Nearest By Distance, Network Trails, Tendrils.
- Workflow: Create Cloth, System Sort, **Quick Cache** (Shift = internal), **Assign Groups to Modifiers**.
- Большинству нужен выделенный объект (некоторые подставляют Figure/Sphere/Torus).

## xpPainter
- Рисование частиц по геометрии (не на кадре 0). Режимы Create / Delete / Paint Life, Color, Speed, Radius, Rotation; Ctrl инвертирует. Brush Radius, Strength, Spacing, **Check Overlaps** (равномерное покрытие), Count, Offset, Life 90 F, Radius 5 cm, Direction, Rotation Mode, нажим пера. Если эмиттер не привязан, создаёт Spawn-Only эмиттер.
