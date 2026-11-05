# Pulsing particles pushing each other while hugging a surface (collider attraction)

- Source: Top Tip Tuesday — Collision Forces — https://www.youtube.com/watch?v=PTamR793O-k (2025-10-07)
- Host / generation: NeXus (nxQuestion, nxPush) + CPU xpColor (Maxon shader) + xpCollider Forces tab
- Goal: particles on a torus grow and shrink in patches, shove each other, but never leave the surface.

## Steps
1. Emitter Object = torus, Polygon Area, **Shot 10 000**, speed 0, **no birth radius** (avoid a flash).
2. **xpColor** with a Maxon **Noise (Voronoi)** shader, huge scale, clipped, animation speed ~7 → moving black/white patches.
3. **nxQuestion**: `Color Brightness < 0.1 → Set Radius 0` (low weight = gradual shrink) / `> 0.7 → Set Radius 26` (low weight).
4. **nxPush** Particle Radius mode, full strength, 10 iterations.
5. Torus **xpCollider tag**: Bounce 0, some Friction (with variation for sliding variety) → particles bounce off when pushed…
6. …so use the collider's **Forces tab → Attraction**, Radius 100 cm, strength ~59 → particles hug the surface while pushing apart. (Avoid nxFollowGeo + nxPush — opposing forces.)
7. xpGenerator **Render Instances** of a Platonic; Extended Data **Use Rotation → Random**.
