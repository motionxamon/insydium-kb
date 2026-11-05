# Rendering constraint springs + glassy skin underwater (xpTrail Algorithm Constraints, xpOpenVDBMesher, Redshift Environment fog)

- Source: Top Tip Tuesday — Rendering nxConstraints in Redshift — https://www.youtube.com/watch?v=jHu6mpJfEUQ (2024-10-01)
- Host / generation: C4D; NeXus G2 nxConstraints (tendril rig from 2024-08-27 recipe) + CPU **xpTrail** & **xpOpenVDBMesher**; **Redshift**
- Goal: make the invisible spring connections renderable, wrap tendrils in an organic glass skin, fake a miniature underwater look.

## Steps
1. On the emitter that makes the connections: Display ▸ **Display Constraints** on (required for viewport and trails). [▶ 0:31](https://youtu.be/jHu6mpJfEUQ?t=31)
2. **xpTrail**: that emitter, **Algorithm ▸ Constraints**, tick **Birth** (choose the constraint type) → trails turn green. Hide emitter/constraints. [▶ 1:07](https://youtu.be/jHu6mpJfEUQ?t=67)
3. xpTrail ▸ **Redshift Object tag ▸ Curve ▸ Boxes**, Thickness ~**3**. [▶ 1:45](https://youtu.be/jHu6mpJfEUQ?t=105)
4. Spawn emitter ▸ RS Object tag ▸ Particles: **sphere instances**, scale reduced to a fraction. [▶ 2:34](https://youtu.be/jHu6mpJfEUQ?t=154)
5. **xpOpenVDBMesher** on the spawn emitter: Voxel Size **3**, Point Radius **2**, **Filters** on (default). [▶ 3:25](https://youtu.be/jHu6mpJfEUQ?t=205)
6. Mesher material: RS Standard, **Transmission weight 1**; IOR **0.95** (< 1 sells "underwater"); Scatter color light grey with **Depth** ~10 (1 = milky, 30 = clear); a touch of roughness. [▶ 3:52](https://youtu.be/jHu6mpJfEUQ?t=232)
7. Render Settings ▸ Redshift ▸ Globals: **default light off**. Add **Redshift Environment**: scattering off, **Attenuation 0.1**, **Fog emission** green (lights the scene + depth fade). Lower its effect on reflections at the bottom of volume scattering settings to soften harsh edges. [▶ 4:45](https://youtu.be/jHu6mpJfEUQ?t=285)
8. Standard materials on trail and particles. [▶ 6:55](https://youtu.be/jHu6mpJfEUQ?t=415)
9. **Redshift Camera** ▸ Optical: pick focus on a tendril, low aperture value, **Bokeh** on → miniature DOF. [▶ 7:28](https://youtu.be/jHu6mpJfEUQ?t=448)

## Newest equivalent
**nxMesher** (Fused 2025.4) for the skin; in NeXus 2026 use nxTrail and nxSpawn for the rig. Redshift C4D 2024+ bakes non-native shaders at 128×128 — raise if using XP shaders.
