# Abstract liquid with neighbour-count color bands (nxColor neighbour search → mesh → glass ramp)

- Source: Top Tip Tuesday — Neighbor Search Color — https://www.youtube.com/watch?v=-GELMnDapCc (2025-12-02)
- Host / generation: C4D, Fused 2025.4 (then beta: nxColor Neighbor mode, nxMesher) + Redshift
- Goal: colorful stripes flowing through a fluid, driven by how crowded each particle is.

## Steps
1. Basic fluid sim (nxTurbulence + nxFluids + nxGravity), top-down camera. [▶ 0:34](https://youtu.be/-GELMnDapCc?t=34)
2. **nxColor** Gradient (Parameter) → **Neighbor**: radius 40 cm, range 0–8000 neighbours; black→white preset (color later in render). [▶ 2:45](https://youtu.be/-GELMnDapCc?t=165)
3. Duplicate the layer (top): ramp knots interpolation **Step**, radius **10**, range 0–200, move the white knot → only **edge/perimeter** particles black. Set this layer's blend **Multiply** → black outlines over the soft gradient below. [▶ 2:45](https://youtu.be/-GELMnDapCc?t=165)
4. Cache (~80 s for 270 frames). [▶ 4:35](https://youtu.be/-GELMnDapCc?t=275)
5. **nxMesher**: Polygon Size 1.5, radius 2.5, Smoothing **Mean Curvature** full, 5 iterations; **Transfer Color** + color smoothing 5 (soft color transitions). [▶ 5:22](https://youtu.be/-GELMnDapCc?t=322)
6. Redshift glass (Transmission 1): **Vertex Attribute** (color map) → **Ramp** with custom colors → transmission color → animated stripes. [▶ 7:17](https://youtu.be/-GELMnDapCc?t=437)
