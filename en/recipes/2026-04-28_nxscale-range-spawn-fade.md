# Spawned particles that grow and fade organically (nxScale Range curve + kill)

- Source: Top Tip Tuesday — Scale Range — https://www.youtube.com/watch?v=THuXYZmNZjQ (2026-04-28)
- Host / generation: C4D, NeXus (nxQuestion Spawn, nxScale Range, nxWind Von Karman) + Taiao toPlant
- Goal: pollen-like particles drifting off a growing plant's twig tips, each one scaling up then down smoothly.

## Scene tree
```
Join  └─ toPlant (polygon selection tag generated on the last branch layer)
xpEmitter "source": Object = Join, Selection = branches tag, Polygon Area, Rate 20, frames 60→end,
                    lifespan 2 F, speed 0, Stick Particle to Source
xpEmitter "spawn": (created by Add Emitter in the Spawn action) Display Circles + Force Display
nxQuestion
  Action Spawn (no question → always): Distance 0, Inherit Parent off, Full Life, speed 0, radius 0, light pink
  If Age > 50  AND  Radius < 0.1  → Kill
nxWind  (+X, Von Karman, more variation, friction velocity, less turbulence)
nxScale (Groups: spawn) — Range layer: Radius 0 → End 3 (variation), End Time 110 F,
        ease curve: fast rise to peak, slow ease back to 0
```

## Steps / key ideas
1. toPlant must sit in a **Join** to emit properly; enable the plant layer's **polygon selection** to emit only from the finest branches.
2. Short-lived "source" particles stuck to the branches → nxQuestion **Spawn** action with no question = continuous spawning into a second emitter.
3. **nxScale Range**: Y axis = Radius Start→End, X axis = Start→End time; draw the curve up then down → grow-and-shrink over the particle's life.
4. Kill when invisible to save sim time — but newborns start at radius 0, so gate the kill with **Age > 50 AND Radius < 0.1**.
5. Squares display hides radius — use Circles/Spheres to judge size.
