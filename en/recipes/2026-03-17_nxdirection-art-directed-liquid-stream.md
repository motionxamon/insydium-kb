# Art-directed gloopy liquid stream (PBD + nxDirection + nxMesher)

- Source: Top Tip Tuesday — Direction Force — https://www.youtube.com/watch?v=pbO2aDK4to8 (2026-03-17)
- Host / generation: C4D, Fused 2025.4+ (nxDirection new in 2025.4, nxFluids PBD, nxMesher, nxColor neighbour search)
- Goal: erratic, tendrilly liquid stream you can steer precisely and mesh in near real time.

## Scene tree
```
nxDirection (Direction Force layer)  ← rotate/animate to steer
  └─ xpEmitter (stream)   (child → emitter follows the direction)
nxTurbulence (Voronoi layer)
nxFluids PBD: External Pressure 100%, Attraction ↓, Repulsion ↑, **Smoothing Radius 150%** (gloopy tendrils)
nxColor: Gradient (Parameter) = Neighbors within 15 cm, 20 → purple … 200 → yellow
nxMesher: emitter, smaller radius, Polygon Size 3, **Zhu-Bridson**, Export Tags ▸ Transfer Color, Smoothing iterations 5 (color)
```

## Steps
1. PBD is the least "physical" solver but ideal for stylised streams; the key to gloop is **Smoothing Radius ~150%** plus full external pressure. [▶ 1:08](https://youtu.be/pbO2aDK4to8?t=68)
2. Stream loses momentum under turbulence → **nxDirection** Direction Force (red arrow = direction), **Direction strength ~180**. [▶ 3:22](https://youtu.be/pbO2aDK4to8?t=202)
3. **Twist strength** spirals particles around the line (negative = other way); twisting pushes them outward, so add **Attract strength ~250** to pull back to the line. [▶ 4:20](https://youtu.be/pbO2aDK4to8?t=260)
4. Animate the nxDirection to aim the stream anywhere — turbulence randomness is kept. [▶ 4:38](https://youtu.be/pbO2aDK4to8?t=278)
5. Mesh with **nxMesher Zhu-Bridson** (smooth without smoothing layers), transfer particle color to a vertex color tag; smoothing iterations blend color patches. [▶ 5:31](https://youtu.be/pbO2aDK4to8?t=331)
