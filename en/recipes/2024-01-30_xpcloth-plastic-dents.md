# Bullet-dented metal sign (xpClothFX plasticity + damping)

- Source: Top Tip Tuesday — xpCloth Dents — https://www.youtube.com/watch?v=tGkpVuhTQCE (2024-01-30)
- Host / generation: C4D; CPU X-Particles (xpClothFX, xpConstraints, xpGravity, xpCache)
- Goal: particles fired at a low-poly sign leave permanent dents instead of springy ripples.

## Base
Editable plane "sign" with a point selection of its perimeter; a gun emitter firing particles through it.

## Steps
1. Select sign ▸ X-Particles ▸ Dynamics ▸ ClothFX ▸ **Create Cloth** → cloth tag, constraints object (P-P collisions), gravity, cloth modifier, cloth emitter (one particle per vertex). [▶ 0:57](https://youtu.be/tGkpVuhTQCE?t=57)
2. Show cloth particles as Circles: by default they overlap. Cloth tag ▸ Advanced ▸ **Set Particle Radius off** → uses emitter radius (default 3 cm) — nearly touching, ideal for dents. [▶ 1:52](https://youtu.be/tGkpVuhTQCE?t=112)
3. Advanced ▸ **Pin** on, drag in the perimeter selection. [▶ 2:23](https://youtu.be/tGkpVuhTQCE?t=143)
4. Cloth emitter ▸ Modifiers tab: **exclude the gravity** so the sign doesn't sag. [▶ 2:49](https://youtu.be/tGkpVuhTQCE?t=169)
5. Cloth options ▸ **Plasticity** (threshold 1.1): springs pushed past it can't spring back → dents. [▶ 3:13](https://youtu.be/tGkpVuhTQCE?t=193)
6. Energy ripples through like thin foil → raise **Damping** to ~34%. [▶ 4:09](https://youtu.be/tGkpVuhTQCE?t=249)
7. **xpCache** (150 F), then put the sign under a **Subdivision Surface** to smooth facets after caching. [▶ 5:03](https://youtu.be/tGkpVuhTQCE?t=303)

## Gotchas
- Keep the cloth low-poly for speed; smooth afterwards.

## Newest equivalent
**nxMPM** metal material / nxMaterial Metal preset (2026.1 beta) on the GPU; nxShatter for breaking.
