# Upres a cached low-count sim into a dense one (xpCache + nxUpres Velocity / Position / Push)

- Source: Top Tip Tuesday — nxUpres — https://www.youtube.com/watch?v=RfvvtXkG8Y0 (2023-07-11)
- Host / generation: C4D; G2 NeXus (nxUpres, nxTurbulence — new in Fused 2023.3) + CPU xpCache
- Goal: turn a sparse pulsed turbulence sim into a detailed velocity explosion, with no modifiers needed on the high-res emitter.

## Base
xpEmitter "base" in **Ring** mode, **Pulse** every **60** frames, **60** particles per pulse; **nxTurbulence strength 15**.

## Steps
1. **xpCache** ▸ cache to **internal memory** ▸ Build Cache. The turbulence can now be deleted — motion is read from the cache. [▶ 0:53](https://youtu.be/RfvvtXkG8Y0?t=53)
2. Copy the emitter, rename "upres", delete its cache tag; Display: green, **Dots**. Emission (still Pulse/60) → **2,000** particles per pulse. [▶ 1:50](https://youtu.be/RfvvtXkG8Y0?t=110)
3. NeXus ▸ **nxUpres**: Source = cached base emitter, **Destination** = upres emitter. Defaults → green particles follow the pink cached ones (velocity blended in). [▶ 1:29](https://youtu.be/RfvvtXkG8Y0?t=89)
4. Hide the base emitter. Upres emitter: untick full lifespan → Life **70**, variation **20** → regular pulses. [▶ 3:15](https://youtu.be/RfvvtXkG8Y0?t=195)
5. Clumping: **Max Count** (base neighbours blended per upres particle) default **3** → **15**; max **64** (smoother but slower). [▶ 3:43](https://youtu.be/RfvvtXkG8Y0?t=223)
6. Transferable data: velocity, radius, color, group, mass, **position**. Position instead of velocity makes them collapse onto parents; enable **Push** to spread them into diffuse blobs; lower **Push Distance** → droplet look. [▶ 4:47](https://youtu.be/RfvvtXkG8Y0?t=287)
7. For the explosion look keep **Velocity** only, Push off. [▶ 4:45](https://youtu.be/RfvvtXkG8Y0?t=285)

## Newest equivalent
nxUpres exists unchanged in NeXus 2026.x (C4D and Blender) with **nxCache** as the source; 2026.1 adds nxCache Disk Reserve/Alembic. See "Upres granular sim" (2025-04-15) and "Upres explode position/velocity blend" (2025-05-27).
