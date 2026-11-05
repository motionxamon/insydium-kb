# Arid dry-riverbed terrain with heightfield scatter (tfNoise Advanced, tfRiver, tfDistribute, tfFlood)

- Source: INSYDIUM LIVE! — February 2024 – Open Beta Preview, TerraformFX — https://www.youtube.com/watch?v=Foe7aTVhbYs (2024-02-21)
- Host / generation: C4D; TerraformFX (open beta → Fused 2024.2: new noise generator, tfDistribute, Advanced Terrain Shader); viewport/Standard shading
- Goal: dune desert with a dry river channel, scattered boulders, pebbles, scrub bushes and murky pools — without scattering real geometry.

## Base
tfTerrain (default 500×500 segments — keep low while iterating), delete the default erosion and grid operators; a river spline across the terrain. In the Advanced Terrain Shader remove the grass layer, set base rock to Surfaces ▸ **Sand**, Normalize off, a little Variation + Jitter.

## Steps
1. **tfNoise** ▸ Properties ▸ mode **Advanced** (new fractal noises; Maxon noises still available): **Simplex Fractal**, large Scale, more Gain, **Octaves ~3** for big smooth dunes. The noise is a movable object — slide it in 3D instead of changing seeds, so a gully lines up with the river spline. [▶ 24:26](https://youtu.be/Foe7aTVhbYs?t=1466)
2. Second **tfNoise** (Advanced, **Cubic Fractal**): fine — raise Lacunarity and Persistence, low Gain, enable fractal **Warp** → water-carved rivulets. [▶ 26:11](https://youtu.be/Foe7aTVhbYs?t=1571)
3. **tfRiver** placed between the two noises, Spline mode with the river spline: even width/depth curves, wider, deeper; lower its noise Strength (dunes don't need it). [▶ 27:11](https://youtu.be/Foe7aTVhbYs?t=1631)
4. **tfDistribute** "large rocks": scatters **height-field bumps**, not geometry. Shape Flat / Round / Cone / Spike / Custom (any object, e.g. a logo) — Round here. Count 1500 → **800**, Deform medium, raise Elevation and Size. Distribution layers: Altitude / Slope / AO / Noise / Shader / Fields — **Altitude** with Min/Max to keep them in the low channel. [▶ 28:28](https://youtu.be/Foe7aTVhbYs?t=1708)
5. Click **Add Rock Layer**: the shader gets an **Object layer + Object mask** linked to the distribute (mask source: Altitude, Slope, Difference map or **Object IDs** for per-rock variation). Pick a sandy rock palette. [▶ 29:24](https://youtu.be/Foe7aTVhbYs?t=1764)
6. tfDistribute "small rocks": Size ~3, low Elevation, Count **50,000**, Altitude min raised to climb the banks, plus a **Noise** distribution layer with softness → natural patches. [▶ 33:23](https://youtu.be/Foe7aTVhbYs?t=2003)
7. tfDistribute "bush": **Add Tree Layer**, Shape **Cone**, taller, Altitude pushed to the high ground; lower the layer blend to sprinkle a few elsewhere; brownish-green palette. [▶ 34:20](https://youtu.be/Foe7aTVhbYs?t=2060)
8. **tfFlood**: flattens the lowest areas; raise the level until pools appear in the riverbed, **add its layer** and pick a murky green palette. The layer uses the flood as a difference map, faking transparent refracting water with rocks "visible" below. [▶ 36:16](https://youtu.be/Foe7aTVhbYs?t=2176)
9. Low light angle while working to read the detail; everything stays procedural — resize the terrain and it rebuilds. [▶ 36:49](https://youtu.be/Foe7aTVhbYs?t=2209)

## Gotchas
- tfDistribute is for distance/drone/background shots; for close-ups instance real rocks/trees.

## Newest equivalent
Same tools are current (Fused 2024.2+). No newer TerraformFX scatter tool is listed; for real instanced geometry over a terrain the 2026.1 beta adds nxScatter (points on meshes → nxGenerator).
