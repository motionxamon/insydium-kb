# Каталог старых видео — часть 1 (2022-09-16 – 2022-12-16)

## INSYDIUM Official Training — Snow Peel
- **2022-12-16 — Snow Peel - Part 1** — https://www.youtube.com/watch?v=0dJbuWbVDRI
  - Что: снежную корку вокруг леденца строят мешингом частиц, снимают её анимированными Boolean-сферами, а там, где корка исчезает, слетают снежные частицы.
  - Инструменты: xpEmitter, xpOpenVDBMesher, C4D Boolean, xpQuestion/xpAction (проверка «внутри объекта»), xpTurbulence, xpWind.
  - Сейчас: nxMesher + nxQuestion на nxEmitter; для физически рассыпающегося снега — nxMPM / пресеты Snow в nxMaterial вместе с nxBind.
- **2022-12-16 — Snow Peel - Part 2** — https://www.youtube.com/watch?v=CDG448vmrm8
  - Что: эффект делят на несколько эмиттеров (поверхность и объём, крупные куски и мелкая пыль), низкое число частиц при эмиссии из объёма лечат через Max Retries, вариативность добавляют data mapping на модификаторах.
  - Инструменты: несколько xpEmitter (Object, объём/поверхность), вкладка Data Mapping, xpTurbulence, xpPainter (прилипшие частицы), xpQuestion.
  - Сейчас: отдельный nxEmitter на каждый слой + вкладка NeXus Mapping и nxFalloff на каждом слое layered nxTurbulence.
- **2022-12-16 — Snow Peel - Part 3** — https://www.youtube.com/watch?v=CqEkvYk4KMc
  - Что: свет в Cycles 4D, кастомный материал липкой карамели на нодах с ремапом градиента и своя геометрия для render-инстансов.
  - Инструменты: Cycles 4D (Principled shader, ремап градиента), Cycles 4D Instance tag.
  - Сейчас: те же приёмы шейдинга в Redshift (Cycles 4D — legacy); инстансы через nxGenerator.
- **2022-12-16 — Snow Peel - Part 4** — https://www.youtube.com/watch?v=mBsW0-e1DZA
  - Что: урезают число частиц на каждом эмиттере, доводят движение снега, кешируют (Boolean отключают для скорости) и настраивают отдельные элементы рендера.
  - Инструменты: xpCache, xpQuestion, xpTurbulence, Cycles 4D.
  - Сейчас: nxCache (Auto Frame Range, Disk Reserve) — workflow по-прежнему актуален.
- **2022-12-16 — Snow Peel - Part 5** — https://www.youtube.com/watch?v=mCUOwczLRWE
  - Что: финальная правка света ради сочности цвета, доводка материалов, сабдивижн Boolean-меша во время рендера и настройки вывода.
  - Инструменты: Cycles 4D Object tag (displacement/subdivision), свет и вывод Cycles 4D.
  - Сейчас: свет Redshift + сабдивижн при рендере; в X-Particles ничего менять не нужно.

## INSYDIUM Official Training — Particle Tree
- **2022-12-16 — Particle Tree - Part 1** — https://www.youtube.com/watch?v=dryt88_zKnc
  - Что: первая из трёх систем ёлки из частиц — частицы с рёбер helix-сплайнов закручиваются вверх под flow field и turbulence, затем размер правят на этапе рендера.
  - Инструменты: xpEmitter (Object, рёбра), xpFlowField, xpTurbulence, xpSpeed, Cycles 4D Instance tag.
  - Сейчас: nxEmitter со сплайнов + nxFlowField / nxWarp Helix (режим Guide) + nxTurbulence.
- **2022-12-16 — Particle Tree - Part 2** — https://www.youtube.com/watch?v=eGSVsEtIPM0
  - Что: плоская лента частиц под линейным flow field, которую затем оборачивают вокруг helix деформером C4D Spline Wrap; плюс эмиттеры снега и шаров.
  - Инструменты: xpEmitter (куб), xpFlowField (слой To Spline), C4D Spline Wrap, xpTrail.
  - Сейчас: nxWarp Helix или Path (режим Flow) делает обёртку нативно; стабильная альтернатива — nxFollowGeo.
- **2022-12-16 — Particle Tree - Part 3** — https://www.youtube.com/watch?v=p2Pc6TPpiQo
  - Что: доводят sim со spline wrap, забирают настройки рендера у первой системы, собирают процедурные материалы блестящих и стеклянных шаров в Cycles 4D и делают тестовый рендер.
  - Инструменты: Cycles 4D (Principled shader, соло нод), xpCache.
  - Сейчас: материалы пересобрать в Redshift; симуляция переносится на nxWarp Helix.
- **2022-12-16 — Particle Tree - Part 4** — https://www.youtube.com/watch?v=e0GeVgSBOxo
  - Что: система тонких «дымных» деталей — частицы эмитятся с sweep вокруг helix по noise-текстуре, спиралью идут вниз вдоль сплайна через flow field и проигрываются в обратную сторону.
  - Инструменты: C4D Sweep, xpEmitter (эмиссия по shader/текстуре), xpFlowField (слой Along Spline), xpTurbulence, xpCache (реверс).
  - Сейчас: эмиссия по shader в nxEmitter + nxFlowField / nxWarp Helix; реверс через проигрывание cache.
- **2022-12-16 — Particle Tree - Part 5** — https://www.youtube.com/watch?v=8VOG4fkZUMY
  - Что: три системы сводят вместе и ретаймят сдвигом проигрывания cache, затем финализируют вывод рендера.
  - Инструменты: xpCache (offset, hold), вывод Cycles 4D.
  - Сейчас: frame range / offset в nxCache — по-прежнему актуально.

## INSYDIUM Official Training — NeXus 2022
- **2022-11-09 — nxConstraints Tutorial 2022** — https://www.youtube.com/watch?v=yTwVv5s8BGU
  - Что: частицы на анимированном разделённом кубе связываются пружинными констрейнтами, которые рвутся под нагрузкой (эффект разрыва); финальный вид добирают другими модификаторами NeXus.
  - Инструменты: xpEmitter (оранжевый/GPU), nxConstraints (радиус поиска, макс. число связей, жёсткость, разрыв), nxTurbulence.
  - Сейчас: nxConstraints поколения G3 (те же слои) + nxPin для закрепления; в 2026.1 nxDeformer добавляет разрыв меша.
- **2022-11-02 — nxPush Tutorial 2022** — https://www.youtube.com/watch?v=vG4zYLbhuMk
  - Что: GPU-расталкивание частиц друг от друга для плотных стилизованных sim, анимация радиуса через nxScale и noise-поле, масштабирование до песка в реальном времени.
  - Инструменты: xpEmitter (смена цвета CPU→GPU), nxPush, nxScale (поле по shader), C4D Fields.
  - Сейчас: nxPush по-прежнему актуален; для физического песка — nxMPM / пресеты Sand в nxMaterial.
- **2022-10-20 — nxFluids Tutorial 2022** — https://www.youtube.com/watch?v=JCd4i0xZDbo
  - Что: всплеск у логотипа — вода вырывается из выдавленной шестерёнки, кружит вокруг неё и разлетается наружу; всё режиссируется в реальном времени на GPU.
  - Инструменты: nxFluids (PBD), nxTurbulence, nxAttract, nxRotate, nxExplode, nxDrag.
  - Сейчас: nxFluids FLIP/APIC + nxMesher для вида жидкости (PBD остаётся); вращение — nxWarp Helix.

## Premium Training — Ivy Growth
- **2022-09-16 — Ivy Growth - 01 - Branching System** — https://www.youtube.com/watch?v=YbNQ7msv6-c
  - Что: краткая анатомия растения, затем иерархия ветвления «главный стебель / боковые побеги / черешки», ползущая по поверхностям.
  - Инструменты: xpBranch (sub-branches), xpFollowSurface, xpTrail, xpAvoid.
  - Сейчас: nxDendrite (ветви) + nxFollowGeo; xpBranch остаётся путём на CPU.
- **2022-09-16 — Ivy Growth - 02 - Tropism** — https://www.youtube.com/watch?v=bAYTV6vpzB0
  - Что: случайные изгибы заменяют управляемым ростом к источнику света и в обход препятствий.
  - Инструменты: xpBranch, xpDirection, xpAvoid, xpFollowSurface.
  - Сейчас: nxDendrite + nxAttract / nxAvoid; для дифференциального роста — nxBioLogic.
- **2022-09-16 — Ivy Growth - 03 - Leaves** — https://www.youtube.com/watch?v=w3g0PjQk8Co
  - Что: простые плоскости-листья ставят на концы веток с правильной позицией, ориентацией, масштабом и разворачиванием, плюс строят геометрию веток.
  - Инструменты: xpGenerator, деформеры C4D на плоскостях листьев, UVW tags, xpSplineMesher.
  - Сейчас: nxGenerator (или Taiao toLeaf для ботанических листьев).
- **2022-09-16 — Ivy Growth - 05 - Rendering** — https://www.youtube.com/watch?v=Q6Fs8GOHsjs
  - Что: настройка камер с safe frames и focus nulls, свет солнца/окружения и полупрозрачный shader листьев с вариацией на каждый лист.
  - Инструменты: Cycles 4D (камера, translucency shader), камеры C4D.
  - Сейчас: аналоги в Redshift; в X-Particles ничего не меняется.
- **2022-09-16 — Ivy Growth - 06 - Compositing** — https://www.youtube.com/watch?v=ybC7vFu8VD0
  - Что: грейдинг, bloom и флейры в After Effects с использованием Cryptomatte-пассов из Cycles 4D.
  - Инструменты: Cycles 4D Cryptomatte, After Effects.
  - Сейчас: по-прежнему актуально (Cryptomatte в Redshift).

## Premium Training — Drawing with Particles
- **2022-09-16 — Drawing with Particles - 01 - Methods** — https://www.youtube.com/watch?v=wPDMjtNChWA
  - Что: сравнение способов рисовать граффити-путь частицами: эмиссия со сплайна, follow-spline и spline-flow, и их ограничения на многосегментных сплайнах.
  - Инструменты: xpEmitter (quick tool Emit from Object), xpFollowSpline, xpSplineFlow.
  - Сейчас: nxFollowGeo (multi-spline) или nxWarp Path.
- **2022-09-16 — Drawing with Particles - 04 - Graffiti** — https://www.youtube.com/watch?v=ZOa2ZU6Ot6I
  - Что: свободное граффити баллончиком по контейнерам — частицы прилипают к поверхностям и пишут wet maps, экспорт через Alembic.
  - Инструменты: xpEmitter на баллончике, xpCollider tag, xpWetMap tag (vertex maps), экспорт Alembic, Xpresso.
  - Сейчас: adhesion в nxCollider + режим Wet в nxFalloff → vertex maps через nxFalloffMap (C4D).
- **2022-09-16 — Drawing with Particles - 05 - Rendering & Compositing** — https://www.youtube.com/watch?v=fMTz2EcSS04
  - Что: wet-map vertex maps и цвет частиц выводят в материалы Cycles 4D (с translucency) и композят в After Effects.
  - Инструменты: Cycles 4D (ноды vertex map и particle data), After Effects.
  - Сейчас: Redshift, читающий vertex maps / vertex color из nxFalloffMap.

## Premium Training — Logo Form
- **2022-09-16 — Logo Form - 01 - xpCover & xpInherit** — https://www.youtube.com/watch?v=hbleYqDBiiA
  - Что: логотип проявляют, покрывая его геометрию частицами или наследуя позиции; показано, как на результат влияет порядок точек.
  - Инструменты: xpCover, xpInherit, xpTurbulence.
  - Сейчас: nxCover; у xpInherit нет указанного nx-аналога — оставить на CPU или приблизить через nxCover / nxAttract.
- **2022-09-16 — Logo Form - 03 - Streams** — https://www.youtube.com/watch?v=YXz1wTcyQf0
  - Что: спиральные струи-трейлы влетают и собирают логотип одновременно с реверсным cache схлопывающейся туманности.
  - Инструменты: xpTrail, xpFlowField, xpFollowSpline / xpSplineFlow, xpCover (ближайшая точка поверхности), xpCache (offset, hold).
  - Сейчас: nxTrail + nxWarp Helix + nxCover.
- **2022-09-16 — Logo Form - 04 - Tweaks & Rendering** — https://www.youtube.com/watch?v=tPZLKDkndEA
  - Что: усиливают спираль туманности, перекешируют, возвращают наследование цвета, затем ставят свет и шейдинг частиц (металлические блики) в Cycles 4D.
  - Инструменты: xpFlowField (сила To Spline), xpInherit, xpTrail, xpCache, Cycles 4D.
  - Сейчас: nxFlowField / nxWarp Helix; шейдинг в Redshift.
- **2022-09-16 — Logo Form - 05 - Compositing** — https://www.youtube.com/watch?v=jfYXZe2VS9Y
  - Что: композ в After Effects — pixel motion blur, тонирование и правка непрозрачности пасса мерцания.
  - Инструменты: After Effects.
  - Сейчас: по-прежнему актуально.

## Premium Training — Fireworks
- **2022-09-16 — Fireworks - 01 - Anatomy of a Firework** — https://www.youtube.com/watch?v=ruePL0LBHDo
  - Что: разбор реальных типов фейерверков, затем управляемый подъём снаряда по сплайну траектории.
  - Инструменты: xpEmitter, xpFollowSpline, xpTurbulence, xpTrail.
  - Сейчас: nxFollowGeo / nxWarp Path + nxTrail.
- **2022-09-16 — Fireworks - 02 - Lift, Break & Shape** — https://www.youtube.com/watch?v=pPSUS_qYfuk
  - Что: разрыв — звёзды спавнятся из снаряда со смещением по радиусу, им задают форму и изолируют в отдельной системе, добавляют трейлы.
  - Инструменты: xpSpawn, xpQuestion, xpTurbulence, xpTrail, опции изоляции системы.
  - Сейчас: nxSpawn (On Death / At Age) + nxTrail.
- **2022-09-16 — Fireworks - 03 - The Display** — https://www.youtube.com/watch?v=bmGuzKj4vk8
  - Что: строят стартовую площадку и шоу из множества фейерверков с таймингом через user data в Xpresso (ignition, travel time).
  - Инструменты: Xpresso, xpSpawn, xpQuestion, xpFollowSpline, xpTrail.
  - Сейчас: Xpresso по-прежнему работает; тайминг отдельных залпов — через nxSpawn / nxQuestion.
- **2022-09-16 — Fireworks - 04 - Lighting & Materials** — https://www.youtube.com/watch?v=ZcgFQWPagqo
  - Что: пролёт камеры, силуэты деревьев и светящиеся материалы фейерверков через node-группу range mapping.
  - Инструменты: Cycles 4D (группа range mapping на math-нодах).
  - Сейчас: Redshift (встроенный range remap).

## Premium Training — Sci-Fi FUI
- **2022-09-16 — Sci-Fi FUI - 01 - The Leak** — https://www.youtube.com/watch?v=vsIISOBfuGU
  - Что: заражённая слизь растекается в чашке Петри — эмиссия регулярной сеткой, fluid-решение и гладкая коллизия/меш через OpenVDB.
  - Инструменты: xpEmitter (regular/hexagonal), xpFluidFX, xpFlowField, xpKill, xpOpenVDBMesher (adaptivity).
  - Сейчас: nxFluids FLIP с высокой вязкостью / non-Newtonian + nxMesher.
- **2022-09-16 — Sci-Fi FUI - 02 - FUI** — https://www.youtube.com/watch?v=si9mAqLRfPg
  - Что: cache слизи обрезают и экспортируют в Alembic под displacer'ы, затем строят HUD-графику, которая следит за частицами через Xpresso.
  - Инструменты: xpCache, экспорт Alembic, xpFlowField, Xpresso.
  - Сейчас: вывод Alembic в nxCache; трекинг через Xpresso без изменений.

## Premium Training — Infectio
- **2022-09-16 — Infectio - 03 - Spores** — https://www.youtube.com/watch?v=OLeYN-Am5TY
  - Что: ворсистые споры растут только из заражённых частиц плесени — через вероятностный spawn и трейлы.
  - Инструменты: xpInfectio, xpSpawn (управляется action), xpQuestion, xpTrail, xpFlowField, xpTurbulence.
  - Сейчас: nxInfectio + nxSpawn / Spawn в nxQuestion + nxTrail.
- **2022-09-16 — Infectio - 04 - Rendering** — https://www.youtube.com/watch?v=QzACkgaJHhs
  - Что: камеры, рендер Cycles 4D на нескольких GPU, случайный цвет частиц и hair-материалы для трейлов с группой range mapping.
  - Инструменты: Cycles 4D (рендер hair/трейлов, camera tag).
  - Сейчас: Redshift (hair из сплайнов nxTrail).

## Maintenance Training — Fluids
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Cloth Interaction** — https://www.youtube.com/watch?v=to0ddsJ8QTA
  - Что: вода рвёт одну ткань и собирается лужей в другой; с тканью связываются только FluidFX или PBD, и ткань должна считаться раньше жидкости.
  - Инструменты: xpClothFX, xpFluidFX / xpFluidPBD.
  - Сейчас: GPU-ткани пока нет — CPU xpClothFX; единая GPU-динамика ткани и связки анонсирована для следующей беты NeXus.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Controlling Flows** — https://www.youtube.com/watch?v=V0kXecaPKhk
  - Что: стилизованный продуктовый шот — PBD для чистой струи против FLIP для брызг и деталей вдоль сплайн-пути.
  - Инструменты: xpFluidPBD, xpFluidFLIP, xpSplineFlow, xpTurbulence, xpSheeter, xpFoam.
  - Сейчас: nxFluids FLIP + nxFollowGeo / nxWarp Flow, nxFoam, nxSheeter.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Mid to Large Scale** — https://www.youtube.com/watch?v=SlAvrz-mI6U
  - Что: сравнение всех трёх CPU-решателей на бассейне со всплеском и водопаде, включая точность против времени симуляции.
  - Инструменты: xpFluidFX, xpFluidPBD, xpFluidFLIP, xpCollider.
  - Сейчас: nxFluids FLIP/APIC.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Glass Fill** — https://www.youtube.com/watch?v=OkigcUDam4I
  - Что: налив в стакан в реальном масштабе; полосатость эмиссии и слишком сильную гравитацию на малом масштабе лечат увеличением subframes.
  - Инструменты: xpFluidFX, xpEmitter (hexagonal), subframes в настройках проекта X-Particles.
  - Сейчас: nxFluids FLIP/APIC с Liquid Fill; substeps — в NeXus Project Settings.
- **2022-09-16 — Fluids - Series 1 - Solver Choice: Macro Splashes** — https://www.youtube.com/watch?v=OEmGpUKXScQ
  - Что: корончатый всплеск в духе скоростной фотосъёмки и продуктовые всплески; сравнение поведения коллизий в FluidFX и FLIP.
  - Инструменты: xpSplash, xpSheeter, xpFluidFX, xpFluidFLIP.
  - Сейчас: nxSplash (корона) + nxFluids FLIP + nxSheeter.
- **2022-09-16 — Fluids - Series 2 - Intro to FluidPBD** — https://www.youtube.com/watch?v=w647Eqzx38g
  - Что: настройки решателя PBD и свойств жидкости — решение без домена внутри стакана.
  - Инструменты: xpFluidPBD, xpGravity, xpCollider.
  - Сейчас: nxFluids PBD (с 2026.1 Beta 2 силы больше не зависят от размера частиц).
- **2022-09-16 — Fluids - Series 2 - Intro to FluidFX: Solver Settings** — https://www.youtube.com/watch?v=jmMXWgtp4ys
  - Что: пресеты точности FluidFX, контроль плотности, внутреннее/внешнее давление и damping на примере бака со сбросом воды.
  - Инструменты: xpFluidFX, xpEmitter (hexagonal box).
  - Сейчас: nxFluids SPH (или FLIP для больших объёмов).
- **2022-09-16 — Fluids - Series 2 - Intro to FluidFX: Emitter Settings** — https://www.youtube.com/watch?v=_-gpqcjuA5c
  - Что: fluid-данные на эмиттере — капли за счёт поверхностного натяжения, вязкие жидкости и сыпучие sim в вибрирующем сосуде.
  - Инструменты: xpEmitter Extended Data → Fluid, xpFluidFX.
  - Сейчас: nxFluids tag на эмиттере / Mixer; сыпучее → песок в nxMPM.
- **2022-09-16 — Fluids - Series 3 - Intro to Sheeter** — https://www.youtube.com/watch?v=l6k_stWo0_0
  - Что: грубый всплеск на лимоне превращают в тонкие плёнки жидкости, подбирая пороги размера, плотности, скорости и возраста.
  - Инструменты: xpSheeter, xpFluidFX, xpCollider.
  - Сейчас: nxSheeter (2026) / sheeting во FLIP в nxFluids.
- **2022-09-16 — Fluids - Series 3 - Intro to Wave and Foam** — https://www.youtube.com/watch?v=dEsr4yqXHEM
  - Что: накатывающий прибой на меше пляжа с пеной и брызгами из частиц.
  - Инструменты: xpWave, xpFoam, xpFluidFX, xpKill.
  - Сейчас: пляж в nxOcean (swash/surf) или nxWave + nxFoam с FLIP.
- **2022-09-16 — Fluids - Series 4 - Teacup Splash Build** — https://www.youtube.com/watch?v=pMrAb9P7Wpk
  - Что: корончатый всплеск в чайной чашке; основной объём жидкости ограничивают тонким слоем ради ряби.
  - Инструменты: xpSplash, xpSheeter, xpFluidFX, xpCollider.
  - Сейчас: nxSplash + nxFluids FLIP.

## Maintenance Training — ExplosiaFX
- **2022-09-16 — ExplosiaFX - The Basics - Intro to the EFX Solver** — https://www.youtube.com/watch?v=bpTUYD_Hkf8
  - Что: основы воксельного решателя — source tag, каналы (fuel, heat, smoke), адвекция и адаптивные границы.
  - Инструменты: xpExplosiaFX, xpExplosiaFX Source tag.
  - Сейчас: nxExplosiaFX (источники — во вкладке Sources).
- **2022-09-16 — ExplosiaFX - The Basics - Particle Advection** — https://www.youtube.com/watch?v=f7_u0G28cAw
  - Что: частицы переносятся скоростью дыма, красятся по температуре и вычищаются по fuel через questions.
  - Инструменты: xpExplosiaFX, xpEmitter, xpQuestion/xpAction.
  - Сейчас: nxExplosiaFX; адвекцию частиц проверить в 2026.1, иначе остаться на CPU EFX.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Object Sources** — https://www.youtube.com/watch?v=vWqea_xAu-o
  - Что: объекты-источники с масками из текстур, selection'ов и vertex maps, передача скорости/цвета, сплайны как источники и эмиссия только в зоне контакта.
  - Инструменты: xpExplosiaFX Source tag.
  - Сейчас: nxExplosiaFX с эмиссией из объектов, сплайнов, vertex maps и shader'ов.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Particle Sources** — https://www.youtube.com/watch?v=ocB802N_bKk
  - Что: частицы как источники дыма передают скорость, цвет и давление — так делают взрывы.
  - Инструменты: xpExplosiaFX Source tag на xpEmitter.
  - Сейчас: частицы-источники в nxExplosiaFX.
- **2022-09-16 — ExplosiaFX - Tags in Depth - Colliders** — https://www.youtube.com/watch?v=mJ919p6x2gE
  - Что: коллайдеры, перенаправляющие дым, заполнение объектов, передача скорости от анимированных коллайдеров и сценарий с высоким давлением.
  - Инструменты: xpExplosiaFX Collider tag.
  - Сейчас: коллизии в nxExplosiaFX.
- **2022-09-16 — ExplosiaFX - Simulation Settings - Simulation Scale & Speed** — https://www.youtube.com/watch?v=NR9IfLLhX64
  - Что: меняют видимый размер sim без изменения вокселей и анимируют скорость симуляции, чтобы замедлить ударную волну.
  - Инструменты: xpExplosiaFX (Sim Scale, Sim Speed).
  - Сейчас: nxExplosiaFX (проверить его настройки масштаба/скорости).
- **2022-09-16 — xpExplosiaFX - Candle & Whispy Smoke** — https://www.youtube.com/watch?v=V8Y7nH2b5Zc
  - Что: пламя свечи и тонкий дым от фитиля на движущемся подсвечнике, эффект горения и зацикленное затухание.
  - Инструменты: xpExplosiaFX + Source tag, xpVertexMap, xpTrail.
  - Сейчас: nxExplosiaFX + nxWarp на дыме; связка с Pyro в C4D 2025.3+.
- **2022-09-16 — ExplosiaFX - Simulation Tutorials - Explosions** — https://www.youtube.com/watch?v=R35x1j1AIa8
  - Что: быстрые частицы-источники с высоким давлением для взрыва по таймеру у стены, коллайдеры на всю сцену и рвущаяся тканевая табличка.
  - Инструменты: xpExplosiaFX, xpEmitter, xpTrail, xpCollider, xpClothFX (разрыв).
  - Сейчас: nxExplosiaFX (+ nxShatter для обломков); ткань по-прежнему на CPU xpClothFX.
- **2022-09-16 — ExplosiaFX - Rendering Colorful Explosions** — https://www.youtube.com/watch?v=Mj23NfHIDhY
  - Что: цветовой канал EFX читают в объёмный материал Cycles 4D через point density, правят его HSV и строят маску.
  - Инструменты: xpExplosiaFX (канал Color), нода Cycles 4D Point Density.
  - Сейчас: VDB из nxExplosiaFX в Redshift (дефолтный smoke-материал) с использованием цветовой сетки.

## Прочее (без техники)
- INSYDIUM Fused - Release Update OUT NOW! - Sept '22 — https://www.youtube.com/watch?v=D3_Cr2oWWW8
- Premium Training - Ivy Growth - Introduction — https://www.youtube.com/watch?v=n9Nrp8qRCns
- Premium Training - Logo Form - Introduction — https://www.youtube.com/watch?v=lgQrcXsk9y0
- Premium Training - Drawing with Particles - Introduction — https://www.youtube.com/watch?v=awBukPjcgkE
