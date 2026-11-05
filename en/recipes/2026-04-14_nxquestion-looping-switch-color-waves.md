# Looping color waves triggered by contact (nxQuestion variable switch + nxBlend)

- Source: Top Tip Tuesday — Looping Actions — https://www.youtube.com/watch?v=jw-XgGPX65E (2026-04-14)
- Host / generation: NeXus (nxQuestion Variable, nxBlend Addition) — C4D & Blender
- Goal: black particles on a surface light up when touched by flying "trigger" particles, then keep pulsing black↔white in spreading waves.

## Switch loop (nxQuestion, Groups Affected = Group 2)
- **Variable** layer: Integer, **Writeable**, **Particle** (per-particle), name `SWITCH`, default 0.
- `If Math ▸ Variable SWITCH = 0 → Add Color white` (fade up)
- `If SWITCH = 1 → Set Color black` (fade down, a bit faster)
- `If Color Brightness < 0.05 → Set Variable SWITCH = 0`
- `If Color Brightness > 0.95 → Set Variable SWITCH = 1`
→ color drives the switch and the switch drives the color = endless cycle. Same pattern can pulse radius, speed, etc.

## Contact spread
1. Surface emitter: groups 1 & 2, First Group Only (all start in group 1, black). Trigger emitter shoots white spheres through them.
2. **nxBlend**: Color, **Blend: Addition** (only brightens), small Distance, Strength 300–800%, Max Blend = whole scene, **Groups Affected: Group 1** (so it doesn't interfere with the loop). Optional **Random field** on strength → irregular spread.
3. Second nxQuestion "group": `If Color Brightness > 0.9 → Set Group 2` → lit particles join the switch loop.
4. Faster/more waves: raise the Add Color strength (reaches white sooner, flips sooner).
5. Map black/white to colorful gradients at render time.
