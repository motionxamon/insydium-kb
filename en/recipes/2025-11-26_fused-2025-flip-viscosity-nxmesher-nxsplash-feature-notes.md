# Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)

- Source: Fused 2025 Tech Preview — INSYDIUM Fused 2025 Final Tech Preview — https://www.youtube.com/watch?v=mWj3nWcfbSQ (2025-11-26)
- Host / generation: C4D; NeXus G2 (nx modifiers on xpEmitters) in the Fused beta that shipped as 2025.4; Redshift renders
- Goal: overview of the new GPU liquid tools — FLIP/APIC solver with built-in viscosity, GPU nxMesher, nxSplash crown splashes.

## nxFluids FLIP / APIC (new solver beside PBD and SPH)
- Voxel-grid solver with two modes: **FLIP** (high FLIP Fraction, default **95%** = noisy, splashy, mid/large scale) and **APIC** (smoother, keeps angular momentum — ripples travel and reflect off walls for a long time).
- Lower FLIP Fraction (≈**60%**) smooths the flow and removes noisy surface detail — good for gloop and small-scale splashes.
- **Viscosity**: 0 = off; any value > 0 switches on the dedicated viscosity solver (100 = gloopy slime).
- **Mapping tab** (source FLIP/APIC) for variable viscosity, e.g. **Particle Speed**: full viscosity up to 5 cm/s, ramping down to 15 cm/s and above (fast parts sheet, slow parts blob).
- Collider tag **Friction** helps the liquid stick to the collider (bust).
- All nx modifiers work on it: **nxWind** Strength 250, **Von Karman** mode for gusts; **nxRotate** pitched upright in the tank centre for a whirlpool; nxTurbulence; **nxDirection** to fake high-speed flow without gravity.
- APIC sheeting splashes: Surface Tension **5**, **Weak Particle Repulsion 10** to keep thin sheets.

## Molten chocolate that sets (colour-mapped viscosity)
1. Emitter width ≈ 0 (one particle thick) → thin folding ribbons.
2. **nxQuestion**: Object Distance < **3 cm** to the ice-cream polygons → Set Color white with a low Weight (fades in).
3. nxFluids Viscosity **150**; Mapping ▸ **Particle Color** → viscosity (black = low but non-zero, white = full).
4. **nxBlend** Mode **Add**, Distance **5 cm**, Strength 100 → particles only get lighter, so leftovers set faster.
5. nxMesher with vertex colour → Redshift roughness differs between molten and set areas.

## nxMesher (GPU)
- Drag emitters into its layers. Surface type **Spheres** (VDB-like, needs smoothing layers) or **Zhu-Bridson** (clean, smooth sheets with no filters).
- Gloop demo: Radius **2**, Polygon Size **1.5**. Folding demo: Radius **0.8**, Polygon Size **3**, smoothing layer **Mean Curvature**, Iterations **10–13** (keeps folds, flattens flat areas).
- **Export Tags ▸ Transfer Color** → Color vertex tag (drives SSS colour in the material); velocity can also be passed on.

## nxSplash (crown splash designer)
- Torus emitter + nxSplash, FLIP active. Top/bottom radius shaping handles plus power handles; Height, Strength (100 → 80% for APIC).
- N peaks = **2N power handles**: 10 handles, every other one lowered → 5 peaks; pull in the top shaping handles at the low-power handles for petal shapes; randomise peaks a little.
- Raise particle count for sheeting (5,000 → **20,000 per frame**).
- FLIP at FLIP Fraction 58 arches down; APIC holds a real crown longer.

## Macro splash photography
- Fast emitter at a collider (lemon), no gravity, nxDirection push; detail needs a very dense voxel grid and high solver substeps.
- Force crown-plus-wrap: hidden collider cylinder with **Displacer** (noise) + **Smoothing** deformer in the path; changing the noise seed gives a new splash each time.

## Replaces
CPU xpFluidFLIP / xpFluidFX viscosity, xpOpenVDBMesher (→ nxMesher), hand-built crown-splash emitters (→ nxSplash). Newer still: 2026.1 beta FLIP non-Newtonian (Flow Index, Yield Stress), Wall Friction and Mixer.
