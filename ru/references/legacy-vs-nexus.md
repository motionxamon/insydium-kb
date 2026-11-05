# Legacy (CPU `xp*`) vs NeXus (GPU `nx*`) — к какому поколению относится совет?

Проверено 2026-11-03 по docs.insydium.ltd. Используйте этот файл всякий раз, когда в рецепте, туториале или сцене пользователя упоминается объект, — сначала определите, к какому **поколению** он относится.

## Три поколения
| Пок. | Годы | Как выглядит в сцене | Примечания |
|---|---|---|---|
| **G1 — X-Particles CPU** | до X-Particles 4 (2017) → 2022 | `xpSystem` → `xpEmitter` + `xp*` модификаторы / динамика | Полностью поддерживается и в Fused 2025. Управление через систему Questions/Actions. |
| **G2 — NeXus внутри X-Particles** | 2022 (Fused/X-Particles 2022+) → Fused 2025 | по-прежнему `xpEmitter`, но с `nx*` модификаторами/солверами **иконка эмиттера становится оранжевой** (GPU, Vulkan) | GPU и CPU могут сосуществовать в одной сцене; каждый эмиттер считается там, где живут его модификаторы. Большинство Top Tip Tuesday 2022-2025 со словом «NeXus» в названии — это G2. |
| **G3 — NeXus 2026 (отдельный набор объектов)** | Blender 2026.0 (июль 2026); **публичная бета C4D 2026.1 (октябрь 2026)** | `nxSystem`, `nxEmitter`, `nxCache`, `nxGroup`, `nxCollider`… тот же движок и параметры в C4D и Blender | Для C4D нужен R19+ (нативная связка с particle/Pyro — 2025.3+) и установленный X-Particles. **nxConvert** (C4D Beta 3) переводит xpEmitter’ы/группы в NeXus за один шаг с возможностью отмены. nx-модификаторы могут работать и с обычными xpEmitter’ами. Бета — возможны изменения. |

Практическое правило для ответов: **для всего тяжёлого (жидкости, дым, миллионы частиц) предпочитайте G2/G3 (`nx*`)**; оставайтесь на G1, если у функции нет nx-аналога (Bullet rigid bodies, xpClothFX, трюки на xpTrail с xpBranch, xpSprite, Questions по CPU-данным, Thinking Particles, звуковые модификаторы…). В Blender есть только NeXus — любой рецепт G1 нужно переводить по таблице ниже.

## Соответствие объектов
| CPU (G1) | GPU (G2 C4D) | NeXus 2026 / Blender (G3) | Что учесть при переводе |
|---|---|---|---|
| xpSystem | xpSystem | **nxSystem** (папки) / NeXus Hierarchy (Blender) | Blender: порядок вычисления = порядок в иерархии |
| xpEmitter | xpEmitter (оранжевый) | **nxEmitter** | В Blender добавлены Liquid Fill/Flow, point clouds, splats |
| xpCache | xpCache | **nxCache** | Blender: Alembic, PLY, Disk Reserve |
| xpGroup | xpGroup | nxGroup | |
| xpCollider tag | xpCollider tag | объект **nxCollider** | Blender: Global включён по умолчанию |
| xpQuestion + xpAction | **nxQuestion** (Question/Action/Loop/Variable/Script GLSL) | nxQuestion (+ Quill, Sleep/Bind) | CPU questions ненадёжно управляют GPU-эмиттерами — пересоберите в nxQuestion |
| вкладка Data Mapping | вкладка NeXus Mapping | то же | источники пересекаются (Age, Speed, Radius…) |
| C4D Fields / falloffs | **nxFalloff** | nxFalloff (+ nxFalloff Modifier, Wet/Curvature/AO) | |
| xpTurbulence | nxTurbulence | nxTurbulence | наследование движения ≈ Curl Blend / Curl Add |
| xpAttractor | nxAttract | nxAttract | |
| xpAvoid | nxAvoid | nxAvoid | |
| xpCover | nxCover | nxCover | |
| xpDirection | nxDirection | nxDirection | |
| xpDrag | nxDrag | nxDrag | |
| xpExplode | nxExplode | nxExplode | |
| xpFlock (динамика) | nxFlock (модификатор) | nxFlock | реакции в C4D = дочерние объекты «nxFlock Reactor» |
| xpFollowSpline / xpFollowSurface / xpSplineFlow | **nxFollowGeo** | nxFollowGeo | один объект; в режиме сплайна есть Twists/Offset |
| xpGravity (Standard/Newton) | nxGravity (Effect Towards) | nxGravity | |
| xpLimit | nxLimit | nxLimit | |
| xpPushApart | **nxPush** | nxPush | намного быстрее |
| xpRotator | nxRotate | nxRotate | |
| xpSpeed | nxSpeed | nxSpeed (layer = Acceleration в 2026.1) | |
| xpSpin | nxSpin | nxSpin | |
| xpSticky | nxSticky | nxSticky | |
| xpWind | nxWind (+Von Karman) | nxWind | |
| — | nxVorticity | nxVorticity | завихрения жидкости |
| xpBlend | **nxBlend** | nxBlend | |
| xpColor | nxColor | nxColor | |
| xpInfectio | nxInfectio | nxInfectio | |
| xpKill / xpLife | nxKill | nxKill | время жизни → nxQuestion Kill/Set Life |
| xpScale | nxScale | nxScale | |
| xpSpawn / xpMultiSpawn | nxQuestion Spawn action | **nxSpawn** (8 подслоёв) | |
| xpBranch / xpTendril | — | **nxDendrite** (ветки/сеть/решётка) | |
| xpConstraints | **nxConstraints** | nxConstraints | те же слои |
| xpPPCollisions | nxConstraints Collisions layer | nxPPCollisions | |
| xpFluidPBD / xpFluidFX (SPH) / xpFluidFLIP | **nxFluids** PBD / SPH / FLIP-APIC | nxFluids (+ Mixer, неньютоновские, связка с океаном) | свойства CPU-жидкости в Extended Data эмиттера → на GPU отдельный **nxFluids tag** на каждый эмиттер |
| xpFoam | nxFoam | nxFoam | на слоях (foam/bubbles/spray) |
| xpSplash / xpWave / xpSheeter | nxSplash / nxWave / — | nxSplash / nxWave / nxSheeter | |
| xpExplosiaFX (+ Source tag) | **nxExplosiaFX** (вкладка Sources) | nxExplosiaFX | GPU: источники перечисляются в самом объекте, а не тегами |
| xpFlowField | (CPU, может сосуществовать) | nxFlowField | |
| xpOpenVDBMesher | **nxMesher** | nxMesher | Zhu-Bridson ≈ гладкая жидкость |
| xpGenerator | xpGenerator | nxGenerator | |
| xpTrail | xpTrail | nxTrail | |
| xpShatter | xpShatter | **nxShatter** (2026.1) | |
| xpOcean | xpOcean | **nxOcean** (2026.1) | spray/foam/берег встроены |
| xpDeformer | xpDeformer | **nxDeformer** (2026.1, разрывы) | |
| xpClothFX / xpBullet / xpDynamics | — (только CPU) | **nxMPM** (elastic/metal/brittle/snow/sand), nxPin, nxBind | MPM — путь на GPU к мягкому/хрупкому/металлическому поведению |
| xpCellAuto | — | **nxBioLogic** (реакция-диффузия, кораллы, Physarum…) | |
| xpScatter | — | nxScatter (preset) | |
| — | — | nxWarp, nxFluid2D, nxUpres, nxMaterial, nxLiquid | новые |

## Что изменилось и ломает старые туториалы
- **В документации Fused 2025 пропали некоторые старые названия**: например, режимы xpTrail «Connect/Branches» теперь в меню **Algorithm**; настройки xpFluidFX лежат в эмиттере в **Extended Data → Fluid**.
- **G2 → G3:** в NeXus 2026 эмиттер — это `nxEmitter`, а не оранжевый xpEmitter. Старые сцены G2 по-прежнему работают в Fused; для перевода в G3 используйте **nxConvert** (C4D 2026.1 Beta 3).
- **NeXus 2026.1 Beta 2:** слайдеры силы PBD больше не масштабируются с размером частиц → старые PBD-сцены выглядят иначе.
- **2026.1 Beta 3:** Pulse Interval считается от старта до старта; у nxWarp Flow Reach по умолчанию 0% (для старого вида ставьте 300%); layer nxSpeed переименован в Acceleration; nxGenerator Spawn → Bias; nxCache Auto → Auto Frame Range.
- **Redshift в C4D 2024+** по умолчанию запекает ненативные shader’ы в 128×128 — повышайте для shader’ов TerraformFX/X-Particles.
- Единицы: C4D — см (Y вверх), Blender — м (Z вверх). Длины из C4D делите на 100 для Blender; C4D Y = Blender Z.
