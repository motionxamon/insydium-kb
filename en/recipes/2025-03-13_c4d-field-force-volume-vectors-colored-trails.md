# Surface-tangent swirl trails (C4D Field Force + Volume Builder Cross Product vectors + nxColor ▸ xpTrail Per Vertex in Redshift)

- Source: Bite-Sized — X-Particles C4D Forces — https://www.youtube.com/watch?v=W8E4taTkKag (2025-03-13)
- Host / generation: C4D native forces/Volume Builder driving an xpEmitter; NeXus GPU nxColor; CPU xpTrail; Redshift
- Goal: particles that swirl randomly but stay on a torus, drawing trails whose color paints on as the direction changes.

## Steps
1. xpEmitter emits static particles from a **Torus** surface. Any C4D Simulate ▸ Forces object works on X-Particles/NeXus (e.g. Attractor). [▶ 0:03](https://youtu.be/W8E4taTkKag?t=3)
2. **Field Force** with a **Random field** (scale ~700%), Velocity Type **Set Absolute Velocity**, ~**50** → noisy flow (for plain noise prefer GPU **nxTurbulence**). [▶ 1:24](https://youtu.be/W8E4taTkKag?t=84)
3. Surface trick: **Volume Builder**, Volume Type **Vector**; inside it the torus *below* the Random field; Random field blend **Cross Product** and Creation Space **Objects Below** → random vectors that are always tangent to the torus surface. [▶ 3:31](https://youtu.be/W8E4taTkKag?t=211)
4. More detail: torus pipe segments up, Volume Builder **Voxel Size ~2**. [▶ 4:06](https://youtu.be/W8E4taTkKag?t=246)
5. Field Force: remove the random field, add the **Volume Builder** as a volume object; hide the builder → particles circulate over the surface. [▶ 4:28](https://youtu.be/W8E4taTkKag?t=268)
6. **xpTrail** on the emitter.
7. **nxColor ▸ Gradient by Parameter ▸ Direction**, load a preset gradient (e.g. Violet). [▶ 5:40](https://youtu.be/W8E4taTkKag?t=340)
8. Redshift material on the trail: Standard ▸ Emission weight **2**; **Vertex Attribute** node, Attribute Name preset **Curves ▸ curve color** → Geometry ▸ Opacity for an additive look. Redshift Object tag on the trail: thicker, tapered tips. [▶ 7:17](https://youtu.be/W8E4taTkKag?t=437)
9. xpTrail ▸ Thickness and Color ▸ **Trail Color Mode**: Particle Color recolors the whole trail at once; **Per Vertex** paints the color change on over time (not possible with C4D's Tracer). [▶ 8:00](https://youtu.be/W8E4taTkKag?t=480)

## Newest equivalent
nxFollowGeo (successor of xpFollowSurface) plus layered nxTurbulence keeps particles on a surface on the GPU; nxTrail is the NeXus trail object, and nxWarp (2026.1) can shape the streams further.
