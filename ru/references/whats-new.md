# Что нового — хронология релизов INSYDIUM (сначала новые)

Сверено 2026-11-03 с новостями insydium.ltd и docs.insydium.ltd. **По умолчанию предлагайте самый новый инструмент, который решает задачу**, а старый/CPU-путь давайте как запасной. По этому файлу можно датировать туториал: если в Top Tip показан какой-то объект, ролик не может быть старше релиза, в котором этот объект появился.

## Анонсировано: следующая бета NeXus (тизер 3 Nov 2026 в финальном Top Tip Tuesday, #196)
- В GPU-движок придёт **единая динамика**: **ткань**, **верёвки / шнуры**, **твёрдые тела**, **разрывы + растрёпывание** и **двусторонняя связь с EFX** (дым/огонь толкают объекты и сами от них отталкиваются).
- На Nov 2026 ещё не вышло — пока не появится, используйте nxConstraints (в духе ткани/soft body), теги C4D Rigid Body на геометрии xpGenerator (см. рецепт 2025-08-26) или CPU xpCloth.
- Этим выпуском серия Top Tip Tuesday завершилась (выходила еженедельно с Feb 2023).

## NeXus 2026.1 Beta (1 Oct 2026; Beta 2 — 7 Oct; Beta 3 — 30 Oct) — Cinema 4D + Blender, один движок
- **Единая GPU-система ("Theron", Vulkan + собственное вычислительное ядро):** одинаковые солверы/модификаторы/результаты в C4D и Blender; новые функции выходят сразу в обоих. NVIDIA/AMD/Intel на Windows и Linux (Vulkan 1.3), Apple Metal 3 (macOS 13+). ≥4 GB VRAM.
- **Хосты:** C4D R19+ (Win/mac; связка с нативными частицами/Pyro требует **C4D 2025.3+**), Blender 4.3+, включая 4.5 LTS и 5.x (Win/mac/Linux, Windows ARM64).
- **Лицензия:** лицензия NeXus работает в обоих хостах (владельцы Blender-версии получают C4D бесплатно); бессрочная + 12 месяцев обновлений; владельцам Fused/X-Particles −50%. **Бета бесплатна для любой лицензии INSYDIUM** (или можно запросить бесплатную бета-лицензию); в C4D любая лицензия INSYDIUM открывает полный Fused + бету NeXus на время беты.
- **Новые солверы/объекты:**
  - **nxMPM** — мультиматериал: жидкость, упругие тела, снег, песок, хрупкие материалы, металл, пена; 2 режима солвера (MPM / CK-MPM), оценка памяти сетки, открываемые стенки, поддержка коллайдеров, **смена материала по возрасту/скорости/растяжению/повреждению** (Mixer), разрушение, auto-sleep. **nxMaterial** = настройка MPM в один клик (пресеты: Snow packed/sticky, Sand wet, Glass bottle, Metal steel…). Разреженный солвер (домен необязателен), переопределение материала для каждого эмиттера (Sand Powder Fine, Sand Dry, Brittle Concrete, Elastic Rubber, Liquid Water…; Momentum 0 для сухих), Auto Sleep (Sleep Speed 5 cm/s, Wake Speed/Spread), окраска по Material или Sleep State. Tech preview 16 Sep 2026, тренинги 7 и 11 Oct 2026.
  - **nxDeformer** — меш следует за частицами, **разрывы** + ремешинг (Blender: subdivision и деформация по кривой).
  - **nxPin** — закрепление частиц (выбор по Falloff/Groups, списку ID, данным частиц, объекту; In Place или To Object) → ткань/верёвка с nxConstraints, твёрдые тела с nxMPM.
  - **nxBind** — удерживает частицы внутри деформируемого объёма и отпускает по возрасту/жизни/скорости/температуре; вкладка Break: Falloff (по умолчанию) / Age range / Color Brightness, Chunks + Chunk Size, Soften (выключается, когда управление забирает солвер). Тренинг 21 Oct 2026 (рассыпающийся персонаж → nxMPM).
  - **nxBioLogic** — реакция-диффузия, дифференциальный рост, Physarum, particle life, кораллы, primordial; трубчатые меши.
  - **nxOcean** — GPU-океан: ветер/спектр (Phillips, Pierson-Moskowitz, JONSWAP), пена, брызги, кильватерные следы, береговые линии, **пляжи с накатом/прибоем** (Beta 3), плавающие объекты, отражение волн от коллайдеров, **связка с FLIP**.
  - **nxShatter** — GPU-разрушение (Voronoi, Glass, Wood, Bricks; вложенное дробление; триггеры; управление эмиттером или повреждениями MPM).
  - **nxWarp** — 19 варпов-клеток для частиц, мешей **и дыма** (Helix, Path, Wind gust wave, Melt, Noise, FFD, Scroll, Bend, Twist…); режимы Deform / Guide / Flow. Общие Twist/Taper/Bulge + Fit to Parent; Guide Strength (низкое значение = частицы вырываются); профили Flow Square/Circle/Star/Custom, выход только через торцевую грань; варпы складываются в стек (границы нижестоящего должны охватывать выход вышестоящего). Тренинг 30 Oct 2026.
  - **nxSpawn** (Beta 3) — дочерние частицы (Instant / At Age / On Collision / On Death; Rate/Burst/Pulse; 8 подслоёв).
  - **nxFluid2D** (Beta 3) — 2D-жидкость в реальном времени в UV-карте. **nxScatter** (Beta 3) — точки на мешах → nxGenerator.
  - **nxSystem** — пресетная структура папок (объект в C4D; в Blender — "Pipeline Manager" / Hierarchy).
- **Управление:** 16 режимов nxFalloff (Box, Linear, Sphere, Noise + Cylinder, Torus, Box Frame, Capsule, Cone, Object, Points, Spline, Attribute + Curvature, AO, **Wet**); у каждого слоя модификатора свой список Falloff; слои **nxFalloff Modifier**: Invert, Clamp, Remap, Step, Quantize, Curve, Cycle, Blur, память (Freeze, Decay, Delay, Grow); слой **Cyclic** (nxColor, nxFlowField); Mapping: один слой → много целей.
- **Жидкости:** FLIP/APIC **неньютоновские** (Flow Index, Yield Stress), **Wall Friction**, перекраска по Density/Viscosity, Mixer по эмиттерам/группам (плотность, вязкость, flow index, yield stress, поверхностное натяжение), связка с океаном. Значения по умолчанию (Blender): voxel 0.1 m, FLIP fraction 95%, CFL 0.7.
- **nxCollider:** адгезия, притяжение, отталкивание, настройки с привязкой к поверхности, collection instances, Fill Hollows. **nxMesher:** UV-адвекция, сглаживание Detail Aware, источник nxGroups, проекция UV с камеры, Blend into Ocean. **nxCache:** диапазон кадров, Disk Reserve, **Alembic одним файлом, PLY**, Local Coords. **nxEmitter:** Initial State + Keep Stored Age, до 8 каналов отображения, Match Solver Resolution, Stick to Source, эмиссия из point cloud / **Gaussian splats** / систем частиц Blender.
- **Workflow:** новый общий рендерер viewport (лучше отрисовка вокселей для FLIP/EFX/FlowField); меню Add разделено на Presets / Generators / Dynamics / Modifiers / Warps; справка у каждого параметра; выбор GPU; предкомпиляция шейдеров.
- **Только C4D:** связка с нативными **частицами и Pyro C4D** (превью-видео 9 Oct 2026) (модификаторы NeXus управляют нативными частицами; обмен дымом/огнём nxExplosiaFX ↔ Pyro), NeXus Project Settings (HUD / Document: substeps, GPU, Rewind on Load), **nxFalloffMap** (falloff → теги vertex map / vertex color), **nxConvert** (xpEmitter и группы → NeXus одним undo), модификаторы NeXus на обычных xpEmitter, дефолтный дымовой материал Redshift для VDB из nxExplosiaFX, nxShatter Make Editable → null с кусками, освобождение памяти GPU перед рендером.
- **Только Blender:** нода Particle Info (shader/GN), Collection Instances, falloff по vertex map, окно GLSL Script, **Quill** (ИИ, который собирает сетапы nxQuestion по описанию обычным языком — подключается облачная модель через API-токен или локальная Ollama/CLI; результат считайте черновиком), **импорт/экспорт сцен C4D**.
- **Ломающие изменения в бете:** сила PBD больше не зависит от размера частиц (Beta 2); Pulse Interval считается от старта до старта, nxWarp Flow Reach 0% (300% = старое поведение), слой nxSpeed = Acceleration, nxGenerator Spawn → Bias, nxCache Auto → Auto Frame Range, FLIP и MPM учитывают фильтры групп коллайдеров (Beta 3).

## NeXus for Blender 2026.0 (13 Jul 2026; 2026.0.1 — 16 Jul)
- Перед ним вышла публичная **бета для Blender (1 Jun 2026)** и серия видео Official Training / Quick Guide (Jun–Jul 2026); короткие превью инструментов — Apr–May 2026.
- Особенности Blender из тренингов: **Export ▸ Create Point Cloud** (автоматические Geometry Nodes + материал Particle Info; частицы во viewport не рендерятся), пресет **Liquid Fill** + тип эмиссии, **nxSheeter** (заполняет дыры в истончающихся FLIP-плёнках), nxExplosiaFX **VDB Output: Live** → Blender Volume + пресетный материал огня, nxMesher Transfer Velocity для motion blur в Cycles/Eevee, Particle Console, Render ▸ Lock Interface.
- Первый релиз для Blender: полный набор NeXus (жидкости PBD/SPH/FLIP/APIC, nxFoam, nxExplosiaFX, nxInfectio, nxDendrite, constraints, flocking, P-P-коллизии, эмиттеры, nxGenerator, nxMesher, nxTrail, nxUpres, все силы, nxQuestion + **Quill AI**). Установка как extension, 21-дневный триал, бессрочная лицензия + 12 месяцев.
- 2026.0.1: счётчики в HUD по эмиттерам, motion blur для nxGenerator, фильтр эмиттеров в консоли.

## Fused 2025.4.1 (25 Feb 2026) — сервисное обновление
- Окраска FLIP/APIC по числу частиц на воксель (диагностика плотности), улучшенная адвекция у границ домена, более быстрые рей-марчеры EFX на DirectX 12 / Metal; режимы воспроизведения Jidou (stop/loop/ping-pong/continue) для jdFlowCam и jdGeoFlow; mtEdgeSpline работает с n-gon; резервные серверы лицензий; исправлен краш xpBranch в **C4D 2026**. Сборки: NeXus 514, X-Particles 1875.

## Fused 2025.4 (8 Dec 2025) — большой GPU-релиз для C4D
- **Переписанное GPU-ядро NeXus** (быстрее, меньше VRAM); слоёные GPU-falloff; Data Mapping с зацикливанием.
- **nxExplosiaFX (новый, GPU-дым/огонь)** — эмиссия из объектов, сплайнов, vertex map, шейдеров, частиц; слоёные эмиттеры, коллизии, силы; объёмный GPU-viewport.
- **nxFluids FLIP и APIC (новые)** — переменная вязкость, жидкие плёнки, усики от поверхностного натяжения.
- **nxMesher (новый, GPU)** без мерцания, слоёное сглаживание, выводит цвет/скорость/ID эмиттеров. **nxFoam** переписан (слои: пена, пузыри, брызги). **nxSplash (новый)** — брызги-короны.
- Слоёные модификаторы (стек как в Photoshop: Strength, Normal/Multiply/Add/Max, свой GPU-falloff и mapping на каждый слой): nxTurbulence, nxScale, nxLimit, nxSpeed, nxColor, nxSpin, **nxDirection** (существовал с начала 2024 как простой толчок по +Z; в 2025.4 стал слоёным с Direction Force / twist / attract). nxFollowGeo: несколько сплайнов + режимы Guide/Force. nxQuestion: вариация + улучшенный поиск соседей.
- **Jidou (новый набор):** jdAniMate, jdDriver, jdFlowCam, jdGeoFlow, jdGeoRoll.
- Публичные превью до релиза: Modifier Improvements 1–3 (Jul–Aug 2025), Core Improvements (11 Sep 2025: ~20 % быстрее, без паузы на компиляцию шейдеров при первом воспроизведении), NeXus ExplosiaFX (16 Oct 2025), Final (26 Nov 2025), Jidou (8 Dec 2025).
→ Любой совет с **nxExplosiaFX, nxFluids FLIP/APIC, nxMesher, nxSplash, слоёным nxDirection или Jidou датируется Dec 2025 или позже** (либо превью лета–осени 2025). Более старые советы по дыму/огню/FLIP используют CPU xpExplosiaFX / xpFluidFLIP / xpOpenVDBMesher.

## Fused 2024.x
- **2024.4** (10 Feb 2025) — только стабильность (исправления cache, Bullet, импорта VDB).
- **2024.3** (10 Sep 2024) — **совместимость с C4D 2025**; анимируемые слои xpFlowField; разные исправления NeXus.
- **2024.2** (9 May 2024) — **Fused Create** (покупка отдельных компонентов) / Complete; NeXus: более быстрое ядро, **коллизии с анимированной геометрией**, новые **nxColor, nxCover, nxFollowGeo, nxSticky**; Taiao: scatter по точкам роста, жилкование toLeaf + пресеты; TerraformFX: **Advanced Terrain Shader**, канал кривизны, **tfDistribute**, новый генератор шума; MeshTools: **mtPolyFold**, **mtPointProject**.

## Fused 2023.x
- **2023.3** (5 Jul 2023) — NeXus: GPU-версии популярных модификаторов XP, **переработанный nxQuestion (иерархия объектов + код)**, **Data Mapping**, новые **nxFlock, nxInfectio, nxWave, nxUpres, nxAvoid**; переработка Taiao (анимация роста, силы); MeshTools: **mtRayline**, **mtSplineFX**; инструменты анимации ландшафта в TerraformFX; улучшения кэширования X-Particles.
- Совместимость с C4D 2024: 2023.3.1 (28 Sep 2023).

## Раньше
- **NeXus представлен в Sept 2022** (GPU-солверы внутри X-Particles; nxPush, nxBlend, nxConstraints, nxFluids PBD/SPH, nxTurbulence…).
- Серия Top Tip Tuesday стартовала в **Feb 2023** (выпуск про xpTrailDeformer); **194 выпуска** к финальному 3 Nov 2026 (рецепты по каждому видео — в `recipes/`).
- X-Particles 4 (2017): xpFluidFX, xpExplosiaFX, xpClothFX, Bullet.

## Шпаргалка «как сейчас» (что предлагать первым в Nov 2026)
| Эффект | Новейшее (бета 2026.1) | Стабильный C4D (Fused 2025.4.x) | Legacy CPU |
|---|---|---|---|
| Жидкости | nxFluids FLIP + Mixer, неньютоновские, wall friction; пресет nxLiquid (Blender) | nxFluids FLIP/APIC + nxMesher | xpFluidFLIP / xpFluidFX |
| Океан | nxOcean (пляж, связка с FLIP) | nxWave во FLIP | xpOcean |
| Дым/огонь | nxExplosiaFX + nxWarp по дыму; связка с Pyro (C4D 2025.3+) | nxExplosiaFX | xpExplosiaFX |
| Снег/песок/желе/металл/стекло | **nxMPM / nxMaterial** | nxFluids SPH Granular, nxConstraints | xpFluidFX granular, пластичность xpCloth, Bullet |
| Разрушения | nxShatter (+повреждения MPM) | xpShatter + Bullet | xpShatter |
| Ткань/верёвки | nxConstraints + nxPin; разрывы nxDeformer | xpClothFX | xpClothFX |
| Рост/органика | nxBioLogic, nxDendrite | nxDendrite (Blender) / xpBranch | xpCellAuto, xpBranch |
| Спавн | nxSpawn | действие Spawn в nxQuestion | xpSpawn/xpMultiSpawn |
| Формирование потоков | nxWarp (Path, Helix, Flow) | nxFollowGeo, nxDirection | xpFollowSpline, xpVortex |
| Логика | nxQuestion + Quill (Blender) | nxQuestion | xpQuestion/xpAction |
| Falloff | 16 режимов nxFalloff + nxFalloff Modifier, Wet/AO/Curvature | nxFalloff | C4D Fields |
