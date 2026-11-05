# xpFluidFX — tool card

Mentioned in **5** recipes · 2023-03-29 → 2026-10-11 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- Add **xpFluidFX**; switch to granular on the emitter: **Extended Data ▸ Fluid Data ▸ Fluid Type: Granular** → only Friction, Stability, Cohesion (all interdependent). [▶ 9:38](https://youtu.be/SMO0CZcHa3k?t=578) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- xpFluidFX **Accuracy Fast → High** — granular needs many substeps/iterations or clumps never stiffen. [▶ 15:01](https://youtu.be/SMO0CZcHa3k?t=901) — *[2023-03-29](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)*
- Keyframe the **xpFluidFX Enabled** checkbox off right as the blast starts (~F77–78) — two velocity solvers on the same particles fight. [▶ 53:37](https://youtu.be/OKRG2FUtXjc?t=3217) — *[2023-03-29](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)*
- Keyframe **xpGravity** off at the same frame as xpFluidFX (75 on, 76 off) — otherwise grains sag the moment the fluid solver stops. [▶ 1:38](https://youtu.be/isCt2UKxPtM?t=98) — *[2023-03-29](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)*

## All recipes (5)
- 2026-10-11 · [Tall sand piles with auto-sleep, wake-on-collision and a brittle block (nxMPM Materials + Auto Sleep + display channels)](../../recipes/2026-10-11_nxmpm-sand-pile-sleep-mixed-materials.md)
- 2025-11-26 · [Feature notes: Fused 2025 liquids — GPU FLIP/APIC with viscosity, nxMesher, nxSplash (Final Tech Preview)](../../recipes/2025-11-26_fused-2025-flip-viscosity-nxmesher-nxsplash-feature-notes.md)
- 2023-03-29 · [Sand number that crumbles into clumps (xpFluidFX Granular, Hexagonal fill, animated gravity falloff)](../../recipes/2023-03-29_xpfluidfx-granular-sand-number-crumble.md)
- 2023-03-29 · [Spline-directed smoke blast that advects live grains (xpExplosiaFX Advection + xpFlowField Along Spline + emitter falloff)](../../recipes/2023-03-29_xpexplosiafx-spline-flowfield-grain-advection.md)
- 2023-03-29 · [Smoke tearing a sand number apart without holes (xpExplosiaFX advection, xpFlowField, xpSpawn fill, xpScale + Question kill)](../../recipes/2023-03-29_explosiafx-advection-spawn-fill-grains.md)
