# Render mtRayLine rays + trails as additive gradient curves inside displaced glass (Redshift)

- Source: Top Tip Tuesday — Redshift Rayline — https://www.youtube.com/watch?v=K560tf-sU0I (2025-06-03)
- Host / generation: cached NeXus sim + **MeshTools mtRayLine** + xpTrail + Redshift
- Goal: glowing tendrils, rays and trails seen through a displaced glass sphere.

## Steps
1. Elements: emitter particles (tendrils) → mtRayLine casts rays to an inner sphere → contact-point particles → xpTrail.
2. Render sphere = slightly bigger copy; glass Standard with Maxon Noise on roughness + displacement → Redshift Object tag ▸ Geometry ▸ **Tessellation + Displacement on** (5/5).
3. Redshift Object tag on rays, trails, particles: Curves ▸ **Cylinder instances** (rays r 2; trails r 1 with tapered radius spline); particles ▸ Sphere instances.
4. Material: Emission 2; **Ramp → Geometry Opacity** (additive look); ramp colors at value 50 % (room for hot overlaps).
5. Gradient along each curve: **Vertex Attribute ▸ preset Curves ▸ Curve Position** → ramp Alt input.
6. Post: Bloom threshold ~3, softness 0; Color Controls contrast 0.1.
