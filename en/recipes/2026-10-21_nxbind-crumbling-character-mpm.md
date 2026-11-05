# Walking character crumbling to sand (nxBind + falloff release + nxMPM brittle)

- Source: NeXus Official Training — nxBIND — https://www.youtube.com/watch?v=-QzOnmifveY (2026-10-21)
- Host / generation: Blender (NeXus for Blender, 2026.1 beta); nxEmitter, nxBind, nxKill, nxFalloff, nxMPM, nxGravity
- Goal: particles fill an animated Alembic zombie, follow its walk, then break off head-first in chunks and pile up as crumbly sand.

## Base
Low-poly, cleanly remeshed character with as little self-intersection as possible (folds behind the knees cause stray particles).

## Steps
1. **nxEmitter**: Shape Object (the zombie), emit from **Volume**, grid mode **Hexagonal**, Shot, speed 0. In hexagonal mode the radius sets the count (0.01 → ~13k particles for testing). [▶ 1:40](https://youtu.be/-QzOnmifveY?t=100)
2. **nxBind** modifier: Object = same zombie, defaults → particles ride the deforming volume. [▶ 3:01](https://youtu.be/-QzOnmifveY?t=181)
3. Clean strays: **nxKill**, Volume = Object (zombie), toggle the inside/outside icon so it kills particles **outside**. Keyframe **Enabled** off after the first frames (~frame 52) so released particles aren't killed later. [▶ 4:12](https://youtu.be/-QzOnmifveY?t=252)
4. nxBind ▸ **Break** tab — release by Falloff (default; nothing releases without a falloff), Particle Age (e.g. 60→150 frames), or Color Brightness (paint a spreading color). **Chunks** on; **Chunk Size** ~0.3 for bigger pieces; turn **Soften** off when a fluid solver takes over (sharp bound/released). [▶ 6:36](https://youtu.be/-QzOnmifveY?t=396)
5. Release top-down: Break = Falloff; add a **Linear falloff** set to **+Z**, small, above the head; keyframe its Z sweeping down to the feet (keep feet bound so they kick through the debris). [▶ 8:55](https://youtu.be/-QzOnmifveY?t=535)
6. **nxMPM** with a domain (optional — sparse — but a domain gives tighter control and a faster solve). Display ▸ Draw Grid (Back) to see voxels. [▶ 10:23](https://youtu.be/-QzOnmifveY?t=623)
7. Emitter ▸ **Match Solver Resolution** → nxMPM; the radius is now driven by the solver. Resolution 40 → ~600 particles; **150** → ~30k (demo, not production). [▶ 11:50](https://youtu.be/-QzOnmifveY?t=710)
8. **nxGravity**. MPM material Liquid → a **Brittle** preset (**Concrete**) for crumbly sand. Slower to solve (more accurate). [▶ 12:35](https://youtu.be/-QzOnmifveY?t=755)
9. MPM object ▸ bottom: add **Wall Friction** so debris stops sliding. [▶ 13:15](https://youtu.be/-QzOnmifveY?t=795)
10. Emitter Display: gradient by **Granular**, Auto Scale off, max ~20 to read the chunks. [▶ 13:30](https://youtu.be/-QzOnmifveY?t=810)

## Gotchas
- Overlapping/internal geometry breaks the inside/outside test — remesh first.
- Don't leave the outside-volume kill active once particles start releasing.

## Newest equivalent
This is already the newest route (2026.1 beta). Legacy CPU had no direct equivalent (xpSticky/xpCover-style tricks); nxPin is the sibling tool when particles should be anchored rather than carried inside a volume.
