# Procedural greeble panels (mtSubdivider driven by noise + mtInset with variation, twist and a spherical field)

- Source: Top Tip Tuesday — MeshTools Greeble — https://www.youtube.com/watch?v=V2U7P7K1pws (2023-06-13)
- Host / generation: C4D; MeshTools (mtSubdivider, mtInset)
- Goal: turn a default plane into dense, irregular sci-fi panel detail, fully procedural and animatable.

## Steps
1. INSYDIUM ▸ MeshTools ▸ **mtSubdivider**; plane as child (MeshTools objects act on their children). Subdivisions **5**.
2. Restrict where it subdivides: driver options are material, selection tag, vertex map, field or **Shader** → choose **Noise**, type **Luka**, lower **High Clip**, Global Scale **300%** → patchy subdivision. [▶ 1:27](https://youtu.be/V2U7P7K1pws?t=87)
3. Test **mtInset** on its own with the plain plane: **Amount** = inner-extrude-style inset; add **Variation**, **Offset** (extrudes the inner face up) with variation. [▶ 2:02](https://youtu.be/V2U7P7K1pws?t=122)
4. **Divisions 6** on the new side faces, then **Twist** with variation for rotated inner faces. [▶ 2:56](https://youtu.be/V2U7P7K1pws?t=176)
5. Chain: plane → inside mtSubdivider → inside mtInset → insets on the irregular subdivided polys. Change the noise **Seed** in the subdivider to browse variants. [▶ 3:36](https://youtu.be/V2U7P7K1pws?t=216)
6. mtInset ▸ Fields: **Spherical field** → only polys inside get inset; field Remapping ▸ Contour/control mode **Curve** for a softer transition. [▶ 4:39](https://youtu.be/V2U7P7K1pws?t=279)
7. mtInset ▸ **Advanced**: choose which values the field affects (Inset, Offset, Twist all by default). Untick Inset → everything stays inset, the field only drives offset and twist. [▶ 4:46](https://youtu.be/V2U7P7K1pws?t=286)

## Newest equivalent
Same MeshTools objects in Fused 2025.x; Fused 2024.2 added **mtPolyFold** and **mtPointProject** for further procedural detail. See "mtInset layered growth" (2024-11-26).
