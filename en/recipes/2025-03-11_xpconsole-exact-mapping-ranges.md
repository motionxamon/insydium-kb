# Exact data-mapping ranges from live particle data (xpConsole min/max → nxColor / Mapping)

- Source: Top Tip Tuesday — xpConsole — https://www.youtube.com/watch?v=Q0gZAMr9MN0 (2025-03-11)
- Host / generation: C4D; X-Particles utility **xpConsole** inspecting a NeXus G2 sim (nxTurbulence, nxDrag, nxColor)
- Goal: stop guessing Min/Max values — read them from the particles.

## Base
Wispy sim: turbulence + drag; **nxColor** gradient by **Distance Travelled** — but the red end never shows because the range is wrong.

## Steps
1. X-Particles ▸ Utilities ▸ **xpConsole**: per-particle data table for the current frame (defaults: ID, Age).
2. Shortcut: Window ▸ Customization ▸ **Command Manager**, search xpConsole, drag the icon to a palette.
3. Data to Display ▸ add **Distance** channel. **Double-click any value** → Min/Max of the channel (≈652 in the demo).
4. Set nxColor Max a bit below (620) → full gradient, reds on the furthest particles.
5. Same for **Speed**: add the channel, double-click, set Max slightly under the reported max.
6. Works for any Mapping: e.g. nxTurbulence ▸ Mapping ▸ Distance Travelled → Strength with the exact range from the console (0–633).

## Gotchas
Values are per frame — check the frame where the extreme matters.

## Newest equivalent
NeXus for Blender 2026.0.1 added a console emitter filter, so the same inspect-then-map habit applies.
