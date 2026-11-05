# Speed-driven glowing lava on cached instanced particles (Redshift User Data Vector velocity → Vector Length → Incandescent)

- Source: Top Tip Tuesday — Redshift Particle Velocity — https://www.youtube.com/watch?v=8A0hvOpOscU (2024-08-13)
- Host / generation: C4D; cached X-Particles emitter (render-time data only); **Redshift** node material
- Goal: fast particles glow white-hot, slow ones stay shiny/dark, even though particle color in the cache is a noise pattern.

## Base
Cached melting/solidifying sim; emitter has a **Redshift Object tag ▸ Custom Objects** instancing a cube, platonic and pyramid. One RS area light. With instanced geometry the **material goes on the instanced objects**, not the emitter.

## Steps
1. Standard RS Material (default reflections give the glints). Open the node editor. [▶ 1:09](https://youtu.be/8A0hvOpOscU?t=69)
2. **User Data Vector** node, attribute from presets ▸ Particle ▸ **Velocity** (the XP velocity attribute). [▶ 2:21](https://youtu.be/8A0hvOpOscU?t=141)
3. **Vector Length** (Vector Math) → turns the vector into a scalar speed. [▶ 2:56](https://youtu.be/8A0hvOpOscU?t=176)
4. **Change Range**: old min 0, old max = the sim's speed cap (**70** — the speed modifier clamped speed to 70 cm in this cache) → 0–1. [▶ 3:28](https://youtu.be/8A0hvOpOscU?t=208)
5. **Scalar Ramp** with a contrast curve, pulled darker so only the fastest bits light up. [▶ 4:38](https://youtu.be/8A0hvOpOscU?t=278)
6. **Incandescent** material, mode **Temperature**, lower the temperature for a white→orange range; Ctrl-click Intensity Multiplier to expose its input and feed the ramp. [▶ 5:26](https://youtu.be/8A0hvOpOscU?t=326)
7. **Material Blender** → Surface: base = Standard material, Layer 1 = Incandescent, blend color white, **Additive** on. [▶ 6:14](https://youtu.be/8A0hvOpOscU?t=374)
8. Strength slider: **Math Multiply** between ramp and intensity; input 2 = strength (**2** for hotter). [▶ 6:54](https://youtu.be/8A0hvOpOscU?t=414)

## Gotchas
- Know your max speed (check the speed limit in the sim) or the remap will clip/underuse the range.
- Add glow in post if needed.

## Newest equivalent
Same Redshift chain works for NeXus caches; in Blender (NeXus 2026) the **Particle Info** shader node is the route to per-particle data.
