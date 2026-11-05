# Каталог старых видео — часть 3 (2019-03-27 – 2020-06-18)

## Maintenance Training — XP Countdown, Series 3 (рендер и композитинг)
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Compositing In After Effects** — https://www.youtube.com/watch?v=bzDVMDJVm4g
  - Что: импорт пяти отрендеренных секвенций обратного отсчёта (плюс beauty- и emission-пассы) в After Effects, ретайм, стоп-кадры и сборка в один монтаж.
  - Инструменты: After Effects (Import Multiple Files, секвенции изображений, дублирование слоёв / стоп-кадры); рендеры из сцен countdown на X-Particles.
  - Сейчас: актуально (workflow композитинга не зависит от партикловых инструментов).
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Six Fill Render** — https://www.youtube.com/watch?v=PjaJxtJ735k
  - Что: свет и рендер сцены с заполнением «6» — закэшированная жидкость, сшитая OpenVDB-мешем внутри Boole с MoText, плюс закэшированные частицы пены; свет, камеры и материалы берутся из прошлых рендер-сборок, радиус пузырьков уменьшается на этапе рендера.
  - Инструменты: xpOpenVDBMesher, xpFoam (cache), xpCache, материалы Cycles 4D, C4D Boole + MoText.
  - Сейчас: nxMesher + nxFoam (Fused 2025.4, GPU), рендер в рендерере хоста (например, Redshift).
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Four Shatter Render** — https://www.youtube.com/watch?v=GVRrMENF-p4
  - Что: добавляет анимацию трещин рассыпающейся «4», чтобы кадр не был статичным, перекэширует и шейдит осколки mix shader'ом, управляемым выходом Selection у xpShatter; рендер EXR-пассов.
  - Инструменты: xpShatter (вкладка Selection), пыль xpExplosiaFX, xpCache, mix shader Cycles 4D, вывод OpenEXR.
  - Сейчас: nxShatter (NeXus 2026.1) + nxExplosiaFX; в стабильном C4D xpShatter по-прежнему актуален.
- **2020-06-18 — Maintenance Training - XP Countdown - Series 3 - Point Density Render** — https://www.youtube.com/watch?v=DLWa30MwOZw
  - Что: дым xpExplosiaFX рендерится только там, где проходит сквозь геометрию «1», — текстура point density читает канал дыма EFX в мировых координатах, затем плотность ремапится через color ramp в principled volume.
  - Инструменты: xpExplosiaFX, текстура Point Density Cycles 4D, Principled Volume, color ramp.
  - Сейчас: VDB-вывод nxExplosiaFX рендерится в рендерере хоста; сам трюк с маскированием объёма прямого аналога в NeXus не имеет.

## Sneak Peeks
- **2020-06-17 — xpScatter - Sneak Peek** — https://www.youtube.com/watch?v=nG79HnArIss
  - Что: превью генератора xpScatter — раскидывание объектов по полигонам, вершинам, площади, текстурам или освещённости с правилами топологии (высота/уклон/кривизна), разносом через kill/push и вариациями; работает на анимированных поверхностях, xpOcean, сплайнах и трейлах.
  - Инструменты: xpScatter, xpOcean, эффекторы MoGraph, модификаторы X-Particles.
  - Сейчас: nxScatter (NeXus 2026.1 Beta 3, точки на мешах → nxGenerator); xpScatter в Fused по-прежнему актуален.
- **2020-06-15 — Intersections - Sneak Peek** — https://www.youtube.com/watch?v=Cr9uzVLjjLg
  - Что: превью новой вкладки Intersections — пересечения трейлов детектятся, и частицы меняют направление, запускают spawn или замирают; получаются непересекающиеся сетки и органичные ветвления.
  - Инструменты: xpNetwork, xpBranch (вкладка Intersection), xpTrail, xpSpawn через trigger action.
  - Сейчас: в NeXus путь — nxDendrite (branches/network/lattice); пересечения в xpNetwork/xpBranch на CPU по-прежнему актуальны.

## Maintenance Training — Constraints
- **2020-06-11 — Maintenance Training - Dynamics - Constraints - Simple Cloth Tutorial** — https://www.youtube.com/watch?v=whjVGe3DuQo
  - Что: по одной частице на вершину плоскости, связи при рождении по рёбрам и диагоналям полигонов дают быструю ткань, которая ложится на сферу; затем частицы деформируют low-poly плоскость, а Subdivision Surface её сглаживает.
  - Инструменты: xpConstraints (Connections — polygon edges / diagonals), xpGravity, xpCollider tag, xpDeformer, C4D Subdivision Surface.
  - Сейчас: nxConstraints + nxPin с nxDeformer (NeXus 2026.1); в стабильном C4D — xpClothFX или тот же CPU-сетап.

## XP Countdown tutorials
- **2020-06-11 — Break scene objects, animate shattered pieces & create dust effects using X-Part…** — https://www.youtube.com/watch?v=EoDeHKiCB7k
  - Что: «4» разбивается и осыпается, открывая «3»; осколки толкаются вдоль сплайна тройки через explode и коллайдер, добавляется пыль xpExplosiaFX.
  - Инструменты: xpShatter, xpDynamics, xpExplode, xpCollider tag, xpExplosiaFX, xpCache, MoText.
  - Сейчас: nxShatter + nxExplosiaFX (NeXus 2026.1) или nxBind → nxMPM brittle для осыпания; в стабильном C4D — xpShatter + CPU-динамика.

## INSYDIUM Training
- **2020-06-09 — INSYDIUM Training - Dynamic Water - xpOcean & xpFluidFX** — https://www.youtube.com/watch?v=pl1aX6iT3so
  - Что: объём воды xpFluidFX в коробке с пеной, взаимодействующий с объектом, поверх которого накладывается волновая деформация xpOcean (wave height, choppiness, детализация).
  - Инструменты: xpFluidFX, xpFoam, xpCollider tag (normals внутрь), xpOcean, box-эмиттер.
  - Сейчас: nxOcean с FLIP coupling (NeXus 2026.1); в стабильном C4D — nxFluids FLIP + nxWave + nxFoam.

## XP Countdown tutorials
- **2020-06-04 — Create a smoke and fire simulation, add organic cloth motion and build a cloth d…** — https://www.youtube.com/watch?v=C-7JxBDJ-S0
  - Что: огонь xpExplosiaFX выжигает пакет, обтянувший «5», а по частицам ткани расползается заражение; плавление/разрыв каждой частицы отсчитывается от момента заражения.
  - Инструменты: xpExplosiaFX, xpInfectio (incubation groups), xpClothFX (tearing), Data Mapping на время в модификаторе, xpCache.
  - Сейчас: nxExplosiaFX + nxInfectio, ткань через nxConstraints/nxPin с разрывом nxDeformer (NeXus 2026.1); в стабильном C4D — xpClothFX.

## INSYDIUM Training
- **2020-05-30 — INSYDIUM Training - xpCache Retiming 02** — https://www.youtube.com/watch?v=OamxZDVUiVY
  - Что: Water Spin, часть 5 — на риге Xpresso/user data рисуются плавные кривые speed ramp, трек ретайма копируется, чтобы все кэши ретаймились одинаково.
  - Инструменты: xpCache (retime), Xpresso, user data, анимационные треки.
  - Сейчас: для xpCache актуально; документированного рига ретайма для nxCache нет.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-05-28 — Maintenance Training - Dynamics - FlowField - Planetary Weather Tutorial** — https://www.youtube.com/watch?v=uDq_2RqjjBg
  - Что: стилизованная закрученная «погода» на планете — xpFlowField в режиме surface, управляемый ригом из повёрнутых полигонов в клонере; затем проверка на другой геометрии.
  - Инструменты: xpFlowField (Surface flow), quick tool Emit from Object, MoGraph Cloner, xpFollowSurface.
  - Сейчас: nxFlowField (NeXus 2026.1) или nxFollowGeo в режиме поверхности (Fused 2025.4).
- **2020-05-28 — Maintenance Training - Constraints - Chain Reaction Tutorial** — https://www.youtube.com/watch?v=9x4cG4Ihej0
  - Что: частицы, связанные при рождении, растут в масштабе в зависимости от движения, поэтому вдавливаемый коллайдер запускает органичный цепной рост.
  - Инструменты: xpConstraints (connect at birth), xpScale с маппингом по скорости, xpCollider tag, shot-эмиссия с плоскости.
  - Сейчас: nxConstraints + nxScale с Mapping по Speed (Fused 2025.4, GPU).

## INSYDIUM Training
- **2020-05-22 — INSYDIUM Training - xpCache Retiming 01** — https://www.youtube.com/watch?v=wrbSZcv-yf4
  - Что: Water Spin, часть 4 — три закэшированные системы переносятся в чистую сцену, строится риг user data/Xpresso для совместного ретайма (speed ramp: быстро/слоу-мо).
  - Инструменты: xpCache (retime), Xpresso, user data.
  - Сейчас: для xpCache актуально; документированного рига ретайма для nxCache нет.

## XP Countdown tutorials
- **2020-05-21 — Use X-Particles in C4D to simulate viscous liquid object fill (Density Sep) ｜ xp…** — https://www.youtube.com/watch?v=qQCLXXnSoxo
  - Что: «5» заполняется вязкими жидкостями разной плотности, которые расслаиваются и смешиваются; старт эмиттеров разносится формулой в поле ввода, одна из жидкостей мешится.
  - Инструменты: xpFluidFX (density, viscosity), несколько эмиттеров, xpOpenVDBMesher, MoText-коллайдер.
  - Сейчас: nxFluids FLIP с Mixer (density/viscosity на эмиттер) + nxMesher (NeXus 2026.1).

## INSYDIUM Training
- **2020-05-18 — INSYDIUM Training - xpFluidFX Hero Splash** — https://www.youtube.com/watch?v=qRJDmKFO-oY
  - Что: Water Spin, часть 3 — арт-директорский hero splash, обвивающий базовые сферы: новые эмиттеры, исключения коллизий по группам и кэш под последующий ретайм.
  - Инструменты: xpFluidFX, xpFoam, xpCollider tag (исключения коллизий), xpCache.
  - Сейчас: nxFluids FLIP/APIC + nxSplash + nxMesher (Fused 2025.4).
- **2020-05-15 — INSYDIUM Training - xpFluidFX Splash** — https://www.youtube.com/watch?v=GrGnRSPQYT0
  - Что: Water Spin, часть 2 — закрученный водяной всплеск с пеной вокруг закэшированных сфер, мешинг OpenVDB-мешером (разбор point radius и voxel size).
  - Инструменты: xpFluidFX, xpFoam, xpGravity (Newton), xpOpenVDBMesher, xpCache.
  - Сейчас: nxFluids FLIP/APIC + nxFoam + nxMesher (Fused 2025.4).

## Maintenance Training — FlowField
- **2020-05-14 — Maintenance Training - Dynamics - FlowField - Bar Magnets Tutorial** — https://www.youtube.com/watch?v=J9PHTpT_Jzk
  - Что: силовые линии полосового магнита строятся сплайнами и клонерами, подаются в xpFlowField, поле экспортируется/импортируется для дублирования, воссоздаётся опыт с железными опилками.
  - Инструменты: xpFlowField (spline flow, export/import), MoGraph Cloner, сплайны.
  - Сейчас: nxFlowField (NeXus 2026.1); для формирования потоков — nxWarp / nxFollowGeo.

## INSYDIUM Training
- **2020-05-12 — INSYDIUM Training - xpFlowField Spline Control** — https://www.youtube.com/watch?v=YbKzbvh29QA
  - Что: Water Spin, часть 1 — структура папок проекта и кэша, динамические сферы ведутся xpFlowField в режиме spline с data mapping на частицах.
  - Инструменты: xpFlowField (spline mode), xpEmitter, Data Mapping, xpCache.
  - Сейчас: nxFollowGeo в режиме spline или nxWarp Path (NeXus 2026.1); nxFlowField — для управления полем.
- **2020-05-11 — INSYDIUM Training - xpVertexMap** — https://www.youtube.com/watch?v=jttdFsnXmg0
  - Что: обзор переписанного xpVertexMap — один объект даёт живые vertex map'ы на нескольких (даже параметрических) объектах; режимы слоёв (polygons, textures, seed), сглаживание, яркость и контраст на слой.
  - Инструменты: xpVertexMap.
  - Сейчас: режимы nxFalloff + nxFalloffMap для запекания falloff'ов в vertex map'ы (C4D, NeXus 2026.1); xpVertexMap по-прежнему актуален.

## Maintenance Training — Constraints
- **2020-05-07 — Maintenance Training - Constraints - Fluids Explained** — https://www.youtube.com/watch?v=1j9GJBzut94
  - Что: разбор настроек surface tension, viscosity и friction в constraints — капли, жёсткая тягучая жидкость, мокрый песок.
  - Инструменты: xpConstraints (Surface Tension, Viscosity, Friction), гексагональный shot-эмиттер, xpCollider tag.
  - Сейчас: nxFluids PBD/SPH (surface tension, viscosity) или nxConstraints; для мокрого песка — nxMPM Sand.

## INSYDIUM Training
- **2020-05-06 — INSYDIUM Training - Trail Display** — https://www.youtube.com/watch?v=EOSe3xbJRQg
  - Что: новый режим отображения Trails в xpFlowField и xpExplosiaFX и его рендер через xpDisplayRender в Cycles 4D, Standard и Physical.
  - Инструменты: xpFlowField, xpExplosiaFX (Trails display), xpDisplayRender, emission-материал Cycles 4D.
  - Сейчас: на CPU (Fused) актуально; прямого аналога в NeXus нет.
- **2020-05-04 — INSYDIUM Training - xpOcean** — https://www.youtube.com/watch?v=KFI08viXs2w
  - Что: разбор xpOcean (волны Тессендорфа) как примитива или деформера — размер, сегменты, wave height, time scale, типы noise, resolution — и бесшовная стыковка нескольких плоскостей через xpJoin.
  - Инструменты: xpOcean, xpJoin.
  - Сейчас: nxOcean (NeXus 2026.1); в стабильном C4D xpOcean по-прежнему актуален.

## XP Countdown tutorials
- **2020-04-30 — Create an exploding splash simulation using X-Particles in Cinema 4D： Integrate…** — https://www.youtube.com/watch?v=SOHvUX6L-QM
  - Что: кастомный всплеск из «6» на xpFluidFX и xpSheeter с ключами, затем мешинг; закэшированный пакет переиспользуется, у cache tag включается hold.
  - Инструменты: xpFluidFX, xpSheeter, xpOpenVDBMesher, xpCache (cache tag, copy tag data).
  - Сейчас: nxFluids FLIP + nxSplash + nxMesher (Fused 2025.4); nxSheeter для тонких плёнок (NeXus 2026).

## INSYDIUM Training
- **2020-04-29 — INSYDIUM Training - xpFlock** — https://www.youtube.com/watch?v=q14LkWwesLA
  - Что: стая рыб на xpFlock — тангенциальное вращение с up vector +Y, поведения (separation, chaos…), затем reactions и avoidance.
  - Инструменты: xpFlock (Behaviors, Reactions, Avoidance), xpEmitter (вращение во вкладке Extended).
  - Сейчас: nxFlock с дочерними nxFlock Reactor (Fused 2025.4, GPU).

## Sneak Peeks (Beta Access)
- **2020-04-28 — INSYDIUM Beta Access - Sneak peek - xpPushApart** — https://www.youtube.com/watch?v=IexdLfCMElo
  - Что: превью xpPushApart — расталкивание перекрывающихся частиц по дистанции или радиусу, в том числе вместе с растущим scale-модификатором.
  - Инструменты: xpPushApart, xpScale.
  - Сейчас: nxPush (GPU, намного быстрее).
- **2020-04-27 — INSYDIUM Beta Access - Sneak Peek - xpOcean** — https://www.youtube.com/watch?v=9pQOO6faWTw
  - Что: превью xpOcean — зацикливаемые волны, choppiness, глубина, направление ветра, vertex map пены и режимы деформера (local/world/surface).
  - Инструменты: xpOcean.
  - Сейчас: nxOcean (NeXus 2026.1, пена/брызги встроены).
- **2020-04-26 — INSYDIUM Beta Access - Sneak Peek - Trail Display** — https://www.youtube.com/watch?v=vExeD3XMzc0
  - Что: превью рендерящихся режимов отображения Trails, plane и voxel для xpFlowField, в том числе поле, управляемое симуляцией xpExplosiaFX.
  - Инструменты: xpFlowField (Trail display), xpExplosiaFX, xpDisplayRender.
  - Сейчас: на CPU актуально; прямого аналога в NeXus нет.
- **2020-04-25 — INSYDIUM Beta Access - Sneak Peek - xpEmitter** — https://www.youtube.com/watch?v=FuqDknGFUtM
  - Что: превью режима simulate у эмиттера — изменения эмиссии (уклон топологии, текстура, порог vertex map) видны вживую на кадре 0; плюс единый список модификаторов/questions.
  - Инструменты: xpEmitter (Simulate mode, topology, texture emission, vertex map threshold).
  - Сейчас: nxEmitter (NeXus 2026) для GPU; xpEmitter по-прежнему актуален.
- **2020-04-24 — INSYDIUM Beta Access - Sneak Peek - xpVertexMap** — https://www.youtube.com/watch?v=z8rPNIcd1HY
  - Что: превью слоёвого xpVertexMap — анимированные карты на примитивах/генераторах, blend-режимы, режимы AO и curvature, расползание от seed, управление эмиссией и динамикой.
  - Инструменты: xpVertexMap, xpDynamics.
  - Сейчас: nxFalloff (Curvature, AO, Wet) + nxFalloffMap (NeXus 2026.1); xpVertexMap по-прежнему актуален.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-04-23 — Maintenance Training - Dynamics - FlowField - Cell Size Explained** — https://www.youtube.com/watch?v=XBDGF8VDcvk
  - Что: cell size как разрешение flow field — сравнение детализации бок о бок и важность для сплайновых входов.
  - Инструменты: xpFlowField (Random flow, режим поля Velocity, Cell Size).
  - Сейчас: тот же принцип в nxFlowField (NeXus 2026.1); xpFlowField по-прежнему актуален.
- **2020-04-23 — Maintenance Training - Dynamics - Constraints - Forces Explained** — https://www.youtube.com/watch?v=8Y5a8_dRgK0
  - Что: тип коллизии Forces в constraints — притяжение и отталкивание, сочетание со связями и маппинг силы по радиусу.
  - Инструменты: xpConstraints (Forces), эмиттер с defined-сеткой.
  - Сейчас: nxConstraints (те же слои) / nxAttract на GPU.

## Sneak Peeks (Beta Access)
- **2020-04-23 — INSYDIUM Beta Access - Sneak Peek - xpBlend** — https://www.youtube.com/watch?v=T5XnNOHEiho
  - Что: превью xpBlend — усреднение цвета, радиуса или физических величин (например, fuel) между соседними частицами, как в смешивающейся краске.
  - Инструменты: xpBlend, xpFluidFX.
  - Сейчас: nxBlend (GPU).
- **2020-04-22 — INSYDIUM Beta Access - Sneak Peek - xpBranch** — https://www.youtube.com/watch?v=ZizmR8dAqDo
  - Что: превью обновлённого xpBranch — curl bending, суб-ветви со своими группами, распределение через сплайн, симметрия — для ригов роста растительности.
  - Инструменты: xpBranch, xpTrail.
  - Сейчас: nxDendrite (NeXus 2026) / nxBioLogic; в стабильном C4D — xpBranch.
- **2020-04-21 — INSYDIUM Beta Access - Sneak Peek - xpFlock** — https://www.youtube.com/watch?v=r38YJ5plcAg
  - Что: превью слоёвых поведений и реакций xpFlock — синяя стая убегает от красных частиц-«акул».
  - Инструменты: xpFlock.
  - Сейчас: nxFlock + nxFlock Reactor.

## VERTEX talks
- **2020-04-20 — Bringing Visual Effects to Motion Graphics - VERTEX 2020 Presentation** — https://www.youtube.com/watch?v=QrtjqCTVh7E
  - Что: живой разбор шота «неоновый город» — жидкий всплеск, «рябящий» пол из MoGraph-кубов, динамика сплайнов, адвекция взрывом и органичный рост огней; рендер в Cycles 4D.
  - Инструменты: xpFluidFX, xpOpenVDBMesher, xpExplosiaFX, xpDynamics (сплайны), MoGraph, Cycles 4D.
  - Сейчас: nxFluids FLIP + nxMesher + nxExplosiaFX (Fused 2025.4); рост — через nxInfectio / nxBioLogic.

## XP Countdown tutorials
- **2020-04-16 — X-Particles shrink-wrap cloth animation, art direct motion & retime the simulati…** — https://www.youtube.com/watch?v=id7ad16ig6k
  - Что: куб превращается в пакет на xpClothFX, который обтягивает «5»; движение арт-директится flow field'ами, ретайм — в эмиттере и xpCache.
  - Инструменты: xpClothFX, xpFlowField, xpCollider tag, xpCache (retime), MoText.
  - Сейчас: ткань на nxConstraints + nxPin / nxDeformer (NeXus 2026.1); в стабильном C4D — xpClothFX.

## Maintenance Training — Dynamics (FlowField & Constraints)
- **2020-04-16 — Maintenance Training - Dynamics - FlowField - Field Modes Explained** — https://www.youtube.com/watch?v=54h5SnIjsnc
  - Что: разница режимов поля direction, velocity и acceleration на примере потока вдоль helix-сплайна; скорость частиц считывается в XP console.
  - Инструменты: xpFlowField (Along Spline flow; Direction/Velocity/Acceleration), XP Console.
  - Сейчас: те же режимы в nxFlowField (NeXus 2026.1); xpFlowField по-прежнему актуален.
- **2020-04-09 — Maintenance Training - Constraints - Connections Explained** — https://www.youtube.com/watch?v=QqFEH8CkB44
  - Что: пружинные связи — радиус и лимит связей при рождении, мягкие тела, distance constraints и кастомные пружины.
  - Инструменты: xpConstraints (Connections, birth/distance), defined-эмиссия, Display Constraints.
  - Сейчас: nxConstraints (те же слои); мягкие тела — через nxMPM Elastic (NeXus 2026.1).

## XP Countdown tutorials
- **2020-04-02 — How to fill objects with water, generate bubbles and mesh fluid sims using X-Par…** — https://www.youtube.com/watch?v=QNsJZhnTzPI
  - Что: первая сцена countdown — структура папок и нейминг, заполнение «6» водой xpFluidFX с прокси-объектом для kill, пузырьки xpFoam и мешинг OpenVDB плюс Boole.
  - Инструменты: xpFluidFX, xpFoam, xpKill, xpOpenVDBMesher, xpCollider tag, C4D Boole, MoText.
  - Сейчас: nxFluids FLIP (Liquid Fill) + nxFoam + nxMesher.

## Maintenance Training — FlowField
- **2020-03-26 — Maintenance Training - Dynamics - FlowField - Flow Modes Explained** — https://www.youtube.com/watch?v=44pjAgy2nB4
  - Что: ячейки и векторы, затем каждый режим потока — default, random, target, shader, spline и surface — и поведение falloff.
  - Инструменты: xpFlowField (flow modes, falloff).
  - Сейчас: nxFlowField (NeXus 2026.1); xpFlowField по-прежнему актуален.

## Sneak Peeks — VERTEX 2020
- **2020-02-28 — VERTEX 2020 - Sneak Peek - xpExplosiaFX** — https://www.youtube.com/watch?v=lhE0y-N9Mq8
  - Что: рендерящийся режим Trails для скорости EFX и новый Upres — low-res симуляция для лукдева превращается в детализированную с тем же движением.
  - Инструменты: xpExplosiaFX (Trails display, Upres).
  - Сейчас: nxExplosiaFX + nxUpres (GPU).
- **2020-02-28 — VERTEX 2020 - Sneak Peek - xpFlock** — https://www.youtube.com/watch?v=1ffSoa_1auo
  - Что: короткое демо стаи рыб со слоёвыми поведениями, убегающей от частиц-акул.
  - Инструменты: xpFlock.
  - Сейчас: nxFlock + nxFlock Reactor.

## Content Repository Tutorials 2019
- **2019-09-27 — Dynamic Web - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=CFEZtK0DmUg
  - Что: тянущаяся липкая паутина между клонированными кубами на constraints, трейлы рендерятся в Cycles 4D (сами трейлы не динамические, поэтому возможны пересечения).
  - Инструменты: xpConstraints, xpTrail, MoGraph Cloner, Cycles 4D.
  - Сейчас: nxConstraints + nxTrail (GPU).
- **2019-07-26 — UV Emission Data - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=hycQlFrHFRU
  - Что: эмиссия с текстурированной плоскости по площади полигонов, анимированная текстура переносится на частицы через UV emission data, затем адвекция и замедление по ключам.
  - Инструменты: xpEmitter (UV emission data), адвекция xpExplosiaFX, Cycles 4D.
  - Сейчас: CPU-путь актуален; в NeXus — nxEmitter + адвекция nxExplosiaFX, документированного аналога UV-данных нет.

## X-Particles Public Release 2019
- **2019-07-01 — New Features - X-Particles Public Release 2019** — https://www.youtube.com/watch?v=HbVKC-ldyUM
  - Что: обзор небольших функций 2019 — xpSplineGrowth анимирует длину/вариацию трейлов (в том числе на текстовых сплайнах), генератор xpDisplayRender рендерится материалами C4D через шейдер MoGraph Color.
  - Инструменты: xpSplineGrowth, xpTrail, xpDisplayRender.
  - Сейчас: на CPU актуально; GPU-трейлы — через nxTrail.
- **2019-06-25 — xpShatter & xpDynamics - X-Particles Public Release 2019** — https://www.youtube.com/watch?v=oY_VKN7D7Yc
  - Что: xpShatter с рекурсивными Voronoi-слоями по времени и по коллизии, точки разреза от объектов или частиц; плюс динамика на частицах для мягких тел, динамических сплайнов и гранул.
  - Инструменты: xpShatter, xpDynamics, xpExplosiaFX.
  - Сейчас: nxShatter + nxMPM (NeXus 2026.1); в стабильном C4D — xpShatter + xpDynamics.
- **2019-06-19 — xpSplash & xpSheeter – X-Particles Public Release 2019** — https://www.youtube.com/watch?v=alvv1XIZGMQ
  - Что: знакомство с xpSplash (всплеск конусным полем скоростей) и xpSheeter (заполняет дыры тонкими плёнками, настройки размера дыр) на симуляции xpFluidFX.
  - Инструменты: xpSplash, xpSheeter, xpFluidFX.
  - Сейчас: nxSplash (Fused 2025.4) + nxSheeter (NeXus 2026) на nxFluids FLIP.

## Content Repository Tutorials 2019
- **2019-06-01 — FluidFX Snow - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=15SS_bITbyg
  - Что: гексагональный снежок скатывается по склону как гранулярная симуляция xpFluidFX, мешится с фильтрами OpenVDB и рендерится в Cycles 4D с подповерхностным рассеиванием.
  - Инструменты: xpFluidFX (granular), xpOpenVDBMesher (filters), Cycles 4D SSS.
  - Сейчас: nxMPM / пресет nxMaterial Snow (NeXus 2026.1); в стабильном C4D — nxFluids SPH Granular.

## VERTEX talks
- **2019-05-22 — VERTEX 2019 - Beyond Expectations by Bob Walmsley** — https://www.youtube.com/watch?v=F3ZXGxqugpk
  - Что: шоурил плюс живые основы — system, emitter, gravity и collider, затем куб с dynamics-тегом, начальным движением и вращением.
  - Инструменты: xpSystem, xpEmitter, xpGravity, xpCollider tag, xpDynamics.
  - Сейчас: твёрдые тела — теги C4D Rigid Body на xpGenerator или nxMPM; единые GPU rigid bodies анонсированы, но не вышли (Nov 2026).

## Content Repository Tutorials 2019
- **2019-05-01 — Sand Advection - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=AANHiU-UfDU
  - Что: логотип X-Particles заполняется гексагональным гранулярным песком, который разносит взрыв xpExplosiaFX через адвекцию.
  - Инструменты: xpFluidFX (granular), xpExplosiaFX (advection), гексагональная эмиссия.
  - Сейчас: nxMPM Sand + nxExplosiaFX (NeXus 2026.1); в стабильном C4D — nxFluids SPH Granular.

## Cycles 4D
- **2019-04-04 — Cycles 4D Build 321 Public Release is out now!** — https://www.youtube.com/watch?v=hqfi4ZNJ8Y4
  - Что: обзор релиза Cycles 4D — real-time preview, переделанный node editor, Cryptomatte, random-walk SSS, векторный/micro-poly displacement и HDR-браузер.
  - Инструменты: Cycles 4D (displacement node, image textures, HDR browser).
  - Сейчас: прямого аналога нет (это рендерер, вне области NeXus).

## Content Repository Tutorials 2019
- **2019-04-01 — Under Water Splash - Content Repository Tutorials 2019** — https://www.youtube.com/watch?v=dJNH4LBxF34
  - Что: выдавленная «X» ныряет в воду, пузырьки разлетаются и всплывают — имитация частицами, адвектированными low-res симуляцией xpExplosiaFX, без жидкостного солвера.
  - Инструменты: xpExplosiaFX (advection, voxel size), xpEmitter, выдавленный текст.
  - Сейчас: адвекция nxExplosiaFX или nxFluids FLIP + пузырьки nxFoam.

## X-Particles Early Access 2019
- **2019-03-27 — X-Particles Early Access Update - xpShatter** — https://www.youtube.com/watch?v=bIvR0R2_Xw8
  - Что: знакомство с xpShatter — осколки от point generator (количество, seed, ручные точки), опции display/цвета/explode/offset, анимация осколков модификаторами, затем настоящая динамика частиц.
  - Инструменты: xpShatter, xpSpin, xpDynamics.
  - Сейчас: nxShatter (NeXus 2026.1; Voronoi/Glass/Wood/Bricks); в стабильном C4D — xpShatter.

## Прочее (без техники)
- 2020-04-17 — VERTEX 2020 - INSYDIUM Vox Pop with Bob Walmsley — https://www.youtube.com/watch?v=Oc9ABSORpa0
- 2019-07-11 — User Accounts – Maintenance Benefits — https://www.youtube.com/watch?v=2h3OpwWUrmI
- 2019-05-20 — VERTEX 2019 - INSYDIUM Vox Pop with Bob Walmsley — https://www.youtube.com/watch?v=YxpLw_m6F7U
