# Underwater splash bubbles (EFX advection + nxMesher + particle haze)

- Source: Top Tip Tuesday — Underwater Splash — https://www.youtube.com/watch?v=Lds-YgrX6RE (2026-05-26)
- Host / generation: C4D, Fused 2025.4+ (nxExplosiaFX as invisible velocity field, nxMesher) + Redshift
- Goal: an object plunges into water: big irregular bubbles plus a milky haze of tiny bubbles that blast down then rise.

## EFX velocity field (not rendered)
1. nxExplosiaFX domain, **Voxel Size 3**. Source: falling Sphere, **Motion Gap Fill** (fast object), Emit From Surface, **Surface Width 0**, Fuel 0.3 **weighted by Noise** (uneven emission).
2. **Velocity From Object Motion 400%** → fluid shoots down before buoyancy brings it back up.
3. Simulation ▸ Dissipation: **off** (smoke/temperature persist).
4. Dynamics ▸ Forces: keep default Turbulence/Vorticity + add **Turbulence FBM**, very strong, scale ~38, octaves 1, **mapped to Document Time** (curve flipped: full at 0 s → none by 0.15 s) → breaks the plume only at the start.
5. Display Draw Mode **Off**.

## Particles
6. **Emitter Big**: Object = Sphere, Polygon Area, Rate 30 000/s only frames 3–20, speed 0, radius 2 ±1.5. EFX ▸ Particle Advection → **Position** mode, strength **~83%** (doesn't hug the fluid → bubbles clump).
7. **Emitter Small**: duplicate, radius 1 ±0.2, **1.5 M/s**, Dots display; advection Position **100%**.
8. Helper: a **Wind** force pointing up (strength ~30) inside the EFX Forces → helps the rise.
9. **xpCache** — Inclusion: uncheck EFX (only particles). Build. Then disable EFX.

## Meshing & render
10. **nxMesher** on Emitter Big: Surface Size **Source 150%**, Polygon Size **1.5** (watch VRAM), **Zhu-Bridson** → irregular bubble blobs, no smoothing. Cache it with **Build Cache → Continue** (keeps particle cache).
11. Emitter Small → **Redshift Object tag** ▸ Particles: Sphere Instances, scale ~0.4, small-bubble material → hazy disturbed water.
