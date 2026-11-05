# Particle rotation basics (emitter Use Rotation: Set / Tangential / None + xpSpin random spin)

- Source: Top Tip Tuesday — Particle Rotation — https://www.youtube.com/watch?v=jdlkfgR8Zy8 (2023-02-28)
- Host / generation: C4D; CPU X-Particles (xpEmitter, xpTurbulence, xpSpin)
- Goal: arrows that point along their travel, or cubes that tumble randomly like floating dust.

## Base
Default **xpTurbulence** swirling **Arrow**-display particles — they all point +Z regardless of motion.

## Steps
1. Emitter ▸ Extended Data ▸ General ▸ **Use Rotation** (off by default to save processing). [▶ 1:06](https://youtu.be/jdlkfgR8Zy8?t=66)
2. Mode **Set**: fixed Heading/Pitch/Bank (e.g. Pitch 90 → all point up). Back to 0. [▶ 1:30](https://youtu.be/jdlkfgR8Zy8?t=90)
3. Mode **Tangential** → each particle continuously aligns to its direction of travel. [▶ 2:02](https://youtu.be/jdlkfgR8Zy8?t=122)
4. Random tumbling: display **Box Filled**; Modifiers ▸ Motion ▸ **xpSpin** (operation Spin, per frame, e.g. 3° per axis). [▶ 2:57](https://youtu.be/jdlkfgR8Zy8?t=177)
5. xpSpin does nothing until the emitter has rotation data: Use Rotation on, mode **None** (emitter doesn't drive rotation, the modifier does). [▶ 4:08](https://youtu.be/jdlkfgR8Zy8?t=248)
6. Organic variety: spin amount back to 0, enable **Random Spin ~2°** per axis → each particle spins at its own rate. [▶ 4:43](https://youtu.be/jdlkfgR8Zy8?t=283)

## Gotchas
Any rotation effect (spin, align, tangential) needs Use Rotation enabled on the emitter.

## Newest equivalent
GPU: **nxSpin** / **nxRotate** (layered nxSpin since Fused 2025.4).
