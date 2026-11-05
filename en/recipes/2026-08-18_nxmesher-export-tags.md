# nxMesher export tags: emitter IDs, particle color, velocity motion blur (Redshift)

- Source: Top Tip Tuesday — nxMesher Export Tags — https://www.youtube.com/watch?v=Aqa8DG6jrA8 (2026-08-18)
- Host / generation: C4D, Fused 2025.4+ (GPU nxMesher) + Redshift (same principle for Octane/Cycles 4D)
- Goal: one fluid mesh from two emitters, rendered with two materials, particle colors and vector motion blur.

## Meshing settings that worked
- Layers: both emitters. **Surface Size: Source** (mesh = particle size) → needs small **Polygon Size** (~1.5–2 cm).
- **Surface Type: Zhu-Bridson** (natural smooth liquid) instead of Spheres; Source scale **200%** for padding so small clumps mesh.
- Add a **Smoothing** layer → switch Gaussian to **Laplacian** (keeps volume — good for fluids), raise Strength, **3 iterations** → thin stringy strands without losing resolution.

## Export Tags tab
1. **Emitter ID** buttons → vertex map per emitter (with two emitters one map is enough: black = A, white = B).
2. **Transfer Color** → vertex color tag with particle colors.
3. **Transfer Velocity** → vel X/Y/Z maps + one **color velocity** map; set **Max Velocity** to your real max speed (default 200 cm/s).

## Redshift material
- Two Standard materials (blue subsurface; orange metal) → **Material Blender**: base = subsurface, layer = metal, **Blend Color = Vertex Attribute (Emitter ID map)**.
- Particle color: **Vertex Attribute** node with the color tag → subsurface color / metal base color; add **Color Correct** (Level) to adjust.
- Motion blur: **Redshift Object tag** on the mesher → Motion Blur → Motion Vector: drag the single **color velocity** map into X (leave Y/Z empty; or use the three separate maps). Scale ~5–20 if Max Velocity is lower than the real speed. Render Settings ▸ Advanced ▸ **Motion Blur + Deformation Blur** on. Not visible in the live IPR — do a real render.

## Gotchas
- Cache the mesher for final renders (first frame "prepares" slowly).
- 2026.1 beta adds UV advection, Detail Aware smoothing and nxGroups as source to nxMesher.
