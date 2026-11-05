# Polygon-by-polygon disintegration driven by particles (xpFragmenter Faces Polys, xpWind with linear field, xpTurbulence mapped to distance travelled)

- Source: Top Tip Tuesday — xpFragmenter Destruction — https://www.youtube.com/watch?v=zA3IYXmyi5Q (2023-06-20)
- Host / generation: C4D; G1 CPU X-Particles (xpEmitter, xpFragmenter, xpWind, xpTurbulence, xpCollider)
- Goal: a wolf model peels apart face by face as a wind front sweeps across it, then the faces tumble in turbulence.

## Steps
1. New **xpEmitter**, Shape **Object** = wolf, emit from **Polygon Center**, **One Particle per Source Element**; Emission **Shot**, Speed **0** → one particle per polygon.
2. Generators ▸ **xpFragmenter**, link the emitter (wolf as child just for tidiness). Mode **Faces (Polys)** = one object holding separate polygons (Faces (Objects) makes one object per polygon — heavy).
3. Hide the original wolf and the particles. Enable **Connect Polys** for smooth shading.
4. Copy the wolf's texture tag onto the xpFragmenter and tick **Remap Textures** (otherwise the texture maps per polygon).
5. **xpWind**, rotated 90° to blow across the head; strength lowered to **85 cm**.
6. Wolf (hidden) ▸ **xpCollider** tag: lower bounce, some friction → faces bounce off the intact shape.
7. **xpTurbulence**: Scale **30**, Strength **8**.
8. Turbulence ▸ **Mapping**: Turbulence **Strength** mapped to **Distance Travelled**, range **0 → 30 cm**; pull the curve start in so the first few cm get no turbulence (wind moves them first).
9. xpWind ▸ Fields: **Linear field** facing **−Z**, keyframed on Z to sweep across the scene → nothing moves until the front arrives.

## Newest equivalent
GPU route today: drive particles with **nxWind**, **nxTurbulence** (mapping Distance-type data in the NeXus Mapping tab) and an animated **nxFalloff**; in NeXus 2026.1 **nxDeformer** (mesh follows particles, with tearing) or **nxShatter** for chunkier breakup. xpFragmenter itself has no nx counterpart listed, so keep it for per-face disintegration.
