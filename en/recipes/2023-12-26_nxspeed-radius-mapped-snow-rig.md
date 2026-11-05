# Natural falling snow (nxSpeed limit mapped to radius + second nxTurbulence Curl Blend mapped to radius)

- Source: Top Tip Tuesday — NeXus Snow Rig — https://www.youtube.com/watch?v=RnIGtMwTpLg (2023-12-26)
- Host / generation: C4D; G2 NeXus inside X-Particles (xpEmitter + nxGravity, nxSpeed, nxTurbulence, nxKill) + CPU xpGenerator
- Goal: realistic drifting snow for VFX plates or full 3D scenes; small flakes fall faster and some get kicked up by gusts (also works as a dust/floaties rig).

## Base
**xpEmitter** Rectangle 950 × 2000, **Rate 1000/s**, speed 0, **radius 0.9 cm ±0.5** (range 0.4–1.4 cm). Extended Data: Use Rotation, birth rotation Random, **Simple Spin** with small values (gives tumbling). Default **nxGravity**; **nxKill** domain removes particles outside the bounds.

## Steps
1. Air resistance: **nxSpeed** at the bottom (after gravity). Operation **Incremental → Acceleration**, exponential value **0** (no acceleration), enable **Speed Limit 85 cm**. [▶ 1:50](https://youtu.be/RnIGtMwTpLg?t=110)
2. nxSpeed ▸ Mapping ▸ **Radius** map → max speed clamp. Range **Min 0.4 / Max 1.4**. Curve: small flakes at full 85, big flakes much lower. [▶ 3:25](https://youtu.be/RnIGtMwTpLg?t=205)
3. Flakes: three Flower splines in **Extrude** objects as children of **xpGenerator** (emitter linked), multiple-children mode Random, Clone type **Multi-Instances** for viewport speed. (With Redshift/Octane/Cycles 4D you would instance at render time instead.) [▶ 5:35](https://youtu.be/RnIGtMwTpLg?t=335)
4. Swirl: **nxTurbulence** below nxSpeed, **Voronoi**, strength ~12 (then reduced slightly), larger scale, lower frequency. [▶ 6:16](https://youtu.be/RnIGtMwTpLg?t=376)
5. Gust kicks (the key step): duplicate the turbulence, type **Curl**, strength **4**. Curl options: turn **Add** off, keep **Blend** high (0 = no effect, near max overrides existing velocity). [▶ 8:09](https://youtu.be/RnIGtMwTpLg?t=489)
6. Mapping ▸ **Radius** map, category Curl, parameter **Blend**, same 0.4–1.4 range; small particles get full blend, large ones none → only some flakes spin-drift upward. [▶ 8:30](https://youtu.be/RnIGtMwTpLg?t=510)
7. Render with depth of field + motion blur. [▶ 9:09](https://youtu.be/RnIGtMwTpLg?t=549)

## Newest equivalent
Fused 2025.4 layered **nxTurbulence/nxSpeed** let both turbulences live in one object. In the 2026.1 beta the nxSpeed layer is called **Acceleration**, and **nxGenerator** / **nxEmitter** (G3) replace the xp objects; **nxWind** gust waves via **nxWarp** are another option for kicks.
