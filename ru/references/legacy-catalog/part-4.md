# Каталог старых видео — часть 4 (2017-07-21 – 2019-03-22)

## X-Particles Early Access Updates (2019)
- **2019-03-22 — X-Particles Early Access Update - xpDynamics** — https://www.youtube.com/watch?v=in5Mig-Rvnc
  - Что: тег xpDynamics ставит частицу на каждую вершину объекта, и гравитация, коллайдеры, turbulence или любой другой XP-модификатор двигают его как твёрдое тело; работает и с результатом xpGenerator/xpSprite, а управляющие частицы могут выпускать fuel для xpExplosiaFX.
  - Инструменты: тег xpDynamics, xpGenerator, xpSprite, xpTurbulence, тег xpCollider, тег xpExplosiaFX Source, Data Mapping.
  - Сейчас: GPU-твёрдых тел пока нет (анонсированы в следующей бете NeXus) — используйте теги C4D Rigid Body на геометрии xpGenerator/nxGenerator или nxMPM (elastic/brittle); xpDynamics по-прежнему работает на CPU в Fused 2025.4.
- **2019-03-15 — X-Particles Early Access Update - Quick Tools** — https://www.youtube.com/watch?v=G93LDHb9YZw
  - Что: обзор панели Quick Tools — 25 пресетов сцен/симуляций в один клик (частицы, жидкости и гранулы, дым/огонь/адвекция, trails) плюс помощники: эмиссия с объекта/выделения/текстуры/vertex map, интерактивное тело жидкости и кэширование.
  - Инструменты: X-Particles Quick Tools, xpEmitter, xpFluidFX, xpExplosiaFX, xpTrail, xpCache.
  - Сейчас: помощники только для CPU; на GPU то же самое закрывают раздел Presets в меню Add NeXus 2026.1, папки nxSystem и сетапы nxMaterial в один клик.

## Content Repository Tutorials 2019
- **2019-03-01 — Surface Advection** — https://www.youtube.com/watch?v=amjgSU-1uE8
  - Что: у частиц, удерживаемых на поверхности, грубая ударная волна xpExplosiaFX адвектирует вращение (а не позицию), затем xpGenerator клонирует на них геометрию — получается текучий, «жидкий» узор на поверхности.
  - Инструменты: xpExplosiaFX (адвекция, крупный voxel size), xpEmitter, xpGenerator.
  - Сейчас: скорости nxExplosiaFX или nxFlowField управляют nxRotate/nxSpin у частиц, прилипших к поверхности (nxSticky) → nxGenerator.

## Cycles 4D Updates
- **2019-02-06 — Cycles 4D - Early Access Update - Build 294** — https://www.youtube.com/watch?v=vzN9wOSnFsk
  - Что: новинки Cycles 4D — переписанный real-time preview (с DOF), Cryptomatte, пересобранный node editor, микрополигональный displacement от noise-карты высот.
  - Инструменты: Cycles 4D.
  - Сейчас: Cycles 4D больше не развивается — используйте Redshift (Cryptomatte, displacement) в C4D или Blender Cycles вместе с NeXus.

## X-Particles 3.5 Tutorials
- **2019-02-05 — X-Particles 3.5 Tutorial - Data Mapping - Melt Rig** — https://www.youtube.com/watch?v=yG8i10D3Crk
  - Что: куб, заполненный по объёму частицами двух групп, плавится по мере нагрева — Data Mapping по температуре снижает переменную вязкость и усиливает гравитацию.
  - Инструменты: xpEmitter (Volume, две xpGroups), переменная вязкость xpFluidFX, Data Mapping (температура), xpGravity, тег xpCollider.
  - Сейчас: nxMPM со сменой материала по возрасту/скорости (Mixer) или вязкость через Mixer в nxFluids FLIP; Data Mapping → вкладка NeXus Mapping.
- **2019-02-05 — X Particles 3 5 Tutorial - xpWind Twister** — https://www.youtube.com/watch?v=w73CsjSgYQA
  - Что: перезалив туториала 2017 года про торнадо — «вентиляторы» xpWind в MoGraph Cloner закручивают частицы вверх по спирали; варианты с жидкостью через xpSkinner, лавой/снегом и косяком рыб через xpGenerator.
  - Инструменты: xpWind, MoGraph Cloner, xpSkinner, xpGenerator.
  - Сейчас: nxWarp Helix/Twist (режим Flow) + nxTurbulence или слои nxWind; nxMesher для жидкости, nxGenerator для рыб.
- **2019-02-05 — X-Particles 3.5 Tutorial - Spiral Growth** — https://www.youtube.com/watch?v=uu-iIprExFk
  - Что: риг из вращающейся плоскости на Xpresso несёт прикреплённые к поверхности частицы, и xpTrail рисует закрученные спиральные следы (в стиле Gyuki88), плюс дополнительный внутренний trail.
  - Инструменты: риг на Xpresso, xpEmitter, xpTrail, объект Connect.
  - Сейчас: nxWarp Helix или Path в режиме Flow с nxTrail — риг не нужен.
- **2019-02-05 — X-Particles 3.5 Tutorial - GeoBoil** — https://www.youtube.com/watch?v=uj-EpRy1qM4
  - Что: повтор гудиниевского GeoBoil Саймона Фидлера — неподвижные частицы рождаются на поверхности, растут и умирают, xpSkinner сшивает их в «кипящие» пузыри; всё упаковано в переиспользуемый риг на Xpresso.
  - Инструменты: xpEmitter (Speed 0, короткий lifespan), xpScale, xpSkinner, Xpresso.
  - Сейчас: nxEmitter + nxScale с маппингом по Age → nxMesher.
- **2019-02-05 — X-Particles 3.5 Tutorials - xpSound** — https://www.youtube.com/watch?v=oPu_1BE6n_0
  - Что: xpSound читает частотные полосы аудиофайла и мапит их (вкладка Map Sound) на эмиссию, цвет и скорость частиц из кольцевого эмиттера-цилиндра.
  - Инструменты: xpSound, xpEmitter (форма Cylinder).
  - Сейчас: прямого аналога нет — xpSound остаётся только на CPU.
- **2019-02-05 — X-Particle 3.5 Tutorial - Crystal Geodes** — https://www.youtube.com/watch?v=lK1rT3huWLI
  - Что: анимированная noise-текстура управляет эмиссией на плотной сфере, xpGenerator выращивает кристаллы-цилиндры по нормалям, а vertex map от xpWetMap выдавливает базовый меш наружу.
  - Инструменты: xpEmitter (эмиссия по текстуре), xpGenerator, тег xpWetMap, vertex map, Displacer.
  - Сейчас: nxEmitter + nxGenerator; режим Wet в nxFalloff / nxFalloffMap (C4D 2026.1) для vertex map.
- **2019-02-05 — X-Particles 3.5 Tutorial - Particle Driven Effects - Colour Scale** — https://www.youtube.com/watch?v=aD6xl-HMKJw
  - Что: продолжение Noisy Extruder — частицы второго эмиттера работают как X-Particles Falloff и гонят волны масштаба и цвета по выдавленным плиткам концентрическими кольцами.
  - Инструменты: xpEmitter, xpGenerator, xpScale, xpColor, X-Particles Falloff, Displacer.
  - Сейчас: nxFalloff в режиме Points со слоями nxScale/nxColor; Decay/Grow в nxFalloff Modifier для шлейфа колец.
- **2019-02-05 — X-Particles 3.5 Tutorial - Noisy Extruder** — https://www.youtube.com/watch?v=YGivDm0iKv0
  - Что: по одной частице в центре каждого полигона с тангенциальным вращением, на них генерируются шестигранные цилиндры, а noise falloff управляет их масштабом.
  - Инструменты: xpEmitter (Shot, одна на элемент), xpGenerator, xpScale, noise falloff.
  - Сейчас: nxEmitter + слой nxScale с nxFalloff Noise → nxGenerator (или просто MoGraph Cloner + Fields).
- **2019-02-05 — X-Particles 3.5 Tutorial - Flynit** — https://www.youtube.com/watch?v=Sypzoyqk25A
  - Что: плетение в стиле Flyknit — анимированный градиент (с новой UV на весь сотовый меш) управляет эмиссией, а xpConstraints с connected birth «вяжут» нити, которые расходятся и собирают меш.
  - Инструменты: MoGraph Cloner (Honeycomb), xpEmitter (текстура), xpConstraints, Display Constraints.
  - Сейчас: nxConstraints (+ nxPin), эмиссия ограничена через nxFalloff.
- **2019-02-05 — X-Particles 3.5 Tutorial - Fireworks** — https://www.youtube.com/watch?v=SyOcIw1ZLYU
  - Что: три фейерверка — фонтан, огненное колесо и ракета — из конусных эмиттеров, trails и вспышек spawn по срабатыванию question.
  - Инструменты: xpEmitter, xpGravity, xpTrail, xpQuestion/xpAction, xpSpawn.
  - Сейчас: nxSpawn (вспышки At Age / On Death) + nxTrail + nxGravity.
- **2019-02-05 — X-Particles 3.5 Tutorial - Controlled Fluids** — https://www.youtube.com/watch?v=McB6SzrzS8s
  - Что: арт-дирекшн FLIP-жидкости внутри домена — она идёт по круговому сплайну, затем стягивается в логотип; меш через xpSkinner плюс вторичные частицы, выпущенные с его поверхности.
  - Инструменты: домен xpFluidFLIP, xpFollowSpline, xpCover, xpQuestion, xpSkinner, xpCache.
  - Сейчас: nxFluids FLIP + nxFollowGeo или nxWarp Path, nxCover, nxMesher.
- **2019-02-05 — X-Particles 3.5 Tutorial - Plexus Geo** — https://www.youtube.com/watch?v=GLupjRXx3Ec
  - Что: соединительные линии в стиле plexus между частицами на поверхности (XP-версия эффекта на Python/VEX) на простых и сканированных моделях.
  - Инструменты: xpEmitter (Shot, Polygon Area), xpTrail (Connect, joins выключены).
  - Сейчас: на CPU по-прежнему актуально (меню Algorithm в xpTrail); вариант на GPU — nxConstraints с Display Constraints.
- **2019-02-05 — X-Particles 3.5 Tutorial - Abstract Everyday** — https://www.youtube.com/watch?v=Er-Rx153CPE
  - Что: сборка статичного абстрактного «эвридея» — xpSkinner сшивает точки геометрии, сплайнов и клонов, плюс вырезы по поверхности и трубки из trails.
  - Инструменты: xpSkinner, xpGenerator, xpTrail.
  - Сейчас: nxMesher для мешинга частиц; C4D Volume Builder для слияния геометрии; xpSkinner остаётся на CPU.
- **2019-02-05 — X-Particles 3.5 Tutorial - Scale Modifier** — https://www.youtube.com/watch?v=CN0GmjPRiWc
  - Что: новое в xpScale 3.5 — Clamp Within Range для разброса размеров и операция Set Value для растяжения по осям.
  - Инструменты: xpScale.
  - Сейчас: nxScale (слои, falloff и режимы смешивания на каждый слой).
- **2019-02-05 — X-Particles 3.5 Tutorial - Spin Modifier** — https://www.youtube.com/watch?v=46Ye_s3HfxM
  - Что: операция Rotate в xpSpin — Absolute, Face Camera и Face Object (частицы смотрят на целевой null).
  - Инструменты: xpSpin, xpScale.
  - Сейчас: nxSpin / nxRotate.
- **2019-02-05 — X-Particles 3.5 Tutorial - Depth of Field Techniques** — https://www.youtube.com/watch?v=3j7KsRyK3xA
  - Что: быстрый DOF без шума — расстояние до камеры мапится в материале X-Particles на размытие/прозрачность, рендер в Standard вместо Physical; применено и к trails на constraints с цветом по скорости.
  - Инструменты: X-Particles Material (маппинг глубины), xpTurbulence, xpConstraints, xpTrail.
  - Сейчас: DOF рендера (Redshift) по выходу nxGenerator / point cloud; трюк с материалом остаётся только для CPU.

## Content Repository Tutorials 2019
- **2019-02-04 — Cloth Matrix** — https://www.youtube.com/watch?v=gW-26xx41Ik
  - Что: полотно xpClothFX используется только как источник движения для MoGraph Matrix (со смещением от Random effector), а на рендере инстансится в тысячи металлических boolean-форм.
  - Инструменты: xpClothFX, MoGraph Matrix, Random Effector, тег Cycles 4D Instance.
  - Сейчас: ткань на nxConstraints (+ nxPin) управляет Matrix или nxGenerator; инстансинг в Redshift.

## Public Release 2018
- **2018-10-25 — New Features - Public Release 2018** — https://www.youtube.com/watch?v=vlBxJB-IPvg
  - Что: главное в релизе под R20 — C4D Fields как falloff модификаторов, адаптивные коллизии, сэмплинг шейдера в пространстве, xpInfection с группами incubating/infected, xpSystemSort, xpWave, теги цвета/скорости у OpenVDB Mesher, экспорт Alembic, векторный режим вращения, Constrain Axis в xpNetwork.
  - Инструменты: C4D Fields, xpInfection, xpWave, xpOpenVDBMesher, xpVertexMap, xpNetwork, xpCache.
  - Сейчас: nxFalloff, nxInfectio, nxWave / nxOcean, выходы nxMesher, Alembic в nxCache.
- **2018-10-15 — FluidFX Speed Improvements - Public Release 2018** — https://www.youtube.com/watch?v=n8f4eFlABw4
  - Что: пересобранный SPH-солвер xpFluidFX правится вживую через xpTurbulence, xpWind и водоворот xpFlowField, плюс стабильные анимированные коллайдеры.
  - Инструменты: xpFluidFX, xpTurbulence, xpWind, xpFlowField, тег xpCollider.
  - Сейчас: nxFluids SPH/FLIP с nxTurbulence, nxWind, nxFlowField.

## Early Access 2018
- **2018-07-13 — xpFluidFX - X-Particles Early Access Speed Improvements** — https://www.youtube.com/watch?v=phYowXy4BX0
  - Что: более ранняя версия того же SPH-демо — живое взаимодействие с модификаторами и flow field, быстрые стабильные коллизии.
  - Инструменты: xpFluidFX, xpTurbulence, xpWind, xpFlowField.
  - Сейчас: nxFluids SPH/FLIP.

## xpReel Tutorials (2018)
- **2018-06-28 — xpReel Tutorials, Strange Cloth, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=fHDNLCeYfGQ
  - Что: рендер сцены strange cloth — свой материал ткани, тег Cycles Instance со сферами на частицах пыли, камера с DOF и чистые настройки рендера.
  - Инструменты: Cycles 4D, тег Cycles Instance, результат xpClothFX.
  - Сейчас: рендер в Redshift (или Blender Cycles через point cloud NeXus); инстансы через nxGenerator.
- **2018-06-26 — xpReel Tutorials, Strange Cloth - X-Particles - Part 1** — https://www.youtube.com/watch?v=Ypi_fWn79EY
  - Что: много плоскостей симулируются как ткань одним сетапом, strange attractor Лоренца утягивает их от камеры, а частицы пыли закручиваются тканью.
  - Инструменты: xpClothFX (cloth emitter, модификатор, деформер), объект Connect, xpStrangeAttractors, xpTurbulence.
  - Сейчас: ткань на nxConstraints + nxPin; у strange attractors нет GPU-аналога (оставляйте CPU-модификатор).
- **2018-06-20 — xpReel Tutorials, Water Helix, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=brUKYFSP_zI
  - Что: рендер меша водяной спирали с цветом частиц по скорости, запечённым в vertex map, плюс свет и малая глубина резкости.
  - Инструменты: Cycles 4D (нода Attribute point color), vertex maps от xpOpenVDBMesher.
  - Сейчас: цветовой выход nxMesher читается в Redshift / атрибутах Blender.
- **2018-06-18 — xpReel Tutorials, Water Helix -X-Particles - Part 1** — https://www.youtube.com/watch?v=c_DVzU5h5Kw
  - Что: xpFlowField вдоль сплайна-спирали направляет симуляцию xpExplosiaFX, которая адвектирует частицы (цвет от синего к белому по скорости); кэш сшивается в водяную спираль.
  - Инструменты: xpFlowField, xpExplosiaFX (адвекция), xpEmitter, xpCache, xpOpenVDBMesher.
  - Сейчас: nxExplosiaFX + nxWarp Helix (работает и на дыме) или nxFlowField; nxMesher с переносом цвета.
- **2018-06-14 — xpReel Tutorials, Particle Advection, Cycles 4D - Part 2** — https://www.youtube.com/watch?v=YUW7NqPDk6Y
  - Что: шейдинг закэшированных адвектированных частиц — смешивание/сложение бликовых и эмиссионных шейдеров по запечённому цвету частиц, плюс свет и DOF.
  - Инструменты: Cycles 4D, xpCache.
  - Сейчас: шейдинг частиц / point cloud в Redshift по каналам NeXus.
- **2018-06-11 — xpReel Tutorials, Particle Advection, X-Particles - Part 1** — https://www.youtube.com/watch?v=lw5aRCM7k_w
  - Что: клонированные MoGraph цилиндры выпускают fuel EFX, а его шлейфы (с вариацией через температуру) адвектируют частицы; цветовые данные запекаются в кэш для рендера.
  - Инструменты: xpExplosiaFX, MoGraph Cloner, xpEmitter, xpCache.
  - Сейчас: nxExplosiaFX адвектирует nxEmitter, nxCache.
- **2018-06-05 — xpReel Tutorials, Procedural Growth - Cycles 4D - Part 2** — https://www.youtube.com/watch?v=WGUggSQaBFs
  - Что: рендер роста коралла — шейдеры золотой крошки и эмиссии под noise-маской, управляемые кэшированным цветом, плюс DOF и motion blur.
  - Инструменты: Cycles 4D, xpCache, xpOpenVDBMesher.
  - Сейчас: Redshift с атрибутами nxMesher/nxBioLogic.
- **2018-06-05 — xpReel Tutorials, Procedural Growth - X-Particles - Part 1** — https://www.youtube.com/watch?v=aCf110U-aBI
  - Что: рост xpCellAuto сшивается в коралл, отдельная система EFX адвектирует парящую пыль, цветовые данные кэшируются.
  - Инструменты: xpCellAuto, xpOpenVDBMesher, xpExplosiaFX, xpCache.
  - Сейчас: nxBioLogic (коралл / рост) + nxExplosiaFX.

## Quick Guides
- **2018-05-29 — Quick Guide - How to import OpenVDB files to X-Particles, then render with Cycles 4D** — https://www.youtube.com/watch?v=6qsxhWhJqTo
  - Что: загрузка скачанного VDB-облака в домен xpExplosiaFX через xpCache и рендер в Cycles 4D с пресетами volume.
  - Инструменты: домен xpExplosiaFX, xpCache, Cycles 4D.
  - Сейчас: C4D Volume Loader / Redshift Volume или Volume в Blender; nxExplosiaFX пишет VDB output для своих симуляций.

## Early Access New Features (2018)
- **2018-05-25 — Early Access New Features - X-Particles, xpEmitter** — https://www.youtube.com/watch?v=MHPrgcvGtGA
  - Что: отображение Modifier Field у эмиттера (силы turbulence стрелками/точками/линиями), UV Emission Data (цвет частиц из видеотекстуры), инстансинг эмиттеров через MoGraph, falloff в questions.
  - Инструменты: xpEmitter, xpTurbulence, xpQuestion, MoGraph Cloner.
  - Сейчас: viewport-рендерер NeXus 2026.1 рисует поля; цвет из текстур через nxColor / Mapping.
- **2018-05-23 — Early Access New Features - X-Particles, xpOVDBMesher** — https://www.youtube.com/watch?v=tCMndzHMKWk
  - Что: OpenVDB Mesher переносит цвет и скорость частиц в vertex maps (для рендера и motion blur на посте) и создаёт карты object ID для каждого источника.
  - Инструменты: xpOpenVDBMesher, xpSplineFlow.
  - Сейчас: nxMesher выдаёт color / velocity / emitter IDs.
- **2018-05-22 — Early Access New Features - X-Particles, Generators & Modifiers** — https://www.youtube.com/watch?v=Id2R5UtrptY
  - Что: xpAttractor с объектами сцены как целями (nearest/furthest), модификаторы, читающие физические данные (temperature, fuel), и Constrain Axis в xpNetwork, сохраняющий пути сетки под 90° при turbulence.
  - Инструменты: xpAttractor, xpNetwork, xpTrail, xpTurbulence.
  - Сейчас: nxAttract; у xpNetwork нет прямого аналога в NeXus.

## X-Particles 4 Tutorials
- **2018-01-26 — X-Particles 4 - Nearest Particle Tutorial** — https://www.youtube.com/watch?v=7bl2ERnKpk8
  - Что: бесконечная система спавна — плоские, тормозимые drag частицы порождают новые, когда xpQuestion замечает соседнюю частицу.
  - Инструменты: xpLimit, xpDrag, xpQuestion (Nearest Particle), action xpSpawn, коллизии.
  - Сейчас: поиск соседей в nxQuestion + nxSpawn; nxLimit, nxDrag.
- **2018-01-09 — StrangeOrb Tutorial** — https://www.youtube.com/watch?v=1k2AK6SUBzU
  - Что: частицы под xpStrangeAttractors мечутся внутри сферы-коллайдера (нормали внутрь), рендер в Cycles 4D с HDRI-окружением.
  - Инструменты: xpStrangeAttractors, тег xpCollider (внутрь), xpTrail, Cycles 4D.
  - Сейчас: nxCollider для оболочки; strange attractors остаются только на CPU.
- **2017-12-14 — xpExplosiaFX - Rendering Guide** — https://www.youtube.com/watch?v=o3xq7I1FRtY
  - Что: простой дым/огонь от сферы-источника, рендер через volume-материал Cycles 4D (absorption + scatter, blackbody), затем экспорт VDB для Redshift и Octane.
  - Инструменты: xpExplosiaFX, тег Source, volume-ноды Cycles 4D, экспорт VDB.
  - Сейчас: nxExplosiaFX с дефолтным smoke-материалом Redshift / VDB output; связка с Pyro в C4D 2025.3+.

## Cycles 4D Updates
- **2017-12-13 — Cycles 4D Update - Build 247** — https://www.youtube.com/watch?v=h2jZtHBd0PU
  - Что: улучшения node editor (цвета каналов, контекстный фильтр, мини-вьюер, режимы проводов, превью выхода каждой ноды) и пост-эффекты камеры (bloom, glare, виньетка, filmic).
  - Инструменты: Cycles 4D.
  - Сейчас: Cycles 4D больше не развивается — пост-эффекты Redshift / композитинг Blender.

## X-Particles 4 Sneak Peeks
- **2017-11-28 — xpFluidPDB & xpFluidFX - X-Particles, New Feature Sneak Peek** — https://www.youtube.com/watch?v=7gGSdnJXbaE
  - Что: xpFluidPBD для быстрых мелкомасштабных жидкостей (усики от external pressure, вязкость, поверхностное натяжение, работа с constraints) и гибридный SPH xpFluidFX с настройками жидкости на каждый эмиттер для смеси плотностей.
  - Инструменты: xpFluidPBD, xpFluidFX, xpSplineFlow, xpOpenVDBMesher.
  - Сейчас: nxFluids PBD/SPH/FLIP + Mixer на эмиттер.
- **2017-11-22 — xpExplosiaFX Part II - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=m98WDn-uIKg
  - Что: XP-модификаторы в списке сил EFX, xpFlowField направляет дым, адвекция частиц в один клик с цветом, унаследованным от симуляции.
  - Инструменты: xpExplosiaFX, xpTurbulence, xpRotator, xpFlowField.
  - Сейчас: nxExplosiaFX с nx-модификаторами и nxWarp на дыме.
- **2017-11-20 — xpExplosiaFX Part I - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=j_wnmiu3UsQ
  - Что: основы EFX — домен, тег Source, voxel size и детализация, отображение каналов, fuel/ignition/buoyancy, ветер и turbulence EFX, теги коллайдера.
  - Инструменты: xpExplosiaFX, тег EFX Source, тег EFX Collider, EFX Wind.
  - Сейчас: nxExplosiaFX (источники во вкладке Sources, nxCollider).
- **2017-11-13 — xpVertexMap Maker - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=c-rCBcBmBCY
  - Что: анимированные vertex maps по текстуре, скорости вершин, касанию частиц или данным взрыва — для управления displacement, эмиссией и xpScale.
  - Инструменты: xpVertexMap, xpScale, xpDrag.
  - Сейчас: nxFalloffMap (C4D 2026.1) запекает nxFalloff (вкл. Wet) в vertex maps.
- **2017-11-06 — xpOpenVDB - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=aNFOQ2jOL50
  - Что: OpenVDB Mesher для частиц и геометрии — контроль voxel/radius, стек фильтров, заполнение сферами, ремеш и живые булевы операции.
  - Инструменты: xpOpenVDBMesher.
  - Сейчас: nxMesher для частиц; xpOpenVDBMesher / C4D Volume Builder для ремеша геометрии и булевых операций.
- **2017-10-30 — xpStrangeAttractors & xpNewtonGravity - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=XRqy2K2msZ0
  - Что: восемь пресетов хаотических аттракторов со scale/delta/константами, trails сшиваются в абстрактные формы, а Newton gravity даёт объектам орбитальное притяжение и меняет размер частиц по расстоянию.
  - Инструменты: xpStrangeAttractors, xpGravity (Newton), xpTrail, xpOpenVDBMesher.
  - Сейчас: nxGravity (Effect Towards) для орбит; strange attractors остаются только на CPU.
- **2017-10-23 — xpCirclePacker & xpCellAuto - X-Particles 4, New Feature Sneak Peek** — https://www.youtube.com/watch?v=rwhY3v01zfk
  - Что: Circle Packer выпускает непересекающиеся частицы с min/max радиусом и кривыми масштаба; Cell Auto выращивает узоры по элементарным правилам, Game of Life и diffusion-limited aggregation.
  - Инструменты: xpCirclePacker, xpCellAuto.
  - Сейчас: nxBioLogic заменяет xpCellAuto; у circle packing прямого аналога нет (приближённо — nxPush + nxScale).
- **2017-10-16 — xpSplineFlow - X-Particles 4 - New Feature Sneak Peek** — https://www.youtube.com/watch?v=TgWvZXlw94Y
  - Что: частицы идут по любому сплайну с силами Along/Towards/Rotate/Attraction на каждом хэндле, сочетаются с turbulence и жидкостями.
  - Инструменты: xpSplineFlow, xpTurbulence.
  - Сейчас: nxFollowGeo (режим spline) или nxWarp Path.
- **2017-10-09 — xpFlowField - X-Particles - New Feature - Sneak Peek** — https://www.youtube.com/watch?v=S282_UbC63s
  - Что: поле скоростей из сплайнов, нормалей/касательных геометрии, частиц/trails или шейдеров, с falloff и слоями режимов.
  - Инструменты: xpFlowField.
  - Сейчас: nxFlowField (NeXus 2026); xpFlowField по-прежнему есть в Fused.
- **2017-10-02 — xpClothFX - X-Particles - New Feature - Sneak Peek** — https://www.youtube.com/watch?v=5834UlTSS84
  - Что: тег/деформер ткани с pinning, коллайдерами, самоколлизиями, разрывами по картам или группам и объектом Cloth Surface для рваных краёв и толщины.
  - Инструменты: тег xpClothFX, тег Cloth Pin, Cloth Surface, тег xpCollider.
  - Сейчас: nxConstraints + nxPin, nxDeformer для разрывов (GPU-ткань анонсирована в следующей бете); xpClothFX остаётся на CPU.

## Webinars
- **2017-07-26 — Maxon Webinar 2017 Cycles 4D Motion Design** — https://www.youtube.com/watch?v=nRgDMUnwldM
  - Что: Cycles 4D для моушн-дизайна — нодовые материалы (стек mix shader, Fresnel, стекло), рендер на CPU/GPU, рендер MoGraph и X-Particles.
  - Инструменты: Cycles 4D, MoGraph, X-Particles.
  - Сейчас: Cycles 4D больше не развивается — Redshift в C4D.

## Tutorials (2017)
- **2017-07-21 — xpWind Twister - Tornado Effects - Full Tutorial** — https://www.youtube.com/watch?v=6uumSQpGOrA
  - Что: оригинальный сетап торнадо — клонированные «вентиляторы» xpWind закручивают частицы вверх; варианты с жидкостью через xpSkinner, лавой/снегом и косяком рыб через xpGenerator.
  - Инструменты: xpWind, MoGraph Cloner, xpSkinner, xpGenerator.
  - Сейчас: nxWarp Helix/Twist + nxTurbulence или слои nxWind; nxMesher, nxGenerator.

## Прочее (без техники)
- 2018-10-08 — X-Particles Speed Improvements - Public Release 2018 — https://www.youtube.com/watch?v=WmVMn06Guhk
- 2018-10-05 — X-Particles Client Story - Territory Studio — https://www.youtube.com/watch?v=RTn-KSgC4-0
- 2018-05-01 — X-Particles Sneak Peek - Speed; E.A.R - 10th May — https://www.youtube.com/watch?v=-TMsxTsL5NY
