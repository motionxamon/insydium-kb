# xpOcean — tool card

Mentioned in **3** recipes · 2023-04-20 → 2025-04-08 · hosts: C4D

_Auto-collected from the recipes: lines are quoted from video recipes (newest first). Values are starting points from captions._

## Settings and values used in videos
- **xpOcean** ▸ mode **Deformer** (not Primitive), child of the plane. [▶ 0:40](https://youtu.be/r_AyI7Bgi0U?t=40) — *[2025-04-08](../../recipes/2025-04-08_custom-object-ocean.md)*
- Loop: xpOcean ▸ **Looping on**, Loop Time = last frame + 1 (**201** for a 200-frame scene). [▶ 5:38](https://youtu.be/r_AyI7Bgi0U?t=338) — *[2025-04-08](../../recipes/2025-04-08_custom-object-ocean.md)*
- X-Particles ▸ Generators ▸ **xpOcean**. Width / Height segments **200** each for detail. [▶ 0:47](https://youtu.be/xQFbyD2fMNo?t=47) — *[2023-06-27](../../recipes/2023-06-27_xpocean-looping-deformer-layer.md)*
- **xpOcean** (Generators): lower Wave Height and Time Scale, raise **Wind Speed** for a longer swell, add **Choppiness** only until peaks start folding. Viewport material: no reflectance, **Fresnel** shader in Color, deep blue → greyish white. [▶ 9:11](https://youtu.be/VuevOvpbvJY?t=551) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- Switch xpOcean **Type: Primitive → Deformer** (works like any C4D deformer as child/sibling). [▶ 10:28](https://youtu.be/VuevOvpbvJY?t=628) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- **xpOpenVDBMesher** source = base emitter, **Point Radius 5**. Put xpOcean as its sibling in the Generators folder → the live mesh is deformed. Move the material onto the mesher. [▶ 12:11](https://youtu.be/VuevOvpbvJY?t=731) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- Particles ride the waves too: add the xpOcean deformer to each colour emitter's **Modifiers** list (ticked = included). [▶ 11:28](https://youtu.be/VuevOvpbvJY?t=688) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- After caching: **untick xpOcean in the emitters' Modifiers** (else cached particles get deformed twice). [▶ 16:33](https://youtu.be/VuevOvpbvJY?t=993) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- The VDB mesh vanishes while scrubbing: put the mesher under an **xpJoin** (Utilities) with xpOcean as its sibling. Lower the Join **Y −7 cm** so particles float on the surface. [▶ 17:37](https://youtu.be/VuevOvpbvJY?t=1057) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*

## All recipes (3)
- 2025-04-08 · [Animated ocean surface inside any object (xpOcean Deformer + Boole Intersect, looping)](../../recipes/2025-04-08_custom-object-ocean.md)
- 2023-06-27 · [Large looping ocean without visible tiling (xpOcean Looping + second xpOcean as Deformer)](../../recipes/2023-06-27_xpocean-looping-deformer-layer.md)
- 2023-04-20 · [Speed-gradient colours and an ocean-deformed fluid bed (Gradient Parameter by Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
