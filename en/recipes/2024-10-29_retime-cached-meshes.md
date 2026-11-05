# Slow-motion ramp on a meshed fluid (retime particle cache, then cache the mesher from retimed particles)

- Source: Top Tip Tuesday — Retime Cached Meshes — https://www.youtube.com/watch?v=SiDN-95Yk88 (2024-10-29)
- Host / generation: C4D; **xpCache** retiming + CPU xpOpenVDBMesher
- Goal: smooth slow-mo on one splash, for particles and mesh.

## Steps
1. xpCache ▸ Playback ▸ Retiming **Time (seconds)**: key 0 s at frame 0 and 500/30 = **16.6 s** at the last frame; curve **Linear**. [▶ 0:52](https://youtu.be/SiDN-95Yk88?t=52)
2. Add two keys around the splash, select both, slide right → flat section = slow motion. [▶ 1:56](https://youtu.be/SiDN-95Yk88?t=116)
3. Particles interpolate smoothly **only with a fixed particle count** (all born at frame 0); dynamically spawned foam can't be filled in. [▶ 2:53](https://youtu.be/SiDN-95Yk88?t=173)
4. A cached mesh steps (topology changes every frame) → delete the mesh cache, then **Build Cache ▸ Continue** — particles play back retimed, mesher is cached from them. [▶ 4:12](https://youtu.be/SiDN-95Yk88?t=252)
5. Fix double retiming: on the **mesher's cache tag ▸ Override** playback, default 100 % (real time). [▶ 5:36](https://youtu.be/SiDN-95Yk88?t=336)
6. Same workflow works for retimed trails.

## Newest equivalent
nxMesher (GPU) meshing of the retimed cache in Fused 2025.4+.
