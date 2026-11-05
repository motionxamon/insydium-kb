# Snow sculpture that crumbles (Shot-mode hex packing + nxFluids SPH Granular: friction, substeps, stability, cohesion)

- Source: Top Tip Tuesday — Granular Drop — https://www.youtube.com/watch?v=1oRzCeDQjWs (2023-03-07)
- Host / generation: C4D; G2 NeXus — xpEmitter + **nxFluids SPH Granular** + nxGravity; xpCollider tags on plane + cube
- Goal: a wolf head packed with grains that drops and breaks into clumps (snow, sand, sugar, salt).

## Steps
1. System ▸ Emitters ▸ new emitter: shape **Object**, link the wolf mesh. [▶ 0:42](https://youtu.be/1oRzCeDQjWs?t=42)
2. Emission: Subframe Emit off; **Shot** mode, Shot Type **Hexagonal** (grid), speed **0**. Step one frame, hide the mesh. Smaller radius = more particles in the volume. [▶ 0:58](https://youtu.be/1oRzCeDQjWs?t=58)
3. **nxGravity** already in scene → they fall but don't hold together. [▶ 1:36](https://youtu.be/1oRzCeDQjWs?t=96)
4. NeXus ▸ Objects ▸ **nxFluids**: type **SPH**, mode **Granular** (PBD can't do grains). [▶ 1:59](https://youtu.be/1oRzCeDQjWs?t=119)
5. Display: Gradient Parameter mapped to the **granular** value, range **Auto**. [▶ 2:21](https://youtu.be/1oRzCeDQjWs?t=141)
6. Granular ▸ **Friction 100**. [▶ 2:44](https://youtu.be/1oRzCeDQjWs?t=164)
7. Real clumps need a better velocity solve: **Substeps 3 → 15**. [▶ 3:18](https://youtu.be/1oRzCeDQjWs?t=198)
8. **Stability** = speed check: grains separating faster than this escape friction. 60 → big lumps survive; 2 → falls apart; final **25**. [▶ 3:42](https://youtu.be/1oRzCeDQjWs?t=222)
9. **Cohesion** = extra spring-like hold; usually leave default — lower it if the sim looks bouncy/springy. [▶ 4:40](https://youtu.be/1oRzCeDQjWs?t=280)

## Newest equivalent
**nxMPM** sand/snow (nxMaterial presets *Snow packed/sticky*, *Sand wet*) in the 2026.1 beta; stable Fused: nxFluids SPH Granular as here.
