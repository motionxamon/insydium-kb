# Docked custom palettes for INSYDIUM tools (C4D Command Manager, tear-off submenus, Lock Icon)

- Source: Bite-Sized — Custom Tool Palettes — https://www.youtube.com/watch?v=jzFk-veno5U (2025-02-27)
- Host / generation: C4D interface customisation (works for any plugin)
- Goal: one-click icons (with fly-out submenus) for NeXus, MeshTools, emitter and cache.

## Steps
1. **Window ▸ Customization ▸ Command Manager** ▸ **Edit Palettes** (palettes become editable).
2. Single commands: search (e.g. "nx" lists every NeXus command) and drag **nxFluids** into an existing palette. In edit mode, double-click an icon to remove it.
3. New palette: **New Palette**, then drag it by its dotted handle and dock it where the line appears (e.g. next to the default palettes) before filling it.
4. Fly-out groups: tear off the INSYDIUM menu (click its top bar) and drag a whole submenu — e.g. **MeshTools**, or X-Particles ▸ **NeXus** — into the palette; the small arrow shows it holds sub-commands. Add frequent single items too (**xpEmitter**, **xpCache**).
5. Tidy with a **Group Separator** between sets; one palette per product (X-Particles, TerraformFX, Taiao…) is fine.
6. Fly-outs show the last-used tool by default; pick the icon you want (e.g. an inset-style MeshTools icon, nxAttract for NeXus), right-click ▸ **Lock Icon**.
7. Right-click empty palette space for icon size, text/text-below (wastes room), rows/columns.
8. Keep it: Window ▸ Customization ▸ **Save as Startup Layout**, or **Save Layout As** for a selectable layout.

## Newest equivalent
NeXus 2026.1 splits its Add menu into Presets / Generators / Dynamics / Modifiers / Warps — those submenus can be docked the same way.
