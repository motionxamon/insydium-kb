# Legacy (CPU `xp*`) vs NeXus (GPU `nx*`) — which generation is this tip from?

Checked 2026-11-03 against docs.insydium.ltd. Use this file whenever a recipe, tutorial or user scene mentions an object — first decide which **generation** it belongs to.

## The three generations
| Gen | Years | How it looks in the scene | Notes |
|---|---|---|---|
| **G1 — X-Particles CPU** | up to X-Particles 4 (2017) → 2022 | `xpSystem` → `xpEmitter` + `xp*` modifiers / dynamics | Still fully supported in Fused 2025. Questions/Actions control system. |
| **G2 — NeXus inside X-Particles** | 2022 (Fused/X-Particles 2022+) → Fused 2025 | still `xpEmitter`, but `nx*` modifiers/solvers make the **emitter icon turn orange** (GPU, Vulkan) | GPU and CPU can coexist in one scene; each emitter is solved where its modifiers live. Most Top Tip Tuesdays 2022-2025 with "NeXus" in the title are G2. |
| **G3 — NeXus 2026 (standalone object set)** | Blender 2026.0 (Jul 2026); **C4D 2026.1 public beta (Oct 2026)** | `nxSystem`, `nxEmitter`, `nxCache`, `nxGroup`, `nxCollider`… same engine & parameters in C4D and Blender | C4D needs R19+ (native particle/Pyro link 2025.3+) and X-Particles installed. **nxConvert** (C4D Beta 3) converts xpEmitters/groups to NeXus in one undoable step. nx modifiers can also act on plain xpEmitters. Beta — may change. |

Rule of thumb for answering: **prefer G2/G3 (`nx*`) for anything heavy (fluids, smoke, millions of particles)**; keep G1 when the feature has no nx equivalent (Bullet rigid bodies, xpClothFX, xpTrail-based tricks with xpBranch, xpSprite, Questions on CPU data, Thinking Particles, sound modifiers…). In Blender, only NeXus exists — every G1 recipe must be translated via the table below.

## Object mapping
| CPU (G1) | GPU (G2 C4D) | NeXus 2026 / Blender (G3) | Notes when translating |
|---|---|---|---|
| xpSystem | xpSystem | **nxSystem** (folders) / NeXus Hierarchy (Blender) | Blender: evaluation order = hierarchy order |
| xpEmitter | xpEmitter (orange) | **nxEmitter** | Blender adds Liquid Fill/Flow, point clouds, splats |
| xpCache | xpCache | **nxCache** | Blender: Alembic, PLY, Disk Reserve |
| xpGroup | xpGroup | nxGroup | |
| xpCollider tag | xpCollider tag | **nxCollider** object | Blender: Global on by default |
| xpQuestion + xpAction | **nxQuestion** (Question/Action/Loop/Variable/Script GLSL) | nxQuestion (+ Quill, Sleep/Bind) | CPU questions don't drive GPU emitters reliably — rebuild in nxQuestion |
| Data Mapping tab | NeXus Mapping tab | same | sources overlap (Age, Speed, Radius…) |
| C4D Fields / falloffs | **nxFalloff** | nxFalloff (+ nxFalloff Modifier, Wet/Curvature/AO) | |
| xpTurbulence | nxTurbulence | nxTurbulence | motion inheritance ≈ Curl Blend / Curl Add |
| xpAttractor | nxAttract | nxAttract | |
| xpAvoid | nxAvoid | nxAvoid | |
| xpCover | nxCover | nxCover | |
| xpDirection | nxDirection | nxDirection | |
| xpDrag | nxDrag | nxDrag | |
| xpExplode | nxExplode | nxExplode | |
| xpFlock (dynamics) | nxFlock (modifier) | nxFlock | C4D reactions = child "nxFlock Reactor" objects |
| xpFollowSpline / xpFollowSurface / xpSplineFlow | **nxFollowGeo** | nxFollowGeo | one object; spline mode has Twists/Offset |
| xpGravity (Standard/Newton) | nxGravity (Effect Towards) | nxGravity | |
| xpLimit | nxLimit | nxLimit | |
| xpPushApart | **nxPush** | nxPush | much faster |
| xpRotator | nxRotate | nxRotate | |
| xpSpeed | nxSpeed | nxSpeed (layer = Acceleration in 2026.1) | |
| xpSpin | nxSpin | nxSpin | |
| xpSticky | nxSticky | nxSticky | |
| xpWind | nxWind (+Von Karman) | nxWind | |
| — | nxVorticity | nxVorticity | fluid swirl |
| xpBlend | **nxBlend** | nxBlend | |
| xpColor | nxColor | nxColor | |
| xpInfectio | nxInfectio | nxInfectio | |
| xpKill / xpLife | nxKill | nxKill | lifespan → nxQuestion Kill/Set Life |
| xpScale | nxScale | nxScale | |
| xpSpawn / xpMultiSpawn | nxQuestion Spawn action | **nxSpawn** (8 sub-layers) | |
| xpBranch / xpTendril | — | **nxDendrite** (branches/network/lattice) | |
| xpConstraints | **nxConstraints** | nxConstraints | same layers |
| xpPPCollisions | nxConstraints Collisions layer | nxPPCollisions | |
| xpFluidPBD / xpFluidFX (SPH) / xpFluidFLIP | **nxFluids** PBD / SPH / FLIP-APIC | nxFluids (+ Mixer, non-Newtonian, ocean coupling) | CPU fluid props on emitter Extended Data → GPU per-emitter **nxFluids tag** |
| xpFoam | nxFoam | nxFoam | layer-based (foam/bubbles/spray) |
| xpSplash / xpWave / xpSheeter | nxSplash / nxWave / — | nxSplash / nxWave / nxSheeter | |
| xpExplosiaFX (+ Source tag) | **nxExplosiaFX** (Sources tab) | nxExplosiaFX | GPU: sources listed in the object, not tags |
| xpFlowField | (CPU, can coexist) | nxFlowField | |
| xpOpenVDBMesher | **nxMesher** | nxMesher | Zhu-Bridson ≈ smooth liquid |
| xpGenerator | xpGenerator | nxGenerator | |
| xpTrail | xpTrail | nxTrail | |
| xpShatter | xpShatter | **nxShatter** (2026.1) | |
| xpOcean | xpOcean | **nxOcean** (2026.1) | spray/foam/shore built in |
| xpDeformer | xpDeformer | **nxDeformer** (2026.1, tearing) | |
| xpClothFX / xpBullet / xpDynamics | — (CPU only) | **nxMPM** (elastic/metal/brittle/snow/sand), nxPin, nxBind | MPM is the GPU route to soft/brittle/metal behaviour |
| xpCellAuto | — | **nxBioLogic** (reaction-diffusion, coral, Physarum…) | |
| xpScatter | — | nxScatter (preset) | |
| — | — | nxWarp, nxFluid2D, nxUpres, nxMaterial, nxLiquid | new |

## Things that changed and break old tutorials
- **Fused 2025 docs dropped some old names**: e.g. xpTrail "Connect/Branches" modes are now the **Algorithm** menu; xpFluidFX settings sit in emitter **Extended Data → Fluid**.
- **G2 → G3:** in NeXus 2026 the emitter is an `nxEmitter`, not an orange xpEmitter. Old G2 scenes still work in Fused; use **nxConvert** (C4D 2026.1 Beta 3) to move them to G3.
- **NeXus 2026.1 Beta 2:** PBD strength sliders no longer scale with particle size → old PBD scenes look different.
- **2026.1 Beta 3:** Pulse Interval measured start→start; nxWarp Flow Reach 0% default (use 300% for old look); nxSpeed layer renamed Acceleration; nxGenerator Spawn → Bias; nxCache Auto → Auto Frame Range.
- **Redshift in C4D 2024+** bakes non-native shaders at 128×128 by default — raise it for TerraformFX/X-Particles shaders.
- Units: C4D cm (Y-up) vs Blender m (Z-up). Divide C4D lengths by 100 for Blender; C4D Y = Blender Z.
