# Additive particle look in Redshift (Point Instances + emission-only material + Color User Data → Opacity)

- Source: Top Tip Tuesday — Additive Particles — https://www.youtube.com/watch?v=KkTBqbnPwg8 (2024-06-18)
- Host / generation: C4D; xpEmitter + nxTurbulence (GPU); Redshift
- Goal: millions of tiny colored particles that add up to a milky, glowing render.

## Sim
1. xpEmitter **Circle**, disc radius 15, **cone angle 90**, **Ring Only** → flat ring emission.
2. **nxTurbulence** Voronoi, strength 50, scale 80%, **Octaves max** for fine detail, then **Persistence 45%** to keep the big swirls.

## Render
3. Emitter ▸ **Redshift Object tag ▸ Particles: Point Instances** (most efficient).
4. Redshift Standard Material: base color, reflection and all other channels weight **0**; **Emission weight 2**.
5. Single-color version: set **Geometry ▸ Opacity** to a color → overlaps add up to white.
6. Particle color: **Color User Data** node, preset **Particles ▸ Color** → into **Geometry Opacity**.
7. Shrink: Redshift Object **Scale Multiplier** way down (~0.05), then raise particle count.
8. Cached version at **100,000/frame** (~4 million live particles) → scale multiplier **0.015**.

## Gotchas
- Instances rebuild whenever scale changes — slow with millions of points.
- Additive needs density + tiny scale; too big just blows out to white.
