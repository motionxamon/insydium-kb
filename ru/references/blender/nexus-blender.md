# NeXus для Blender (2026.0 → 2026.1 Beta 3)

Источник: docs.insydium.ltd/blender/* (проверено 2026-11-03; последняя версия = 2026.1 Beta 3, 30 Oct 2026). Пересказ.
Большинство параметров объектов **совпадают с NeXus в C4D** — смотрите `../c4d/nexus-*.md` по nxConstraints, nxFluids (PBD/SPH/FLIP-APIC), nxExplosiaFX, nxMesher, nxFoam, nxSplash, nxWave, nxQuestion, Mapping, nxFalloff и всем nx-модификаторам. Здесь — только то, что специфично для Blender или появилось недавно.

## Установка и настройка
- Blender **4.3+**, лицензия INSYDIUM, онлайн-проверка при каждом запуске, access token. Ставится как **extension**: Preferences → Get Extensions → добавить репозиторий INSYDIUM (с access token) → установить NeXus → ввести лицензию в Add-ons.
- Добавление объектов: **Add ▸ INSYDIUM NeXus ▸ Presets / Generators / Dynamics / Modifiers / Warps** (разделено в 2026.1). Настройки находятся на вкладке **Properties ▸ Physics** (не в стеке модификаторов и не в Geometry Nodes).
- **NeXus Hierarchy** (N-панель ▸ NeXus): дерево всех объектов NeXus; **сверху вниз = порядок вычисления**; отступ = дочерний объект; папки отключаются целиком; удаление строки удаляет объекты. **nxSystem** (Beta 3) добавляет набор папок-пресетов.
- Вкладки **NeXus Panel**: Object Properties, Groups Affected, Mapping, Falloff. **Particle Console** показывает данные частиц вживую (фильтр по эмиттеру). Preferences: Compute Device, Precompile Shaders, VRAM.
- Единицы: в Blender **метры, Z вверх**; в C4D **см, Y вверх** (Blender Z+ = C4D Y+; 1 m = 100 cm). Blender скрывает неактуальные опции, C4D делает их серыми.

## Основные объекты (Blender)
- **nxEmitter** — Shape Rectangle/Disc/Sphere/Box/Object (меши, кривые, point cloud, домены nxFluids, Collection Instances, Gaussian splats в Blender 5.3+, системы частиц Blender); Emission Rate / Pulse (Interval = от старта до старта начиная с Beta 3) / Shot / **Liquid Fill** / **Liquid Flow**; Mode Random / Regular / Hexagonal; Speed 1.5 m/s, Radius 0.03 m, Mass 1, Lifespan 90; Motion Inheritance; **Stick to Source**; Initial State (нужен ≥1 просчитанный кадр); до 8 **Display Channels**; **Export ▸ Create Point Cloud** (нужно для рендера / ноды Particle Info) и Create Gaussian Splats. Match Solver Resolution перекрывает radius/spacing.
- **nxLiquid** (Presets) — в один клик Fill (стоячая вода, Fill Level 30%) или Flow (струя): эмиттер + nxFluids (по умолчанию FLIP) + mesher + foam (оба изначально выключены) + gravity под одним empty; общий ползунок Resolution.
- **nxCollider** — список Colliders (меши/кривые/collection instances); Normals Outside / Inside / Any / Outside-Fill Hollows; Bounce 40%, Friction 1%, **Adhesion**, Attraction/Repulsion; **Global включён по умолчанию** (первый коллайдер управляет всеми). FLIP/APIC: Any работает как Outside; Scatter игнорируется в FLIP/APIC/MPM.
- **nxGenerator** — инстансит меши на частицы; Display Preview (только во viewport) или **Geometry** (нужно для рендера/коллизий); слои с Bias (режим Random), Mode random/sequence/index; родной **motion blur** в Cycles/EEVEE.
- **nxTrail** — Lines (превью) или **Splines** (настоящие объекты-кривые → Curve to Mesh/geometry nodes); Length по времени или расстоянию; Connections.
- **nxCache** — Build: Record, Format NeXus / **Alembic (single file)** / **PLY** / OpenVDB для EFX, Directory, Auto Frame Range, **Disk Reserve** 1024 MB; Playback: Local Coords, Retiming Disabled (Offset, Time Scale) / Frame / Time / Custom spline. Empty Cache удаляет всё.
- **nxGroup** — группы (+ цвет градиентом/noise в Beta 3; режимы Shader/Object Color убраны).
- **Интеграция с нодами** — редактор Shader/Geometry: **Add ▸ NeXus ▸ Particle Info** (Color, Speed, Age, Life, Rotation, Scale, Radius, ID…). Эмиттеру нужны Create Point Cloud + каналы в Transfer Properties. Сырые атрибуты `nx_color` и т. д. (`position`, `radius` без префикса). ID — float в шейдерах, int в GN.

## Новое в 2026.1 Beta (сначала в Blender, почти всё есть и в бете C4D)
- **nxMPM** — мультиматериальный солвер Material Point Method: Liquid, Elastic (желе), Snow, Sand, Brittle (бетон/стекло/камень — трескается), Metal (гнётся → рвётся), Foam. Домен-бокс (Resolution/Voxel Size, стенки Closed/Open/Kill, Use Bounds выкл. = сетка следует за частицами), солвер MPM или CK-MPM (более чёткие контакты, тяжёлый; принудительно включается пресетами concrete/glass/rock/ice/steel). Density, Viscosity, Stiffness (E), Poisson Ratio, CFL, substeps, Auto Sleep, разрушение (Fragment Size, Strength, Toughness — только MPM). **Mixer**: смешивание материалов по Speed/Age/Height/Damage. Прочность снега — в Pa.
- **nxMaterial** (Presets) — настройка MPM в один клик (эмиттер + nxMPM + mesher + gravity).
- **nxDeformer** — меш/кривая следует за частицами (в паре с nxMPM): Bind Radius 0.2 m; Deform Mode Breaking → рвётся по Tear Damage 0.9 / Tear Stretch 50%.
- **nxPin** — фиксирует выбранные частицы. **nxBind** — держит частицы на деформируемом меше/коллекции и отпускает по условиям (Stay Released вкл.).
- **nxBioLogic** — органический рост: reaction-diffusion (Feed/Kill), кораллы, differential growth, Physarum (слизевик), particle-life ×2; вкладка Meshing строит трубки; Stop Frame 0 = рост не останавливается.
- **nxDendrite** — ветви / сети / решётка Бете / рост кристаллов-дендритов из частиц (слоями, Spawn, изгиб Curl).
- **nxOcean** — GPU-океан (спектр Phillips / Pierson-Moskowitz / JONSWAP, Wind Speed/Direction, Choppiness, Patch Size > 0.64·wind² m), пена на гребнях, брызги через nxEmitter, **береговая линия**: обрушение/накат/песчаный пляж, отражение волн от коллайдеров (Wave Masking по умолчанию 0), **связка с FLIP** (подключить океан в домене nxFluids; nxMesher Blend into Ocean). Geometry On Render по умолчанию.
- **nxWarp** — 19 cage-варпов (Bend, Bulge, Cast, FFD, Flatten, Helix, Melt, Noise, Path, S Bend, Scroll, Shear, Spherify, Squash&Stretch, Taper, Twist, Wave, Wind, Wrap); режимы Deform / Guide / **Flow**; Reach/Extent (в Beta 3 Flow Reach по умолчанию 0% — 300% = поведение Beta 2).
- **nxShatter** — разрушение Voronoi/Glass/Wood/Bricks, Solid (замкнутый меш) / Surface, Gap, слои SubFracture, триггеры Frame/Collision, Driven By nxEmitter или nxMPM (Build Shatter по трещинам MPM).
- **nxSpawn** — дочерние частицы: триггер Instant / At Age / On Collision / On Death; Rate / Burst / Pulse; до 8 подслоёв (фейерверки).
- **nxFluid2D** — 2D-жидкость с красителем в реальном времени в UV-развёртке меша → текстура / vertex group (нужны UV).
- **nxScatter** (Presets) — точки по поверхности мешей. **nxFalloff Modifier** (переформирует/размывает falloff; новые режимы Wet, Curvature, AO). **Vertex Maps** — запись falloff в атрибуты/vertex groups.
- Дополнения **nxQuestion**: флаги Asleep/Bound, действия Sleep/Bind; слой **Quill** (Blender). **Mapping**: один слой → несколько назначений. Слой **nxSpeed** теперь Acceleration (экспоненциальный). В **nxGenerator** "Spawn" переименован в Bias.
- **Импорт/экспорт сцен C4D ↔ Blender** (Beta 3, на стороне Blender): меши+UV, кривые (первый сплайн), камеры, свет, настройки и градиенты NeXus, материалы (Cycles 4D → shader nodes); не переносятся ключи анимации, материалы по полигонам, многослойные списки, bezier-ручки.

## История версий (кратко)
- 2026.0.0 (13 Jul 2026) первый релиз для Blender · 2026.0.1 (16 Jul) счётчики в HUD, motion blur для nxGenerator · 2026.1 Beta 1 (1 Oct) NeXus в бете C4D + nxMPM и др. · Beta 2 (7 Oct) nxOcean, nxShatter, nxWarp; **силы PBD больше не зависят от размера частиц** (старые сцены выглядят иначе) · Beta 3 (30 Oct) nxSpawn, nxFluid2D, nxScatter, nxSystem, кэш Alembic/PLY, обмен с C4D.
