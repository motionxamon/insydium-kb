# Hide the hexagonal grid in granular sims (emitter Jitter + one-frame nxPush + Initial State)

- Source: Top Tip Tuesday — Jitter Grid Particles — https://www.youtube.com/watch?v=XwX71yF7O5M (2025-04-01)
- Host / generation: C4D; NeXus inside X-Particles (nxFluids SPH Granular, nxPush, nxGravity)
- Goal: stable grain packing without the visible regular hex pattern in renders, and without an explosive start.

## Base
Object emitter (fox model), **Shot Hexagonal, radius 4 cm**; nxGravity + **nxFluids SPH Granular**. Simulates fine, but the hex lattice is obvious in the render.

## Steps
1. Emission tab ▸ **Jitter X/Y/Z ≈ 3** → grid broken up… but jittered particles now overlap → high density → pressure blast on frame 1. [▶ 1:45](https://youtu.be/XwX71yF7O5M?t=105)
2. Disable gravity and fluids. Add **nxPush**: mode **Particle Radius**, **Strength 100**, **Iterations ~200** (all the separation must happen in a single frame; more particles → more iterations). [▶ 3:15](https://youtu.be/XwX71yF7O5M?t=195)
3. Step forward one frame — particles shift slightly apart. Swap back (push off, gravity + fluids on) → crumbles cleanly, no explosion. [▶ 3:46](https://youtu.be/XwX71yF7O5M?t=226)
4. Finer version: radius **2 cm**, jitter **2.2**, push iterations **~1,500** (one frame takes longer). [▶ 4:49](https://youtu.be/XwX71yF7O5M?t=289)
5. Bake it: emitter ▸ Object ▸ **Initial State ▸ Set State** after the push frame; Emission mode → **Controlled Only** so nothing new is emitted. Delete/disable nxPush. [▶ 6:19](https://youtu.be/XwX71yF7O5M?t=379)

## Gotchas
Not enough push iterations = residual overlaps = explosion when fluids switch on. Smaller particles need less jitter but far more iterations.

## Newest equivalent
Same workflow in NeXus 2026 (nxEmitter has **Initial State** + Keep Stored Age; nxPush unchanged). For sand behaviour, 2026.1 beta **nxMPM** (sand material) is the newer solver option.
