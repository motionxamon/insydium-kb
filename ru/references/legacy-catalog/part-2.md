# Каталог старых видео — часть 2 (2020-06-18 – 2022-09-16)

## Maintenance Training — ExplosiaFX

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Settings - Buoyancy & Vorticity** — https://www.youtube.com/watch?v=M1unG8LWO_U
  - Что: buoyancy для каждого канала отдельно (смена знака переворачивает вертикальное движение heat/fuel/smoke), vorticity для мелких завихрений и turbulence для естественного случайного движения на источнике-торе.
  - Инструменты: xpExplosiaFX (вкладка Simulation), xpExplosiaFX Source tag.
  - Сейчас: nxExplosiaFX (источники перечисляются во вкладке Sources); те же принципы buoyancy/vorticity, плюс nxVorticity/nxTurbulence на GPU.

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Settings - Substeps** — https://www.youtube.com/watch?v=Km9pfAIw2tM
  - Что: когда симуляциям с высоким давлением или скоростью нужно больше substeps; CFL, min/max substeps, accuracy и max pressure iterations на примере источника с давлением 5000 и ключами.
  - Инструменты: xpExplosiaFX (Simulation ▸ Substeps), xpExplosiaFX Source tag.
  - Сейчас: nxExplosiaFX; substeps также задаются глобально в NeXus Project Settings (C4D 2026.1).

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Burn Model, Dissipation & Diffusion** — https://www.youtube.com/watch?v=FkCLZQGD95o
  - Что: химическая и кастомная burn model на горящем пятне масла и горелке Бунзена, отдельные объекты для fuel и heat для эффекта воспламенения, затем dissipation и diffusion для формы пламени и дыма.
  - Инструменты: xpExplosiaFX, xpExplosiaFX Source tag (noise-шейдеры в каналах heat/fuel).
  - Сейчас: nxExplosiaFX (настройки горения на объекте, источники во вкладке Sources); в C4D 2025.3+ возможен обмен с Pyro.

- **2022-09-16 — MNT Training - Dynamics - ExplosiaFX - The Basics - Controlling EFX with xpModifiers** — https://www.youtube.com/watch?v=CdnHYfeOHFc
  - Что: управление объёмом дыма/огня через attractor, turbulence и flow field по сплайну, затем изгиб деформерами Bend, Twist и Spline Wrap.
  - Инструменты: xpExplosiaFX, xpAttractor, xpTurbulence, xpFlowField, деформеры C4D.
  - Сейчас: nxExplosiaFX + nxAttract/nxTurbulence/nxFlowField; nxWarp (Path, Bend, Twist, Helix) теперь деформирует дым напрямую.

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Simulation Tutorials - Flame & Embers** — https://www.youtube.com/watch?v=BDoW0Qc5KCQ
  - Что: огонь в настенном светильнике: нарисованная vertex map ограничивает, какие полигоны угля горят, look-dev пламени во вкладке Simulation, герметичный collider из high-res mesh и частицы-угольки, которые адвектятся пламенем.
  - Инструменты: xpExplosiaFX, Source tag с vertex map, xpVertexMap, xpEmitter (advection), xpScale, xpCache.
  - Сейчас: nxExplosiaFX + nxEmitter с адвекцией дымом; вместо трюка с vertex map по возможности nxFalloff (Object/Attribute).

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - The Basics - Display Options** — https://www.youtube.com/watch?v=91p9Vu5Zs0s
  - Что: отображение каждого канала (fuel, smoke, temperature, velocity) во viewport, количество слайсов, trail-отображение потока и настройки цвета/прозрачности для анализа симуляции.
  - Инструменты: xpExplosiaFX (вкладка Display).
  - Сейчас: nxExplosiaFX в новом общем viewport-рендерере NeXus (лучшее отображение вокселей, 2026.1).

- **2022-09-16 — Maintenance Training - Dynamics - ExplosiaFX - Rendering Fire & Smoke** — https://www.youtube.com/watch?v=0ia33svoTX0
  - Что: volume-материал в Cycles 4D, где temperature управляет эмиссией через ноды Blackbody и Map Range, затем scattering/absorption для дыма, плюс густой углеводородный дым из огнемёта.
  - Инструменты: xpExplosiaFX (cache), Cycles 4D volume, ноды Blackbody, Map Range и Wavelength.
  - Сейчас: рендер nxExplosiaFX в Redshift (в C4D 2026.1 есть дефолтный Redshift-материал дыма); логика temperature → blackbody та же.

## Maintenance Training — Fluids

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 4 - Teacup Splash Mesh & Render** — https://www.youtube.com/watch?v=LYd96W-nRUY
  - Что: перенос закешированных частиц всплеска и ряби в сцену с чашкой от другого художника (с исправлением смещения позиции), меширование с фильтрами для гладкой поверхности, затем свет от HDRI и рендер в Cycles 4D.
  - Инструменты: копирование xpSystem вместе с xpCache, xpOpenVDBMesher (фильтры), Cycles 4D.
  - Сейчас: nxMesher (Zhu-Bridson, сглаживание Detail Aware) на nxCache; рендер в Redshift.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 3 - Intro to Splash** — https://www.youtube.com/watch?v=L0b8IaypNqo
  - Что: заполнение резервуара однокадровой эмиссией Shot, затем «корончатые» всплески от xpSplash в связке с xpSheeter и настройка их вида.
  - Инструменты: xpEmitter (Shot), xpCollider (Normals Inside), xpFluidFX, xpSplash, xpSheeter.
  - Сейчас: nxFluids + nxSplash; nxSheeter в NeXus 2026.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 2 - Intro to FluidFlip** — https://www.youtube.com/watch?v=8ly9TMUbBAY
  - Что: симуляция реки/бассейна в домене со статичными и анимированными коллайдерами; APIC против FLIP, weak spring, liquid level и viscosity.
  - Инструменты: xpFluidFLIP (вкладка Domain, настройки солвера, свойства жидкости).
  - Сейчас: nxFluids FLIP/APIC + nxMesher; в 2026.1 добавлены non-Newtonian, Wall Friction и Mixer.

- **2022-09-16 — Maintenance Training - Dynamics - Fluids - Series 1 - Solver Choice: Introduction** — https://www.youtube.com/watch?v=3e6J5kMV0o8
  - Что: один и тот же сетап emitter/gravity/collider-коробка прогоняется через три CPU-солвера жидкости, чтобы показать, как выбрать нужный.
  - Инструменты: xpFluidPBD, xpFluidFX, xpFluidFLIP, xpGravity, xpCollider.
  - Сейчас: один объект nxFluids с режимами PBD / SPH / FLIP-APIC; nxMPM для сыпучих и твердоподобных материалов.

## Premium Training — Drawing with Particles

- **2022-09-16 — Premium Training - Drawing with Particles - 03 - Wet Maps** — https://www.youtube.com/watch?v=Jj814YfqMzY
  - Что: частицы, касающиеся поверхности, превращаются в wet map на vertex map (видна через шейдер материала), чтобы нарисовать логотип на контейнере, затем экспорт в Alembic.
  - Инструменты: xpWetMap tag, xpEmitter, шейдер wet map, экспорт Alembic.
  - Сейчас: nxFalloff в режиме Wet + nxFalloffMap (falloff → vertex map / vertex color tags, C4D 2026.1).

- **2022-09-16 — Premium Training - Drawing with Particles - 02 - Stencils** — https://www.youtube.com/watch?v=KvpS0GGSCUg
  - Что: распыление частиц через выдавленный сплайн-трафарет, чтобы на стену контейнера попадал только вырез; collider-меш через деформер Collision и действия Freeze Particles для каждой системы.
  - Инструменты: xpEmitter, xpCollider, деформер Collision в C4D, xpQuestion + xpAction (Freeze Particles).
  - Сейчас: nxCollider + nxSticky или действие nxQuestion на GPU; CPU-сетап по-прежнему работает.

## Premium Training — Sci-Fi FUI

- **2022-09-16 — Premium Training - Sci-Fi FUI - 04 - Compositing** — https://www.youtube.com/watch?v=EDI4asV0UlQ
  - Что: композ beauty- и FUI-пассов из Cycles 4D в After Effects; импортированная 3D-камера помогает привязать маску-проявление к движущемуся экрану.
  - Инструменты: After Effects (данные 3D-камеры, маски).
  - Сейчас: актуально (workflow композа).

- **2022-09-16 — Premium Training - Sci-Fi FUI - 03 - Rendering** — https://www.youtube.com/watch?v=HYAjqXrexzk
  - Что: раскладка сцены по слоям и Takes для рендера beauty-пасса и отдельного FUI-пасса в Cycles 4D, доводка толщины и цвета линий.
  - Инструменты: Layers и Takes в C4D, Cycles 4D, элементы FUI на xpTrail/xpGenerator.
  - Сейчас: тот же подход с Takes, рендер в Redshift.

- **2022-09-16 — Premium Training - Sci-Fi FUI - Introduction** — https://www.youtube.com/watch?v=FCmTfd31EKE
  - Что: обзор курса про заражённую лабораторию: сочащаяся слизь на солвере жидкости с коллайдерами и flow field, плюс FUI из эмиттеров и генераторов, рендер по пассам и композ.
  - Инструменты: xpFluidFX, xpCollider, xpFlowField, xpEmitter, xpGenerator, Cycles 4D.
  - Сейчас: nxFluids SPH (вязкая жидкость) + nxFlowField, рендер в Redshift.

## Premium Training — Bonus Videos

- **2022-09-16 — Premium Training - Bonus Videos - Cycles 4D Range Mapping Node** — https://www.youtube.com/watch?v=FwpvsvZ0Cvs
  - Что: сборка переиспользуемой группы нод range mapping в Cycles 4D для ремапа цвета/радиуса частиц в шейдинге.
  - Инструменты: xpEmitter, группы нод Cycles 4D (входы данных частиц).
  - Сейчас: собственные range/remap-ноды Redshift; на стороне симуляции — NeXus Mapping или слой Remap в nxFalloff Modifier.

- **2022-09-16 — Premium Training - Bonus Videos - Falloff Positioning Without Fields** — https://www.youtube.com/watch?v=AV1PQynoC5o
  - Что: как до C4D R20 отвязать и анимировать falloff модификатора, управляя им от null через XPresso.
  - Инструменты: xpSpeed, xpFlowField (Surface Normal), XPresso.
  - Сейчас: больше не нужно: Fields в C4D (R20+) или объекты nxFalloff двигаются свободно.

## Premium Training — Fireworks

- **2022-09-16 — Premium Training - Fireworks - 05 - Compositing** — https://www.youtube.com/watch?v=CEW7ZMVsmjc
  - Что: композ рендера фейерверков из Cycles 4D в After Effects: emission-пасс, размытые слои в режиме Add и контраст для bloom, плюс резкость.
  - Инструменты: After Effects (emission-пасс, blur, режимы наложения).
  - Сейчас: актуально (или bloom прямо в рендере Redshift).

- **2022-09-16 — Premium Training - Fireworks - Introduction** — https://www.youtube.com/watch?v=FoWnGY5mC1w
  - Что: обзор курса: кастомный риг фейерверка с контролем подъёма, разрыва и формы, несколько стилей фейерверков, светящиеся материалы и композ.
  - Инструменты: xpEmitter, риг на спавне, Cycles 4D.
  - Сейчас: nxSpawn (подслои On Death / At Age) для стадий разрыва.

## Premium Training — Infectio

- **2022-09-16 — Premium Training - Infectio - 05 - Compositing** — https://www.youtube.com/watch?v=6-d380gH6Rc
  - Что: простой композ шотов со слизевиком в After Effects с цветокоррекцией и работой с альфой.
  - Инструменты: After Effects.
  - Сейчас: актуально.

- **2022-09-16 — Premium Training - Infectio - 02 - Skull Scene** — https://www.youtube.com/watch?v=FWFiCHoK0AA
  - Что: перенос сетапа заражения на скульпт-сцену с черепом: наведение порядка через System Sort, объединение и ремеш геометрии VDB-мешером и добавление UV, чтобы частицы могли эмитироваться и распространяться.
  - Инструменты: xpInfectio, xpColor, xpSystem (System Sort), xpOpenVDBMesher (remesh).
  - Сейчас: nxInfectio; ремеш через mtRemesh или Volume Builder/Mesher в C4D.

- **2022-09-16 — Premium Training - Infectio - 01 - The Spread** — https://www.youtube.com/watch?v=D9K6UGwlc8s
  - Что: основы заражения на плоскости с эмиссией из текстуры: группы по цвету, incubation и сколько соседей нужно для распространения.
  - Инструменты: xpEmitter (эмиссия из текстуры), xpInfectio, xpGroup, Data Mapping.
  - Сейчас: nxInfectio (+ NeXus Mapping).

- **2022-09-16 — Premium Training - Infectio - Introduction** — https://www.youtube.com/watch?v=CX9MB32S3rI
  - Что: обзор курса: слизевик расползается по сцене с черепом, из него растут споры; SSS-материал слизи и споры, отрендеренные трейлами.
  - Инструменты: xpInfectio, xpOpenVDBMesher, xpTrail.
  - Сейчас: nxInfectio + nxTrail; nxBioLogic (Physarum) для роста, похожего на слизевик.

## Premium Training — Logo Form

- **2022-09-16 — Premium Training - Logo Form - 02 - Something from Nothing** — https://www.youtube.com/watch?v=8zUthpInoyI
  - Что: частицы сдуваются с логотипа (flow field, attractor с обратной силой, скорость по шейдеру), а симуляция проигрывается в обратную сторону, чтобы логотип будто собирался из облака.
  - Инструменты: xpEmitter (из Connect с логотипом), xpFlowField, xpAttractor, xpSpeed, xpColor, xpHistory.
  - Сейчас: nxFlowField / nxExplode с nxFalloff; для эффекта сборки проиграть nxCache в обратную сторону.

## Premium Training — Ivy Growth

- **2022-09-16 — Premium Training - Ivy Growth - 04 - Ruins** — https://www.youtube.com/watch?v=8T1qJMhTCIw
  - Что: рост рига плюща по скульпт-руинам с церковным окном после объединения и ремеша отдельных частей, чтобы ветки не проваливались в щели; затем настройка seed и скоростей веток.
  - Инструменты: риг плюща на частицах (эмиттеры-ветки, xpTrail), xpOpenVDBMesher (remesh), xpCache.
  - Сейчас: Taiao (growth points, анимация роста) или ветки nxDendrite (NeXus 2026).

## Maintenance Training — XP Countdown

- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Granular & Advection Render** — https://www.youtube.com/watch?v=fM2RNmLJsYQ
  - Что: рендер шота «3 → 2» с рассыпанием гранул и адвекцией дыма; переиспользование камеры/света и согласование цветов между цифрами в материалах Cycles 4D.
  - Инструменты: xpFluidFX granular, адвекция xpExplosiaFX, Cycles 4D principled/volume.
  - Сейчас: nxMPM (песок) или nxFluids SPH Granular + nxExplosiaFX; рендер в Redshift.

- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Cameras, Lights, & Rendering** — https://www.youtube.com/watch?v=pIzIfG6Jpxc
  - Что: одна фиксированная камера и световой риг, проверенные на сборной сцене (всплеск, разрыв ткани, жидкости, EFX-шторка), плюс настройки рендера Cycles 4D и clamping от «светлячков».
  - Инструменты: Cycles 4D (integrator, clamping), разрыв в xpClothFX, xpExplosiaFX.
  - Сейчас: Redshift; разрыв ткани через nxDeformer + nxConstraints (2026.1) или CPU xpClothFX.

## Релизные обновления и Sneak Peeks (2022)

- **2022-09-15 — NeXus Sneak Peek - GPU - Release Update - Sept '22** — https://www.youtube.com/watch?v=BYajB1dbupw
  - Что: первая волна NeXus: скорость GPU против CPU для жидкостей SPH, PBD и granular, живая пена, пружинные constraints и переработанная turbulence (persistence, lacunarity).
  - Инструменты: ранние nxFluids, nxFoam, nxConstraints, nxTurbulence, nxRotate, nxWind.
  - Сейчас: объекты G3 nxSystem / nxEmitter в NeXus 2026, добавлены FLIP и nxMPM.

- **2022-09-13 — Taiao Sneak Peek - Growth Tab - Release Update - Sept '22** — https://www.youtube.com/watch?v=oq1QIo9qZP8
  - Что: управление ростом для каждого слоя (trunk, branch, leaf, flower, custom) с вариацией и смещённым ростом через Fields.
  - Инструменты: Taiao toPlant (вкладка Growth), Linear Field.
  - Сейчас: актуально (рост расширен в 2023.3).

- **2022-09-13 — MeshTools Sneak Peek - mtFractal - Release Update - Sept '22** — https://www.youtube.com/watch?v=2KCkHZMs73s
  - Что: процедурные 3D-фрактальные копии любого объекта (Tree, Fern, Koch, Dragon) с контролем по уровням, затем частицы и трейлы из результата.
  - Инструменты: mtFractal, xpEmitter, xpTrail.
  - Сейчас: актуально (nxTrail для трейлов на GPU).

- **2022-05-11 — INSYDIUM nxFluids Tech Preview** — https://www.youtube.com/watch?v=dmKulhMfDbg
  - Что: GPU-демо объединённого объекта nxFluids (PBD и SPH, включая granular) в сравнении с xpFluidFX, кроссплатформенно на AMD, NVIDIA и Apple.
  - Инструменты: nxFluids (PBD / SPH), xpFluidFX.
  - Сейчас: nxFluids (+ FLIP, Mixer) и nxMPM для сыпучих.

- **2022-03-16 — Taiao Sneak Peek – Coming Soon to INSYDIUM Fused** — https://www.youtube.com/watch?v=5E4Fp9Q0L84
  - Что: первый взгляд на послойный конструктор растений: слои trunk/branch/leaf/custom object, кривые формы листа, апельсиновое дерево, папоротник и цветок.
  - Инструменты: Taiao toPlant (слои trunk, branch, leaf, flower, custom object).
  - Сейчас: актуально.

- **2022-03-10 — TerraformFX Sneak Peek - Coming Soon to INSYDIUM Fused.** — https://www.youtube.com/watch?v=VPJbYtZaTPg
  - Что: grid operator с кистью для лепки рельефа, hydraulic erosion и дороги/реки по сплайнам с клонированием вдоль дороги.
  - Инструменты: tfGrid (Grid brush), tfPath, tfRoad, фильтр erosion.
  - Сейчас: актуально (+ Advanced Terrain Shader, tfDistribute в 2024).

- **2022-03-03 — MeshTools Sneak Peek – Coming Soon to INSYDIUM Fused** — https://www.youtube.com/watch?v=OONMWPXQoj8
  - Что: inset с делениями выдавливания, shape curve и twist; равномерный/адаптивный ремеш; ресемплинг сплайна с анимацией роста.
  - Инструменты: mtInset, mtRemesh, mtSplineSample.
  - Сейчас: актуально.

- **2022-02-17 — INSYDIUM xpFluidGPU - Tech Preview** — https://www.youtube.com/watch?v=leeZ8I5Ied8
  - Что: первое GPU-демо: PBD-водопад, переключённый на GPU во вкладке GPU эмиттера, при этом всё ещё с CPU-модификаторами.
  - Инструменты: xpFluidGPU, xpFluidPBD, xpGravity, xpRotator.
  - Сейчас: заменён nxFluids PBD (оранжевый эмиттер в G2, nxEmitter в G3).

## Туториалы MeshTools / Taiao / TerraformFX

- **2022-06-01 — INSYDIUM MeshTools - Crystal Smash Tutorial** — https://www.youtube.com/watch?v=9a95U9NtJ8g
  - Что: сфера-тетраэдр с ремешем и inset, poly scale по field и сплайны edge/shortest path для светящихся кристаллических осколков, пробивающихся наружу.
  - Инструменты: mtRemesh, mtInset, mtPolyScale, mtEdgeSpline, mtShortestPath, mtSubdivider, Fields в C4D.
  - Сейчас: актуально.

- **2022-04-21 — TerraformFX Tutorial - Guilin Landscape** — https://www.youtube.com/watch?v=JaWxygtVlY4
  - Что: пейзаж по референсу Гуйлиня: горы через grid operator, извилистая 3D-дорога, нарисованная в видах top/front, и erosion после path; high-res террейн на переднем плане и low-res на заднем.
  - Инструменты: tfTerrain, tfGrid, tfPath, tfRoad, оператор erosion.
  - Сейчас: актуально.

- **2022-03-31 — Taiao Tutorial - Palm Tree Build** — https://www.youtube.com/watch?v=TUs1-T0I2o0
  - Что: наклонённая пальма из слоя trunk, веток кроны, листьев и кастомного объекта-кокоса на песчаном террейне TerraformFX.
  - Инструменты: Taiao toPlant (trunk, branch, leaf, custom object), tfTerrain.
  - Сейчас: актуально.

- **2021-08-19 — MeshTools Tutorial - Crystal Growth** — https://www.youtube.com/watch?v=iNildRnEGAM
  - Что: low-poly террейн TerraformFX со стеком анимированных subdivide/inset для растущих кристаллов, рендер с subsurface scattering в Cycles 4D.
  - Инструменты: tfTerrain, mtSubdivider, mtInset, Cycles 4D SSS.
  - Сейчас: для MeshTools актуально; рендер в Redshift.

- **2021-08-12 — MeshTools Tutorial - Shortest Path Geometry Ripple** — https://www.youtube.com/watch?v=3TlsRpyG7n8
  - Что: куб, который «волной» проявляется через subdivide и inset, со стилизованными сплайнами, растущими по кратчайшим путям по мешу; экспорт в Alembic.
  - Инструменты: mtSubdivider, mtInset, mtShortestPath, mtShell, Alembic.
  - Сейчас: актуально.

- **2021-08-09 — MeshTools Tutorial - Organic Geometry** — https://www.youtube.com/watch?v=GfxbCce61n0
  - Что: стек inset на торе с недеструктивной анимацией через fields, шейдеры и noise для органичного роста.
  - Инструменты: mtInset (стеком), mtSubdivider, mtEdgeSpline, Fields/noise в C4D.
  - Сейчас: актуально.

- **2021-07-26 — TerraformFX - Mountain Landscape Tutorial** — https://www.youtube.com/watch?v=ifwFEGPMgyM
  - Что: как операторы строят террейн (чёрно-белый analysis-дисплей, генераторы spline и noise), затем горный хребет с erosion.
  - Инструменты: tfTerrain, операторы-генераторы (spline, noise), фильтры erosion.
  - Сейчас: актуально (+ Advanced Terrain Shader).

## X-Particles — xpBullet Tutorials

- **2021-08-04 — X-Particles - xpBullet Tutorial - Domino Rig** — https://www.youtube.com/watch?v=wz-3egYgShI
  - Что: процедурный риг домино: заспавненные частицы расставлены вдоль трейла, масштабируются, превращаются в доминошки генератором и опрокидываются rigid bodies Bullet.
  - Инструменты: xpBullet Collider / Rigid Body tags, xpSpawn, xpTrail, xpFlowField, xpGenerator, xpScale.
  - Сейчас: актуально на CPU (у Bullet нет nx-аналога; GPU rigid bodies анонсированы в ноябре 2026, ещё не вышли).

- **2021-07-29 — X-Particles - xpBullet Tutorial - Destruction Scene** — https://www.youtube.com/watch?v=X74ARe24Bes
  - Что: стена раскалывается на фрагменты и разбивается rigid bodies Bullet, в том числе с Bullet-тегами прямо на эмиттере.
  - Инструменты: xpShatter, xpBullet Collider / Rigid Body tags, xpGenerator.
  - Сейчас: nxShatter (2026.1, может управляться damage из nxMPM); xpShatter + Bullet по-прежнему работает.

## Sneak Peeks (2020–2021)

- **2021-07-14 — xpBullet - Sneak Peek** — https://www.youtube.com/watch?v=LaVQgqpIZQ0
  - Что: коллизии Bullet для частиц: рассыпающийся бегущий человек, точные коллизии для каждой формы отображения, вопросы о столкновении, запускающие спавн, и трейлы вместе с avoid.
  - Инструменты: xpBullet Rigid Body tag, xpQuestion (Bullet collision) + xpAction (Unstick, Spawn), xpTrail, xpAvoid, xpColor.
  - Сейчас: CPU Bullet актуален; nxMPM для мягкого/хрупкого поведения на GPU.

- **2021-06-29 — INSYDIUM TerraformFX - Coming Soon!** — https://www.youtube.com/watch?v=3A9ZFvSGKd4
  - Что: первое превью TerraformFX: слои генераторов noise/gradient, fold, 2D/3D hydraulic, thermal и coastal erosion, экспорт карт altitude/slope/erosion, сборка вулкана и группы с маской через field.
  - Инструменты: tfTerrain, генераторы и фильтры, фильтр erosion, шейдер terrain operator, Cycles 4D.
  - Сейчас: актуально.

- **2021-06-08 — INSYDIUM MeshTools - Coming Soon!** — https://www.youtube.com/watch?v=G1IPg2FZGDA
  - Что: первое превью MeshTools: edge splines (outline, curvature, contour, пересечения, по текстуре), inset по noise с проявлением через box field и рост города через subdivider.
  - Инструменты: mtEdgeSpline, mtInset, mtSubdivider, Fields в C4D.
  - Сейчас: актуально.

- **2021-05-18 — xpOpenVDBImporter - Sneak Peek** — https://www.youtube.com/watch?v=W6vcdGdhXjA
  - Что: загрузка VDB-файлов/секвенций с отображением каналов и управлением временем, затем инстансинг объёмов на каждую частицу или через MoGraph Matrix.
  - Инструменты: xpOpenVDBImporter, Cycles 4D instance tag, MoGraph Matrix/эффекторы.
  - Сейчас: прямого nx-аналога нет; xpOpenVDBImporter или объёмы Redshift.

- **2021-04-27 — xpOpenVDBMesher - Transfer Foam - Sneak Peek** — https://www.youtube.com/watch?v=djUHxGykGdg
  - Что: опция мешера, записывающая анимированную vertex map из данных пены для текстурирования меша жидкости, со сглаживанием и кривой ремапа.
  - Инструменты: xpOpenVDBMesher (Transfer Foam), xpFoam, xpFluidFX.
  - Сейчас: nxFoam + nxMesher; CPU-путь через Transfer Foam по-прежнему работает.

- **2021-04-13 — xpOpenVDBMesher - UV Advection - Sneak Peek** — https://www.youtube.com/watch?v=x8aQxHLFkoc
  - Что: UV advection, чтобы текстура, спроецированная на меш жидкости, двигалась вместе с частицами, с опорным кадром.
  - Инструменты: xpOpenVDBMesher (UV Advection), xpFluidFX.
  - Сейчас: UV advection в nxMesher (2026.1).

- **2020-06-29 — xpExplosiaFX - Sneak Peek** — https://www.youtube.com/watch?v=RTO8aeq97ao
  - Что: обновление EFX 2020 года: OpenGL-отображение объёма, поддержка деформеров (Bend, Twist, Spline Wrap), новые burn models, раздельные vorticity/turbulence и вкладка Up-Res.
  - Инструменты: xpExplosiaFX (display, Up-Res), деформеры C4D.
  - Сейчас: nxExplosiaFX + nxWarp на дыме; nxUpres.

- **2020-06-24 — xpFluidFLIP - Sneak Peek** — https://www.youtube.com/watch?v=-7eA4jDPPWk
  - Что: переписанный солвер в домене со сравнением APIC и FLIP и новыми коллизиями со статичными, быстрыми и вращающимися объектами.
  - Инструменты: xpFluidFLIP (APIC / FLIP).
  - Сейчас: nxFluids FLIP/APIC.

- **2020-06-22 — xpFlowField - Sneak Peek** — https://www.youtube.com/watch?v=pUgnMvQluts
  - Что: новая система слоёв: along spline, random и curl с режимами наложения, strength и falloff, отображение потока трейлами, surface tangent на модели руки.
  - Инструменты: xpFlowField (слои).
  - Сейчас: nxFlowField (слой Cyclic в 2026.1) или nxWarp Flow / nxFollowGeo.

## Доклады VERTEX

- **2021-02-25 — Vertex 2021 - ExplosiaFX Tutorial - Rendering Fire & Smoke** — https://www.youtube.com/watch?v=fN7emTrvW_M
  - Что: бесплатная публичная версия того же урока по рендеру огня и дыма в Cycles 4D, что и в Maintenance Training выше.
  - Инструменты: xpExplosiaFX, ноды Cycles 4D Blackbody/Map Range/volume.
  - Сейчас: nxExplosiaFX с рендером в Redshift.

## Прочее (без техники)

- INSYDIUM Fused - Out Now! (2021-07-22) — https://www.youtube.com/watch?v=2WL2Xziq-Fo
- X-Particles Fluids - Additional Content - OUT NOW! (2021-03-30) — https://www.youtube.com/watch?v=cV37Hv1YrbE
