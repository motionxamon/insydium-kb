# Deforming meshes and static particle clouds with a MoGraph Random effector (Deformer mode + xpEmitter Modifiers list)

- Source: Bite-Sized — Effector Deformation — https://www.youtube.com/watch?v=P9mLMWa6XKQ (2025-02-13)
- Host / generation: C4D MoGraph effectors + Fields; CPU **xpEmitter** (G1)
- Goal: turbulent, animated deformation of a balloon-dog mesh, then the same effector moving a static particle cloud without breaking it apart.

## Steps — mesh
1. MoGraph ▸ Effectors ▸ **Random effector**; Deformer tab ▸ Deformation **Point** (Polygon and Object modes also exist).
2. Parameter tab: Position **15 cm** on X/Y/Z; make the effector a **child of the geometry** so it acts as a deformer.
3. Put the mesh (with its effector child) under a **Subdivision Surface** to smooth the result.
4. Animate it: Effector tab ▸ Random Mode **Turbulence** (most detail), Animation Speed **20%**; raise Position to **30 cm** on each axis.

## Steps — particles
5. Move the effector out of the mesh. **xpEmitter** ▸ Emitter Source **Object**, drop in the Subdivision Surface, emit from **Polygon Area**.
6. Emission **Shot**, **100,000** particles, set to fire so they already exist on frame 0; Speed 0; Display **Dots**; hide the source mesh.
7. Emitter ▸ **Modifiers** tab: drag the Random effector in → the static particles are displaced with the same animated turbulence.
8. Localize it: add a **Linear Field** (Z) to the effector's falloff and animate it across the dog → a wave of turbulence travels through the cloud.

## Gotchas
- Particles stay static and are only displaced, so the cloud never tears apart — no forces or speed involved.

## Newest equivalent
NeXus 2026.1 beta: **nxWarp** (Noise and other cage warps, **Deform** mode) deforms particles and meshes directly, with nxFalloff modes in place of C4D Fields. In C4D 2025.3+, the Pyro/native particles link lets NeXus modifiers drive native particles.
