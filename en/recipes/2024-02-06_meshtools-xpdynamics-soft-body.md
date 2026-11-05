# Organic wobbling spiky ball (mtSubdivider + mtInset on an xpDynamics soft body)

- Source: Top Tip Tuesday — Dynamic MeshTools — https://www.youtube.com/watch?v=3YmhMKdK0o4 (2024-02-06)
- Host / generation: C4D; MeshTools (mtSubdivider, mtInset) + CPU X-Particles (xpDynamics tag, xpTurbulence, xpAttractor)
- Goal: procedural animated geometric spikes riding a squashy soft-body sphere.

## Steps
1. Sphere, type **Icosahedron**. [▶ 0:14](https://youtu.be/3YmhMKdK0o4?t=14)
2. **mtSubdivider** (sphere as child): level **5**, driven by a **Noise shader** type **Box** with lowered High Clip → uneven subdivision. [▶ 0:45](https://youtu.be/3YmhMKdK0o4?t=45)
3. **mtInset** (subdivider as child): raise Amount and Offset → spikes. [▶ 1:08](https://youtu.be/3YmhMKdK0o4?t=68)
4. Inset **Fields ▸ Random field**: Perlin, scale ~530, animation speed 20% → rippling spikes; raise Offset to exaggerate. [▶ 1:41](https://youtu.be/3YmhMKdK0o4?t=101)
5. Disable MeshTools; on the sphere add **xpDynamics tag ▸ add Emitter** (one particle per vertex). [▶ 3:02](https://youtu.be/3YmhMKdK0o4?t=182)
6. **xpTurbulence**: scale 150, strength 15. [▶ 3:25](https://youtu.be/3YmhMKdK0o4?t=205)
7. Dynamics tag **Rigidity** 0.5 → 0.1 (floppy). **xpAttractor** (default) keeps it centred; **Pressure 0.5**; rigidity back up to **0.4** to hold shape. [▶ 3:43](https://youtu.be/3YmhMKdK0o4?t=223)
8. Re-enable MeshTools — procedural spikes now ride the dynamic mesh. Random field ▸ Remapping ▸ Contour **Curve** for spikier contrast. [▶ 5:35](https://youtu.be/3YmhMKdK0o4?t=335)

## Newest equivalent
GPU soft bodies: **nxMPM elastic** + **nxDeformer** (2026.1 beta), with nxTurbulence/nxAttract.
