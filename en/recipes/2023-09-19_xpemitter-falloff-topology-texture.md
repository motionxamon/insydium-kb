# Controlling where an object emits (xpEmitter Polygon Area, Falloff, Topology Height curve, Emit from Texture)

- Source: Top Tip Tuesday — Emission Control — https://www.youtube.com/watch?v=GebrRmY2L4Q (2023-09-19)
- Host / generation: C4D; CPU **xpEmitter** (emission settings, independent of solver)
- Goal: restrict and shape emission on a torus by falloff, height and an animated texture.

## Base
Emitter with wind + turbulence modifiers.

## Steps
1. Emitter Shape **Rectangle → Object**, drag in the **Torus**. Emit From **Polygon Center** (default) → **Polygon Area** for even surface distribution.
2. **Falloff** tab: shape **Infinite → Sphere**; move it to emit only inside (reset to Infinite afterwards).
3. **Topology** tab ▸ **Height**: Min **0** (object origin, torus middle) / Max **50** (top) → only upper half emits. Slope and Curvature work the same way.
4. Edit the topology **spline curve**: drop the first knot → fewer particles low down = feathered edge; slide it to tune the fade.
5. Random patches: new material, Color ▸ **Noise** shader type **Stupl**, Space **Texture → UV**, raise Low Clip / lower High Clip for contrast, **Animation Speed 0.5**; enable **Animate Preview** in viewport settings.
6. Emit From **Texture** → Texture tab, drag in the texture tag, use the **Color** channel (others off) → particles only from light, moving bands.

## Newest equivalent
NeXus 2026.1 **nxFalloff** (16 modes incl. Curvature, Noise) can mask modifiers the same way after emission; see also recipe 2023-12-05 for texture-driven radius/speed/offset.
