# Trails whose thickness follows particle radius (xpTrail Thickness: Use Radius Variable → Redshift curves)

- Source: Top Tip Tuesday — Varied Trail Thickness — https://www.youtube.com/watch?v=Lx6Sugl11TA (2024-12-10)
- Host / generation: NeXus (nxColor, nxScale) + CPU **xpTrail** + Redshift
- Goal: glassy colored trails that swell and thin as particles change size.

## Steps
1. Emitter Defined mode, count 5, speed ~330; **nxColor** gradient-by-parameter driven by a big Perlin random field. [▶ 0:23](https://youtu.be/Lx6Sugl11TA?t=23)
2. **xpTrail** with the emitter → **Redshift Object tag ▸ Curves ▸ Capsules**, thickness 200 for a first look. [▶ 1:37](https://youtu.be/Lx6Sugl11TA?t=97)
3. Color: xpTrail ▸ Thickness & Color ▸ Trail Color **Per Vertex** (remembers color history); Redshift **Vertex Attribute ▸ preset Curves ▸ Curve Color** → transmission color of a glass material. [▶ 3:01](https://youtu.be/Lx6Sugl11TA?t=181)
4. Per-trail width: Redshift thickness back to 1; xpTrail Thickness mode **Use Particle Current** → each trail = its particle's size. Mesh subdivisions **Adaptive** (smooth). [▶ 4:07](https://youtu.be/Lx6Sugl11TA?t=247)
5. Animated width: **nxScale** Set by Falloff with the same random field; emitter radius 200, no variation; xpTrail Thickness **Use Radius Variable** → width painted along the trail. [▶ 5:39](https://youtu.be/Lx6Sugl11TA?t=339)
6. Thickness factor **2** = exact particle diameter (radius-based). [▶ 6:10](https://youtu.be/Lx6Sugl11TA?t=370)

## Newest equivalent
NeXus trails (nxTrail-style GPU trails, see "NeXus Particle Trails") where available; render data access stays the same.
