# Индекс эффектов — «Хочу сделать…» → чем это делать

**Правило «сначала новое»:** для любого эффекта сначала загляни в таблицу «Newest way» в `references/whats-new.md` (бета-объекты NeXus 2026.1: nxMPM, nxMaterial, nxOcean, nxWarp, nxShatter, nxSpawn, nxBioLogic, nxDeformer, nxPin, nxBind, nxFluid2D, nxScatter, связка Pyro/нативных частиц в C4D 2025.3+). Ниже перечислены все варианты.

C4D-CPU = классический X-Particles · GPU = NeXus (`nx*`, C4D или Blender) · Fused = MeshTools/TerraformFX/Taiao/Jidou. Имена файлов указаны относительно `references/`. Рецепты (по одному на каждый Top Tip Tuesday / туториал, сначала новые, у каждого есть заметка о новом аналоге) собраны в `recipes/README.md` — ищи там grep'ом по имени инструмента.

## Жидкости и флюиды
- Налив воды / брызги / заполнение ёмкости → **GPU** nxFluids FLIP/APIC (большие объёмы) или PBD (мелкие, стилизованные) + nxMesher (Zhu-Bridson) + nxFoam → `c4d/nexus-core.md`, `c4d/nexus-dynamics-logic.md`. В Blender в один клик: nxLiquid → `blender/nexus-blender.md`. CPU: xpFluidFLIP / xpFluidFX + xpOpenVDBMesher → `c4d/xp-generators-dynamics.md`.
- Мёд / вязкая жидкость / слизь → nxFluids PBD/SPH Viscosity + слой Viscosity в nxConstraints (умеренная жёсткость, больше итераций); Blender: FLIP non-Newtonian.
- Смешивание красок / двухцветные жидкости → отдельный тег nxFluids на каждый emitter + **nxBlend** (color) → `c4d/nexus-modifiers.md`.
- Масло + вода, вода + песок → отдельные теги nxFluids на каждый emitter (для песка SPH Granular).
- Океан / волны / береговая линия → Blender/2026: **nxOcean** (+связка с FLIP); C4D-CPU: xpOcean; волны внутри жидкости: nxWave; бурная, перекатывающаяся вода: nxVorticity.
- Белая вода / пена / пузыри / водяная пыль → слои nxFoam (Simulation Bounds = домен жидкости).
- Всплеск при ударе → nxSplash (Start Time = кадр удара).
- Тающий объект → nxFluids + nxGravity (таяние по falloff/возрасту), либо xpDeformer/nxDeformer; MPM: переход elastic→liquid через Mixer (Blender 2026.1).
- Конденсат / капли на стекле → QuickTools Condensation; nxConstraints Surface Tension.
- 2D-чернила в UV-карте / интерактивный краситель → nxFluid2D (2026.1).

## Дым, огонь, взрывы
- Дым / огонь / костёр / свеча → **nxExplosiaFX** (GPU) → `c4d/nexus-core.md`; CPU: xpExplosiaFX + тег Source → `c4d/xp-generators-dynamics.md`. Быстрый старт: QuickTools EFX Basic Flame / Camp Fire.
- Взрыв → nxExplosiaFX с Pressure + Fuel Frame Limits, Gas Expansion; обломки добавить через xpShatter/nxShatter.
- Дым, который деформируют объекты / турбулентность → слои Dynamics (Turbulence, Vorticity, Wind) + подвкладка Modifiers (nxDirection, nxAttract).
- Искры / пыль, которые несёт дым → подвкладка Particle Advection.
- Рендер дыма → кэш в OpenVDB (xpCache / nxCache) → volume в рендере; в бете C4D 2026.1 появился дефолтный материал дыма для Redshift.

## Разрушения, ткань, мягкие тела
- Раскол / трещины / рекурсивное разрушение → xpShatter (Volume/Surface, рекурсивные слои, триггер Collision + xpBullet) или nxShatter (2026.1).
- Твёрдые тела → теги xpBullet Rigid Body / Collider, xpBulletConstraints (шарниры, разрушаемые связи).
- Ткань, флаги, разрывы, **вмятины на металле** → xpClothFX (Create Cloth) + тег xpCloth (Plasticity, Tearing) → `c4d/xp-generators-dynamics.md`. Альтернатива на GPU: nxMPM Metal/Elastic (Blender 2026.1).
- Желе / мягкое тело → связи Birth в nxConstraints (жёсткость, разрыв) или тег xpDynamics; nxMPM Elastic.
- Песок, снег, гравий, сыпучка → nxFluids SPH Granular (substeps до 30) или nxMPM Sand/Snow; слой friction для горок.
- Осыпание / шелушение / распад → nxInfectio (Infected Lifespan 1 кадр) + nxTurbulence; эмиттеры, прилипшие к источнику, + nxKill.

## Движение частиц и моушн-графика
- Частицы складываются в логотип/форму, морфинг между формами → nxCover (Sequence / Time to Target) или xpCover; xpInherit (копирует построение другого эмиттера).
- Движение по сплайнам / спиралям / трубкам → nxFollowGeo в режиме spline (Twists, Offset) или xpFollowSpline / xpSplineFlow.
- Ползание по поверхностям / рёбрам → nxFollowGeo в режиме surface/edge, xpFollowSurface.
- Завитки curl-noise → nxTurbulence (Curl) / QuickTools Curl Noise.
- Стаи, птицы, рыбы, погони → nxFlock (поведения + реакторы Pursuit/Flee).
- Орбиты / гравитационные колодцы → nxGravity Effect Towards, xpGravity Newton.
- Торнадо / вихрь → xpVortex (Helix), nxRotate.
- Линии странных аттракторов → xpStrangeAttractors + xpTrail.
- Схемы / печатные платы / сетевые пути → xpNetwork + xpTrail; рост через mtShortestPath.
- Появление / растворение / распад из частиц → nxInfectio, nxKill с falloff, nxScale по возрасту.
- Частицы прилипают / собираются на объекте → nxSticky / xpSticky, xpCollider Connect on Collision.
- Спид-рампы на симуляциях → закэшировать, затем xpCache/nxCache Retiming → Custom spline.
- Повысить детализацию лёгкой симуляции → nxUpres (2 k → 80 k частиц).
- Частицы от аудио → xpSound, xpSoundDisplacement, xpSoundShader.
- Текстовые спрайты / счётчики → xpSprite Text + xpText.

## Шлейфы, линии, рост
- Шлейфы частиц (извилистые, естественные) → xpTrail + **xpTrailDeformer** (Top Tip #1) → xpSplineMesher / Sweep / Hair; в Blender nxTrail Splines.
- Плексус / связи с ближайшими → xpTrail Algorithm Nearest by Distance + xpPlanarMesher; nxConstraints Distance + Display Constraints.
- Молнии → xpElektrix, **mtSplineFX** (ответвления), xpBranch.
- Лазеры / отражающиеся лучи света → **mtRayline** (шейп X-Particles для лучей из частиц).
- Ветки, корни, усики, деревья → xpBranch + Sub-Branch, xpTendril, nxDendrite, Taiao toTree (рост внутри объёма логотипа).
- Клеточный / коралловый рост / реакция-диффузия → xpCellAuto (DLA), nxBioLogic (2026.1).
- Распускающийся цветок из шлейфов частиц → nxFollowGeo/nxTurbulence + шлейфы (рецепт).

## Меш / процедурное моделирование (MeshTools)
- Рост техно-панелей / рост инсетов → mtInset, управляемый анимированным полем/шейдером.
- Разворачивание оригами → mtPolyFold. Растворение полигонов → mtPolyScale. Оболочки/толщина → mtShellGen. Гриблы → стек mtInset + mtShellGen + mtSubDivider.
- Тун / контурные линии → mtEdgeSpline Outline/Contour.
- Фракталы → mtFractal. Ремеш под симуляции → mtRemesh.
- Динамические MeshTools (падающие куски инсетов) → стек MeshTools + xpDynamics.

## Ландшафт и природа
- Горы, эрозия → TerraformFX tfNoise + tfErosionHydraulic (Inertia) + tfHighpass → `c4d/terraformfx.md`.
- Реки, дороги, камни → tfRiver (+tfRiverExport), tfRoad, tfRock. Логотип → ландшафт: tfTrace.
- Анимированный «текущий» ландшафт → операторы Time Dependent / анимированный offset у tfNoise («Terrain Flow»).
- Снег на вершинах / мох в расщелинах → вкладка Topology у эмиттера (высота/уклон/кривизна) или слои шейдера Terrain.
- Трава, растения, деревья, цветы, ветер → Taiao toGrass / toPlant / toTree / toFlower → `c4d/taiao-jidou.md`. Падающие листья → вывод X-Particles у toPlant.
- Дождь с брызгами → xpRainRig / QuickTools Simple Rain + spawn через xpCollider; мокрые поверхности → xpWetMap.

## Помощники анимации (Jidou)
- Дрожание/пульсация любого параметра → jdDriver (Noise/Wave/Time). Перемещения A→B → jdAniMate. Пути камеры → jdFlowCam. Катящиеся объекты → jdGeoRoll.

## Пайплайн
- Cache / VDB / Alembic → `c4d/xp-system-cache-control.md`, `blender/nexus-blender.md` (nxCache).
- Дублировать/переиспользовать закэшированные симуляции для наполнения сцены → смещения/ретайм воспроизведения в xpCache, несколько объектов кэша.
- Рендер в Redshift/Octane/Cycles → `c4d/xp-utilities-render.md`; в Blender: Create Point Cloud + нода Particle Info.
- Конвертация старых CPU-сцен → nxConvert (бета C4D 2026.1) + `legacy-vs-nexus.md`.

- `references/tools/` — карточки инструментов: по странице на инструмент (79 шт.) со всеми настройками и значениями из видео, подводными камнями и всеми рецептами. Начинай отсюда для вопросов «как настроить nxMPM / nxFLIP / xpTrail».
