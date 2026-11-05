# Shader-driven emission: radius, speed, color and topographic offset (xpEmitter Emit from Texture)

- Source: Top Tip Tuesday — xpEmitter Advanced Emission — https://www.youtube.com/watch?v=Dco0kD_UD4Q (2023-12-05)
- Host / generation: C4D; CPU xpEmitter (emission feature, works with any downstream solver)
- Goal: control where particles are born and their radius, speed, color and surface offset from a C4D shader in a material.

## Base
**xpEmitter** from a plane, emission mode Simulate, **Random Shot 30,000**, radius **3 cm**, speed 0, display Spheres. Material on the plane: only **Luminance** active.

## Steps
1. Luminance ▸ **Noise** shader, type **Luka**, Global Scale **300%**, add contrast, raise octaves, try seeds.
2. Emitter ▸ Object: Emit from **Texture** → new **Texture** tab; drag in the plane's texture tag; set every channel to None first.
3. **Emit** channel = Luminance → particles only from light areas; the emitter's **Contrast** raises the threshold (turned off again for the final look).
4. **Color** channel = Luminance → particles take the shader colors.
5. **Radius** channel = Luminance — needs radius **variation** in the Emission tab (e.g. 2 ±1.5; demo 10 ±9 to exaggerate): white = radius + variation, black = radius − variation.
6. **Speed** channel = Luminance with speed variation (e.g. 20 ±15) → light areas fly faster (not kept).
7. **Offset** channel = Luminance, then raise Emission ▸ **Offset Origin** → bright areas lift off the surface = topographic relief.
8. Final: Radius channel off (random radius **1.5 ±1.3**), push to **100,000** particles for detail.

## Gotchas
- A texture channel does nothing until the matching range (variation / Offset Origin) is set in the Emission tab.

## Newest equivalent
Still done on the xpEmitter in Fused. In the 2026.1 beta, **Attribute / Noise nxFalloff** modes (or nxFalloffMap in C4D) plus NeXus **Mapping** can drive radius/speed per particle after birth.
