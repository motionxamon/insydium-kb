# Triggering modifiers by switching particle groups (nxGroup, Groups Affected, nxQuestion Set Group)

- Source: NeXus for Blender Quick Guide — Particle Groups — https://www.youtube.com/watch?v=P9O1SJhPeik (2026-06-22)
- Host / generation: Blender (NeXus for Blender, G3); nxEmitter, nxGroup, nxWind, nxGravity, nxColor, nxCollider, nxQuestion
- Goal: particles sit on a Suzanne, get blown off by wind when they change group (by age or by a moving falloff), then fall under gravity after travelling a distance.

## Base
Suzanne (Subdivision 2, applied, shade smooth). **nxEmitter** Shape Object = Suzanne, emit from **Poly Area**, Shot of **100,000**, Speed 0. **nxWind** Mode **Von Karman** with a little strength variation, Heading rotated to blow left. **nxCollider**: big hidden plane layer (small bounce + friction) + Suzanne layer (no bounce/friction).

## Steps
1. Emitter ▸ **Groups** tab ▸ add-group button (auto-creates an **nxGroup** and a group layer). Born particles now use the group's own particle properties (default green, has speed) — set group Speed 0.
2. Add a second group (pink, speed 0). Emitter group mode **Random** splits particles between them.
3. Rename each group to include its **Group ID** (1, 2, 3…) — makes later questions easier.
4. Any modifier ▸ **Groups Affected**: nxWind on group 2 only (tick = include, minus = exclude/invert).
5. Emitter group mode **First Group Only** → all born into group 1 (wind does nothing).
6. **nxQuestion** ▸ Question layer: Particle category, **Age > 45** → child **Action** (default Set Color yellow to test) → switch to **Set Group = group 2**. Feather it: **Age 55, variation 20**.
7. **nxColor** Gradient by Parameter (speed), adjust min/max.
8. Tactile version: question category **Field** with a **Sphere falloff** (orange = 1 → blue = 0); **Field > 0** → Set Group 2. Animate the falloff to "paint" particles loose.
9. Third group + **nxGravity** with Groups Affected = group 3. New question (use **Outdent** so it's not a child): **Distance Travelled > 5 m, variation 1 m** → Set Group 3 (disable nxColor while testing a color action — it overrides).
10. Add group 3 to the wind's Groups Affected so falling particles keep being pushed along the floor.

## Gotchas
- Group particle properties (color, speed…) apply **only at birth**; nxQuestion Set Group changes just the group ID.
- New question layers auto-nest under the selected one — outdent for an independent question.

## Newest equivalent
NeXus 2026.1 beta: each modifier layer has its own Falloff list and 16 nxFalloff modes, so simple "inside the sphere" effects work without a group switch; **Quill** (Blender) can draft the nxQuestion logic from a plain-language prompt.
