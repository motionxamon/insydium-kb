# Exploding planet: spin-speed-driven texture emission with clumping debris (Expresso Range Mapper → Birth Rate, nxDrag, nxConstraints Friction)

- Source: NAB 2023 — INSYDIUM Training — NeXus Friction - Part 1 — https://www.youtube.com/watch?v=6sdlTZsi9kQ (2023-04-16)
- Host / generation: C4D; G2 — CPU xpEmitter features (texture emission, motion inheritance) + NeXus GPU **nxDrag** and **nxConstraints** (orange emitters)
- Goal: a spinning sphere flings off stripy streams of particles only while it spins fastest; the streams slow down and clump together.

## Base
- Sphere ▸ Type **Icosahedron**, Segments **100** (even topology).
- Material on the sphere: Color ▸ **Noise**, type **Stupl**, Octaves **10**, Global Scale **230**, scale stretched on X and squashed on Y, **Low Clip** raised a lot and **High Clip** lowered → thin white streaks; cycle Seed for variants.
- Texture tag Projection **UVW → Spherical** (the primitive has no real UVs, so emission would not line up with the texture otherwise).
- Animation (200 F): rotation H keys **0° @ F0, 180° @ F60, 220° @ F120**; in the Timeline switch Dope Sheet → **F-Curve** and shape the curve slow → very fast → slow.

## Steps
1. **xpSystem** ("system motion") with its **xpEmitter**: Emitter Shape **Object** = sphere, Emission Source **Texture** → Texture tab: link the sphere's texture tag (emit from bright parts of the Color channel, color particles from it). Speed **0**. [▶ 31:41](https://youtu.be/6sdlTZsi9kQ?t=1901)
2. Birth Rate units **Per Second → Per Frame** (personal preference: you know exactly how many are born each frame). [▶ 2:05](https://youtu.be/6sdlTZsi9kQ?t=125)
3. Emission ▸ **Motion Inheritance**: enable, linear off, **rotational on** → particles fly off tangentially. [▶ 10:32](https://youtu.be/6sdlTZsi9kQ?t=632)
4. Drive emission by spin speed: sphere ▸ Programming Tags ▸ **Expresso**. Sphere node output **Rotation Velocity** → **Calculate ▸ Range Mapper** → emitter node input **Emission ▸ Birth Rate**. [▶ 25:35](https://youtu.be/6sdlTZsi9kQ?t=1535)
5. Range Mapper: Input Range **Degrees**; Input Lower **~150°/s** (tried 100 and 160), Input Upper **360°/s**; Output Lower 0, Output Upper large (**30,000** in the demo) → nothing is born until the spin is fast. [▶ 27:36](https://youtu.be/6sdlTZsi9kQ?t=1656)
6. **nxDrag**: Density **Water**, Strength multiplier **50**. Drag scales with particle radius (bigger = slowed more): emitter radius **2**, variation **0.5**. Display **Dots** for speed. [▶ 27:54](https://youtu.be/6sdlTZsi9kQ?t=1674)
7. **nxConstraints ▸ Friction** layer (not spring connections): defaults are Friction 80, up to **16** neighbours within **30 cm** — heavy on the GPU, so lower the radius and Connection Limit while blocking, raise for the final cache. [▶ 23:15](https://youtu.be/6sdlTZsi9kQ?t=1395)
8. Duplicate the emitter → **emitter big**: display Squares; give it its own Range Mapper copy (Ctrl-drag the node) with Output Upper **500**. On original + big: Speed **1** with a little variation. [▶ 24:33](https://youtu.be/6sdlTZsi9kQ?t=1473)
9. Third copy → **emitter detail**: Range Mapper Output Upper **5,000**; radius **4** (later **3**), variation **1** → heavily dragged fill particles. [▶ 27:25](https://youtu.be/6sdlTZsi9kQ?t=1645)
10. For instancing rocks later: all emitters ▸ Extended Data ▸ **Use Rotation ▸ Simple Spin 1°**, variation 1° per axis (check with Display ▸ Boxes Filled). [▶ 30:21](https://youtu.be/6sdlTZsi9kQ?t=1821)
11. All emitters ▸ Texture tab: drive **Radius** from the Color channel too → brighter streaks get bigger radii, drag harder, and clump more coherently. [▶ 31:12](https://youtu.be/6sdlTZsi9kQ?t=1872)

## Gotchas
- An Expresso-driven parameter can no longer be edited in the emitter (it snaps back).
- UVW mapping on a primitive without UVs misplaces texture emission — use Spherical.
- Too strong a drag leaves a static halo of particles: lower the radius on the detail emitter or the nxDrag strength.

## Newest equivalent
Same layers exist in NeXus 2026 (**nxEmitter** + nxDrag + nxConstraints Friction; **nxConvert** moves xpEmitters over in C4D 2026.1 Beta 3). Spin-gated emission is easier to keep procedural with Mapping/nxFalloff instead of Expresso. For granular clumping debris, the 2026.1 beta **nxMPM** Sand material is an alternative to friction constraints.
