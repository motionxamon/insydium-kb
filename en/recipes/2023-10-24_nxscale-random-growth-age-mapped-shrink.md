# Grow at random rates, shrink with age, then die (nxScale Clamp within Range + Age map on Upper Radius Limit + nxQuestion kill)

- Source: Top Tip Tuesday — nxScale Random Growth — https://www.youtube.com/watch?v=luYB_A_yV1I (2023-10-24)
- Host / generation: C4D; G2 NeXus inside X-Particles (nxScale, nxQuestion, nxTurbulence) + wind
- Goal: particles born at 0 grow at different speeds to different max sizes, then shrink away and are removed.

## Base
**xpEmitter** radius **0 cm**; wind + **nxTurbulence** for motion. Default **nxScale**: **Change Value Over Time – Absolute** (+2 cm/frame), **Clamp to Radius Limit** with **Upper 20 cm**.

## Steps
1. Keyframing the upper limit shrinks all particles at once — use mapping instead. [▶ 1:37](https://youtu.be/luYB_A_yV1I?t=97)
2. nxScale ▸ Mapping ▸ **Age** map, parameter **Upper Radius Limit**, range **100 → 150** frames; curve full until 100, down to 0 at 150. [▶ 2:08](https://youtu.be/luYB_A_yV1I?t=128)
3. Object tab: raise the radius change and add **variation** → different growth rates. [▶ 3:29](https://youtu.be/luYB_A_yV1I?t=209)
4. Clamp mode **Clamp within Range** → each particle gets a random max between the two limits. [▶ 3:58](https://youtu.be/luYB_A_yV1I?t=238)
5. **nxQuestion**: Age **> 5** frames **AND** Radius **= 0** → Action **Kill** (age check avoids killing newborns at radius 0). [▶ 5:44](https://youtu.be/luYB_A_yV1I?t=344)
6. Display Spheres for the final look.

## Newest equivalent
Fused 2025.4 makes **nxScale** layered; see recipe 2026-04-28 (nxScale range spawn fade). In the 2026.1 beta, lifespan logic can also sit in nxQuestion Kill/Set Life.
