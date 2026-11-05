# Activate a fluid sim by moving particles into a new group (nxQuestion Field + Random math, Set Group)

- Source: Top Tip Tuesday — nxQuestion Change Group — https://www.youtube.com/watch?v=xCo2B_o5VeQ (2023-09-12)
- Host / generation: C4D; G2 NeXus inside X-Particles (orange xpEmitter, nxFluids SPH, nxGravity, nxAvoid, nxQuestion redesign of Fused 2023.3)
- Goal: a 100k-particle water body sitting frozen on a wolf head and only falling/splashing where a growing field passes, with a ragged, random edge.

## Base
xpEmitter from the head, Emission **Shot**, random shot type, **100,000** particles. **nxFluids** default but solver **SPH**; default **nxGravity**. Collisions faked with **nxAvoid** on the head (fast; put a collider tag on the mesh instead if leaks matter).

## Steps
1. Emitter ▸ Groups: Ctrl+Alt-click Create twice (groups 1 and 2); mode Random → **First Group Only** so every newborn particle lands in group 1. [▶ 1:35](https://youtu.be/xCo2B_o5VeQ?t=95)
2. **nxFluids** and **nxGravity** ▸ Groups Affected: **group 2** only. Playback now shows no motion. [▶ 2:04](https://youtu.be/xCo2B_o5VeQ?t=124)
3. Add an **nxQuestion** plus a C4D **Spherical field**; (the field is linked on the nxQuestion Fields tab). [▶ 2:40](https://youtu.be/xCo2B_o5VeQ?t=160)
4. nxQuestion ▸ Object: add a **Question**, data type Age → **Field**, test **> 0** (anywhere inside the outer sphere counts). [▶ 2:50](https://youtu.be/xCo2B_o5VeQ?t=170)
5. Add an **Action** as its child: Set Color → **Set Group**, target **group 2**. Scale the field up over time: particles entering it drop and splash. [▶ 3:19](https://youtu.be/xCo2B_o5VeQ?t=199)
6. Break the perfect spherical hole: add a second Question as child of the first (Set Group becomes its child), combine as **And**, type **Math ▸ Random**, Min **−100**, Max **100**, test > 0 → only about half the particles inside switch. [▶ 4:51](https://youtu.be/xCo2B_o5VeQ?t=291)
7. Enable **Time Variation** (new random number every frame) and raise the threshold to **> 80**: few switch per frame, but more accumulate over time → a gradual, crumbly release. [▶ 5:36](https://youtu.be/xCo2B_o5VeQ?t=336)

## Gotchas
- Order matters: actions only fire when every parent question passes.
- Without Time Variation each particle keeps one random value, so the "losers" never switch.

## Newest equivalent
Same nxQuestion setup in NeXus 2026.1 (nxEmitter/nxGroup); use an **nxFalloff** (16 modes, incl. Noise for an organic front) instead of a C4D field, or a per-layer Falloff list on the modifiers. Quill (Blender) can draft the question tree from a prompt. FLIP/APIC (Fused 2025.4) for a nicer splash.
