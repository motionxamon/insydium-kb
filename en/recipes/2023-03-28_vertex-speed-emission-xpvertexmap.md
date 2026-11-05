# Emit only from the fastest-moving parts of a mesh (xpVertexMap Vertex Speed layer + texture emission)

- Source: Top Tip Tuesday — Vertex Speed Emission — https://www.youtube.com/watch?v=iWET6SJpDhw (2023-03-28)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpVertexMap, xpTurbulence)
- Goal: wispy, smoky particles that burst off a vibrating capsule only when it moves fast.

## Base
Capsule primitive with a C4D **Vibrate** tag (position + rotation). xpEmitter in Object mode on the capsule, speed 0, **lifespan 30**.

## Steps
1. INSYDIUM ▸ X-Particles ▸ Utilities ▸ **xpVertexMap**; add the capsule to its Objects list — works on primitives and generators (e.g. MoGraph clones), not just polygon objects. [▶ 0:07](https://youtu.be/iWET6SJpDhw?t=7)
2. Delete the default Polygon layer; add a **Vertex Speed** layer. Options: weight 0 at 0 world speed, full weight at **300 cm/s** by default — raise the max well above that for a fast-moving object, and raise **Min Speed** so static parts stay at zero. [▶ 2:19](https://youtu.be/iWET6SJpDhw?t=139)
3. Emitter ▸ Object tab: put the generated vertex map in **Selection**; raise **Threshold** so only fast vertices emit (back off if too sparse). [▶ 3:02](https://youtu.be/iWET6SJpDhw?t=182)
4. Emission ▸ **Motion Inheritance** on, ~**60%**. [▶ 3:35](https://youtu.be/iWET6SJpDhw?t=215)
5. **xpTurbulence** (Modifiers ▸ Motion): noise **FBM**, larger scale, Strength **~24** → wispy smoke. [▶ 4:02](https://youtu.be/iWET6SJpDhw?t=242)
6. Texture: C4D material with a **Luka** noise in Color (scale **600%**) on the capsule. Emitter ▸ Emit from **Texture**, link that texture tag: emission follows the bright parts of the Color channel and particles take their color from it. [▶ 4:44](https://youtu.be/iWET6SJpDhw?t=284)

## Newest equivalent
G2/G3: nxEmitter emission with nxFalloff (Attribute / vertex-map falloffs, 2026.1 beta) and motion inheritance; nxTurbulence (Curl Add/Blend ≈ inheritance).
