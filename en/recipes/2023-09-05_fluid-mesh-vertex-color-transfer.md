# Gloopy fluid meshed with particle colors carried into the mesh (nxFluids SPH + nxConstraints Viscosity, xpOpenVDBMesher Transfer Point Color)

- Source: Top Tip Tuesday — nxFluids Vertex Color — https://www.youtube.com/watch?v=fvS3h7uk35s (2023-09-05)
- Host / generation: C4D; G2 NeXus (nxFluids, nxConstraints, nxGravity) + **CPU xpOpenVDBMesher**; Standard material (any renderer works)
- Goal: a colorful viscous pour whose mesh keeps the per-particle gradient colors for shading.

## Base
xpEmitter with a Vibrate tag, **Hexagonal** emission, speed 0, particle radius **1 cm**; **nxGravity strength 400 cm**; colliders on the props. Color: emitter Display ▸ Color mode **Shader** → Gradient shader, **3D Linear**, **Cycle** on.

## Steps
1. **nxFluids**, solver **SPH**, rest default.
2. **nxConstraints**: Iterations **3**, add a **Viscosity** constraint, search Radius **20**, max connections **3** → gloopy.
3. Generators ▸ **xpOpenVDBMesher**, drag the xpEmitter into its list. Voxel size **3** for more polygons.
4. Point Radius (default 10 = 10× particle radius): lower it step by step until the mesh thins; at **2** it vanishes, **5** keeps enough depth to survive smoothing.
5. Filters: delete the default Median; instead of Gaussian (too aggressive, eats small blobs) use **Curvature**, raising iterations — smooths bumps, keeps flat areas and detail.
6. Hide the particles. Mesher ▸ Tags ▸ **Transfer Point Color** → vertex color tag on the mesher; add a little **color smoothing** in the mesher's tag settings to clean polygon-edge artifacts.
7. Material: Reflectance **Beckmann** layer + **Dielectric Fresnel** with a water-like IOR; Color channel texture ▸ Effects ▸ **Vertex Map**, drop the color vertex tag in. Works live on playback and in third-party renderers via their vertex-color node.

## Gotchas
- More particles = cleaner mesh; Point Radius too low with a coarse voxel size kills the mesh.

## Newest equivalent
GPU **nxMesher** (Fused 2025.4) outputs color/velocity tags directly with layered smoothing; FLIP/APIC with variable viscosity, or 2026.1 non-Newtonian settings, replaces the SPH + viscosity-constraint trick. See "Speed-stretched meshes and vertex color" (2024-11-05).
