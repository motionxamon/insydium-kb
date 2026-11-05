# Trails whose thickness follows particle radius (xpTrail Thickness: Use Radius Variable → Redshift curves)

- Source: Top Tip Tuesday — Varied Trail Thickness — https://www.youtube.com/watch?v=Lx6Sugl11TA (2024-12-10)
- Host / generation: NeXus (nxColor, nxScale) + CPU **xpTrail** + Redshift
- Goal: glassy colored trails that swell and thin as particles change size.

## Steps
1. Emitter Defined mode, count 5, speed ~330; **nxColor** gradient-by-parameter driven by a big Perlin random field.
2. **xpTrail** with the emitter → **Redshift Object tag ▸ Curves ▸ Capsules**, thickness 200 for a first look.
3. Color: xpTrail ▸ Thickness & Color ▸ Trail Color **Per Vertex** (remembers color history); Redshift **Vertex Attribute ▸ preset Curves ▸ Curve Color** → transmission color of a glass material.
4. Per-trail width: Redshift thickness back to 1; xpTrail Thickness mode **Use Particle Current** → each trail = its particle's size. Mesh subdivisions **Adaptive** (smooth).
5. Animated width: **nxScale** Set by Falloff with the same random field; emitter radius 200, no variation; xpTrail Thickness **Use Radius Variable** → width painted along the trail.
6. Thickness factor **2** = exact particle diameter (radius-based).

## Newest equivalent
NeXus trails (nxTrail-style GPU trails, see "NeXus Particle Trails") where available; render data access stays the same.
