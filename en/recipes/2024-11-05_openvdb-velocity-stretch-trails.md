# Speed-stretched meshes and vertex color (xpOpenVDBMesher Point Radius, Transfer Velocity, Trails source)

- Source: Top Tip Tuesday — Mesh Velocity Stretch — https://www.youtube.com/watch?v=-4wYDCnis9M (2024-11-05)
- Host / generation: C4D; **CPU xpOpenVDBMesher** (pre-nxMesher)
- Goal: bouncing colored particles meshed into blobs with motion-stretched tails.

## Steps
1. Particles r 3 cm, Gradient Random color, gravity + floor. [▶ 0:27](https://youtu.be/-4wYDCnis9M?t=27)
2. **xpOpenVDBMesher** with the emitter: default **Point Radius 10 = 10 × particle radius** (30 cm spheres). [▶ 1:17](https://youtu.be/-4wYDCnis9M?t=77)
3. Exact size: Point Radius **1** → needs finer voxels: **Voxel size 4 → 1** (else spheres vanish). [▶ 2:52](https://youtu.be/-4wYDCnis9M?t=172)
4. Tags ▸ **Transfer Point Color** → vertex color tag; a little color **smoothing** cleans seams. [▶ 3:29](https://youtu.be/-4wYDCnis9M?t=209)
5. Tags ▸ **Transfer Velocity** → combined color-vertex tag + separate X/Y/Z tags (also usable for render motion blur). [▶ 4:41](https://youtu.be/-4wYDCnis9M?t=281)
6. General ▸ Source **Point Type: Trails** → tails proportional to speed; **Velocity Factor ~4**. [▶ 5:17](https://youtu.be/-4wYDCnis9M?t=317)
7. **Trails Delta**: low = smooth stretch; high = visible bead chains (stylised / toon look). [▶ 6:42](https://youtu.be/-4wYDCnis9M?t=402)

## Newest equivalent
**nxMesher** (Fused 2025.4) on the GPU with Export Tags (color, velocity) — see "nxMesher Export Tags".
