# MoGraph Matrix points as moving attraction targets (nxAttract Object mode + nxPush + nxScale age map)

- Source: Top Tip Tuesday — Matrix Particle Attract — https://www.youtube.com/watch?v=nJpItCX8GlY (2024-07-30)
- Host / generation: C4D; xpEmitter + NeXus GPU (nxPush, nxScale, nxAttract, nxTurbulence) + C4D MoGraph Matrix
- Goal: particles from a text outline pulse and swarm towards the nearest of a few Matrix points that slide along an inner spline.

## Base
xpEmitter Object mode, text spline **Edges**; Rate, lifespan 150, **2000/s**, speed 0. A closed spline inside the letter with **Uniform** intermediate points 100.

## Steps
1. **nxPush** in **Particle Radius** mode, more iterations. [▶ 1:09](https://youtu.be/nJpItCX8GlY?t=69)
2. **nxScale** (below nxPush — order matters): **Set Value** radius 3, **Mapping ▸ Age** 0→80 F on radius; curve rises from 0 quickly to full then shrinks by 80 F. [▶ 1:41](https://youtu.be/nJpItCX8GlY?t=101)
3. Set the emitter radius to **0** so nxScale does all sizing (otherwise they pop on at 3 cm). [▶ 1:52](https://youtu.be/nJpItCX8GlY?t=112)
4. **MoGraph Matrix** in **Object** mode on the inner spline; animate its **Rate** (e.g. 2%) so points travel along the spline. [▶ 3:42](https://youtu.be/nJpItCX8GlY?t=222)
5. **nxAttract** below nxScale, **Object** mode, drop the Matrix in → each Matrix point acts as a separate target; each particle goes to its **nearest** point. Target display off. [▶ 4:28](https://youtu.be/nJpItCX8GlY?t=268)
6. Tame it: **Acceleration 100**, **Speed Limit 25**. [▶ 4:43](https://youtu.be/nJpItCX8GlY?t=283)
7. Matrix **Count ~7** = slow waving/pulsing hand-offs between points; high counts = defined spikes. Hide Matrix + spline. [▶ 5:36](https://youtu.be/nJpItCX8GlY?t=336)
8. **nxTurbulence** at the bottom, Voronoi, smaller scale, modest strength for drift. [▶ 5:54](https://youtu.be/nJpItCX8GlY?t=354)

## Gotchas
- Matrix can also sit on vertices/surfaces and be animated with Effectors — any of that drives the targets.
