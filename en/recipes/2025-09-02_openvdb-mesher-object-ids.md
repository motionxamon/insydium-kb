# One mesh, a different material per emitter (xpOpenVDBMesher Object IDs → Redshift)

- Source: Top Tip Tuesday — Particle Mesh IDs — https://www.youtube.com/watch?v=e49Ob7tPXfc (2025-09-02)
- Host / generation: C4D, CPU **xpOpenVDBMesher** + cached viscous NeXus sim + Redshift
- Goal: three colored goos from three emitters, meshed together, shaded separately.

## Steps
1. **xpOpenVDBMesher** with the 3 emitters; **Voxel 1.5**; **Point Radius 4** (default 10 = ×10 particle radius, too blobby). [▶ 1:22](https://youtu.be/e49Ob7tPXfc?t=82)
2. Filters: remove Median, **Curvature** ×7 iterations ("99 % of the time for fluids"). [▶ 1:53](https://youtu.be/e49Ob7tPXfc?t=113)
3. Per emitter in the mesher list: **Object ID** (vertex map) + **Smoothing 7** (feather the seams). [▶ 3:57](https://youtu.be/e49Ob7tPXfc?t=237)
4. Redshift: three SSS Standard materials (pink / green / orange, SSS scale ~10) → **Material Blender**: base pink; Layer 1 = green with Blend Color = **Vertex Attribute (ID map 1)**; Layer 2 = orange with Blend Color = Vertex Attribute (ID map 2) (Ctrl-click to expose layer inputs). [▶ 7:41](https://youtu.be/e49Ob7tPXfc?t=461)

## Newest equivalent
**nxMesher** Export Tags ▸ **Emitter ID** buttons do the same on the GPU (see "nxMesher Export Tags").
