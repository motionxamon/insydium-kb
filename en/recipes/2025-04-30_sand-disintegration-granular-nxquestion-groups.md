# Procedural sand-bust disintegration (nxFluids SPH Granular + nxColor/nxQuestion groups + nxWind Von Karman + distance-mapped grains)

- Source: INSYDIUM tutorial — Sand Disintegration — https://www.youtube.com/watch?v=V4mwAf8tcLk (2025-04-30)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxFluids, nxColor, nxBlend, nxQuestion, nxWind, nxSpeed, nxKill, nxPush) + CPU xpCollider tag, xpCache; Redshift
- Goal: a sand bust cracks into chunks along a moving noise front, the chunks crumble to dry powder and blow out of frame.

## Base
Bust from the C4D content browser scaled to ~113 cm tall (object volume decides particle count), ground plane at Y −50, static render camera.

## Steps
1. **xpEmitter ▸ Object** = bust; Emission **Shot**, shot type **Hexagonal**, speed 0; draft radius **1 cm** (~62k particles). Display ▸ birth color **black**.
2. **nxColor ▸ Gradient by Parameter** layer, gradient black→white, parameter **Field**. Fields tab: **Random field** (noise Luka, scale ~1000; Remapping ▸ Contour **Curve**, crush to ~0.2 / 0.8 for contrast) + **Linear field** on **Multiply**, direction +Y, rotated (P ~33°, H ~85°). Keyframe the linear field Y from 85 (F0) to −2.5 (~F39) so whiteness sweeps down.
3. Set the gradient layer's blend mode to **Add** → once white, a particle never returns to black when it moves through the field.
4. **nxBlend**: mode Addition, Color only, radius 5, **Strength ~1000** → white creeps through the dark patches until everything is white.
5. **nxQuestion** (below nxColor): particle Color **Brightness > 0.5** → action **Set Group = group 1** (create the xpGroup first).
6. **nxWind**, **Groups Affected = group 1**, H −95°, P 55°; mode **Von Karman**, strength **625**, **Variation 190%** (>100% gives some negative, back-blowing gusts), turbulence frequency 40, Friction Velocity **0.13**.
7. Ground: **xpCollider** tag, bounce 0, a little friction.
8. **nxFluids** SPH, Fluid Type **Granular**, **Substeps 12**, Friction 100%, **Stability 5** (default is too high — the whole bust lifts as one), cohesion default 10%.
9. **Speed clamp nxQuestion** — must be last in the stack: Particle Group **< 1** (ungrouped = group 0) → **Set Speed 0**, so black grains are not dragged along by friction.
10. Efficiency: **nxKill ▸ Outside Camera Field of View** with the render camera (optional extra degrees) — off-screen grains die and stop costing sim/cache time.
11. Crumble to powder: nxFluids ▸ Mapping, three **Distance** layers (SPH Friction, Stability, Cohesion), range **5 → 100 cm**, curve full → 0 (cohesion can fall off a bit later). Raise the min distance (e.g. 30 cm) to keep big chunks flying longer.
12. Tame the wild edges: **nxSpeed** after the wind, operation **Acceleration** with exponential 0 (does nothing) + **Clamp Max Speed 500 cm**.
13. Production resolution: radius **0.225** → ~5.5 M particles (lower radius in small steps — count climbs very fast).
14. Break the hex grid: **disable the collider**, emission **Jitter X/Y/Z = 0.225** (≤ radius), then **nxPush** Particle Radius, full strength, thousands of iterations (≈3 min for frame 1) to undo overlaps; then **nxKill** box (size 100, Y −100 so its top sits on the floor, kill inside bounds) placed **after** the push to remove grains pushed below ground.
15. Emitter ▸ **Initial State ▸ Set State**; Emission type **Controlled Only**; switch off push + both setup kills; **re-enable collisions**.
16. **xpCache** with **Compress Cache on Build**: 500 F took ~20 min (estimate starts at hours but most grains are dead by ~F200). Viewport: Dots, Level of Detail **1%**.
17. Iterate: **Stability 15** for bigger chunks at 5.5 M. Keyframe wind Variation from 190% down below 100% around F187 so stragglers leave frame.
18. Slow motion: cache Playback **Hold** on, **Scale 50%** (fixed-count sims stay smooth even at 1%).
19. Redshift: **Redshift Object tag ▸ Sphere instances**, rough sand material; bucket **512** (24 GB card), adaptive threshold **0.02**, Random Noise Pattern on (turn it off only when denoising), EXR **16-bit float**; ~16 s/frame at 720p, frames 10–400.

## Gotchas
- Order matters: nxColor → nxQuestion (group) → forces → speed-clamp question last; push before kill.
- Forgetting to re-enable the collider before the long cache ruins the run.
- Fluid particles born overlapping blast apart — always push apart after jittering.

## Newest equivalent
NeXus 2026.1 **nxMPM** sand (per-emitter materials such as Sand Dry / Sand Powder Fine, Momentum 0 for dry grains, Auto Sleep) replaces SPH Granular; **nxBind** can hold the bust and release by Falloff or **Color Brightness** with Chunks / Chunk Size — the same "crumbling character → nxMPM" idea shown in the 21 Oct 2026 training. Use nxFalloff layers instead of C4D fields; nxSpeed's layer is called Acceleration in 2026.1.
