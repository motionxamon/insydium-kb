# X-Particles — утилиты, Actions, группы, рендер

Источник: docs.insydium.ltd/x-particles/{utilities,x-particles-render-settings-materials-shaders-a}/* (Fused 2025, проверено 2026-11-03). Пересказ.

## Утилиты
- **xpGroup** — группы частиц, на которые нацеливаются модификаторы/actions. Уникальный Group Number; Mode Standard / Display Only / **Extended** (mass, friction и т. п. только здесь). Эмиттер должен содержать её в **Groups to Use**. Размер сферы/круга частицы всё равно берётся из эмиттера.
- **xpAction** — что происходит, когда срабатывает Question (или коллизия). Типы: Object (Change Emitter / Generator / Trails), Control Modifier (переключение модификаторов), Direct (Change Geometry, Change Group), Dynamics (Sheeter), Other (Output to Console, Stop Following Spline, Unlink TP, Unstick from Source); Change Editor Display. Actions, созданные из меню, не привязываются к Question автоматически.
- **xpDeformer** — вершины меша следуют за частицами (дочерний к мешу; эмиттер в Points + One Particle Per Source Element, Emit All Frames выключен). Применение: превратить любой меш в деформацию от частиц (плавление, сдувание турбулентностью).
- **xpTrailDeformer** — колыхание/течение сплайнов xpTrail по формулам для каждой оси (`u` вдоль длины, градусы), Amplitude, Wavelength, смещение шейдером (Mix по умолчанию 0%!). Тема Top Tip #1 (естественно текущие трейлы).
- **xpSplineGrowth** — рост/сжатие сплайнов/трейлов (дочерний к сплайну): Point-by-Point / Whole / Section, Invert, случайная Min Length. Применение: анимированная прорисовка линий.
- **xpVertexMap** — анимированные vertex maps из слоёв seeds/particles/shaders/speed/curvature/occlusion (карты роста для MeshTools/Taiao/шейдеров). Без иерархий.
- **xpVolumeEmit** — запускает/останавливает эмиттер, когда он (или объект) внутри/снаружи замкнутых объёмов.
- **xpCirclePacker** — заполняет пространство непересекающимися кругами/сферами (Min/Max Radius, Separation). Поднимите Birthrate (отклонённые частицы удаляются).
- **xpJoin** — объединяет объекты в один источник/коллайдер (только одного типа). Используйте с клонерами/множеством объектов (например, попадания xpRainRig).
- **xpMetaGroup** — группа групп.
- **xpDataExporter / xpDataImporter** — экспорт/импорт снапшота в CSV (position, direction, color, rotation). **xpOpenVDBImporter** — загрузка VDB.
- **xpConsole** — консоль данных частиц/отладка.

## Рендер
- **X-Particles Material** (нативный, рендер Physical/Standard): рендерит частицы, сплайны и объёмы без геометрии. Цвет по Age/Speed и т. д., прозрачность, Size (Particle Radius / World / Screen), **Filling** (дополнительные частицы только в рендере), Volumetric. Назначьте на Group, чтобы рендерить только её. Сплайнам нужен связанный xpTrail. С GI ставьте Self Illumination > 0.
- **X-Particles Gaseous** — нативный шейдинг огня/дыма (voxel size, градиенты smoke/fire, Black Body).
- Эффект Render Settings (добавляется автоматически): blending, пороги теней, volume step (не больше самого маленького объёма), Best AA, мультипассы normals/position. High Q Render игнорирует Physical DOF.
- Шейдеры: **xpSampleShader** (окрашивает поверхности по данным ближайших частиц — speed/age/custom), **xpProximityShader** (оттенки серого по расстоянию до частиц — мокрые следы, свечение в месте контакта), xpDistanceShader, xpObjectShader (нужен для некоторых полигонов xpDisplayRender), xpSoundShader, xpSpriteShader, **xpWetMapShader** (с тегом xpWetMap), Noise/Particles/Shader Falloff.
- **Сторонние рендеры** (Redshift, Octane, Arnold, Cycles 4D/Cycles): в документации они не описаны. Общая практика (сверяйтесь с документацией своего рендера): частицы рендерить как геометрию через xpGenerator (instances/render instances) или мешеры (nxMesher / xpOpenVDBMesher); трейлы — через xpSplineMesher или hair/spline-объект рендера; дым/огонь — кэшировать xpExplosiaFX/nxExplosiaFX в **OpenVDB** в xpCache и загружать VDB в volume-объект рендера; данные частиц (color, velocity) — через vertex color / UV-теги, экспортируемые nxMesher, или ноды particle-data рендера.
- Пост-эффект X-Particles Render Info = вшитый водяной знак (кадр, число частиц, время).
