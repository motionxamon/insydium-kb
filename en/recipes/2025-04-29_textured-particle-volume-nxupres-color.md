# Volume particle cloud coloured by an object's UV texture (texture surface emitter + nxUpres Color + Initial State)

- Source: Top Tip Tuesday — Textured Particle Volume — https://www.youtube.com/watch?v=N32nQXnqMLE (2025-04-29)
- Host / generation: C4D; NeXus inside X-Particles (nxUpres, nxTurbulence) on xpEmitters; Redshift for render
- Goal: a solid (filled) particle version of a textured model, coloured throughout, ready to simulate.

## Base
Content-browser mushroom (~10 cm, UV-mapped texture). Surface emitter: Object mode, **Shot Random, 500,000 particles, radius 0.04, speed 0**.

## Steps
1. Surface emitter ▸ Object ▸ emit from **Texture**; Texture tab: drag in the model's texture tag, **Emit channel None** (everywhere), **Color channel = Color** → coloured shell only.
2. Duplicate → "emitter volume": **Shot Hexagonal** (fills the volume at the particle radius) + small X/Y/Z **Jitter**. Volume has depth but no colour (textures can't colour a volume).
3. **nxUpres**: Source = surface emitter, Destination = volume emitter; untick Velocity, tick **Color**. Each volume particle blends its 3 nearest surface colours. Hide surface particles, step one frame.
4. Volume emitter ▸ **Initial State ▸ Set State**; Emission → **Controlled Only**. Disable the surface emitter and nxUpres.
5. Render: material with **Color User Data (Particle Color)**, **Redshift Object tag ▸ Sphere instances**. Simulate freely (demo: nxTurbulence; works for granular crumble too).

## Newest equivalent
Same pattern in NeXus 2026 (nxEmitter Initial State, nxUpres). In the 2026.1 beta nxEmitter can also emit from point clouds / Gaussian splats, which carry their own colour.
