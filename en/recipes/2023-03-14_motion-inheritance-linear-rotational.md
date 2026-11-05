# Particles that carry their emitter object's motion (Motion Inheritance linear + rotational, xpTurbulence)

- Source: Top Tip Tuesday — Motion Inheritance — https://www.youtube.com/watch?v=pwEBS2tOgNw (2023-03-14)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpTurbulence)
- Goal: organic, advection-like wisps driven by an erratically moving object.

## Base
Platonic with a C4D **Vibrate** tag (position + rotation). xpEmitter: Object shape, emit from **Edges**, all frames, lifespan **50 ± 10**, speed 0.

## Steps
1. Optional baseline: **xpTurbulence** (Modifiers ▸ Motion), default settings — nice, but unrelated to the object's motion. Disable it while tuning. [▶ 1:30](https://youtu.be/pwEBS2tOgNw?t=90)
2. Display: dots, color **Gradient Parameter** mapped to Age (pastel preset: yellow young → pink old). [▶ 1:55](https://youtu.be/pwEBS2tOgNw?t=115)
3. Emission ▸ **Motion Inheritance** on. Types: **Linear Direction** and **Rotational Direction**. [▶ 2:38](https://youtu.be/pwEBS2tOgNw?t=158)
4. Linear only first: very strong with erratic motion — lower **Speed Blend** a lot. [▶ 3:59](https://youtu.be/pwEBS2tOgNw?t=239)
5. First-frame static particles (nothing to inherit yet): turn off Emit All Frames, emit **frame 2 → 600** (scene end). [▶ 3:44](https://youtu.be/pwEBS2tOgNw?t=224)
6. Rotational only to see the spin contribution; final = both on with low Speed Blend. [▶ 4:14](https://youtu.be/pwEBS2tOgNw?t=254)
7. Re-enable turbulence: Strength **16**, slightly smaller scale. [▶ 4:40](https://youtu.be/pwEBS2tOgNw?t=280)

## Newest equivalent
nxEmitter motion inheritance + **nxTurbulence** (Curl Add / Curl Blend) on the GPU.
