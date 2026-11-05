# Smooth slow-motion speed ramps on cached particles (xpCache Playback Scale / Offset / Retiming Time in seconds)

- Source: Top Tip Tuesday — Retiming Cached Particles — https://www.youtube.com/watch?v=MChyNywlLF8 (2024-09-24)
- Host / generation: C4D; **xpCache** playback (particles only)
- Goal: real-time → super slow-mo on the splash → real-time, with interpolated, jitter-free particles.

## Steps
1. xpCache ▸ Playback: enable **Hold** (past the cached range it holds the last frame instead of simulating live).
2. Constant speed: **Scale** (200 % = double, 50 % = half, 5 % = extreme slow-mo); **Offset** (e.g. **25** F) to reach the interesting moment. Scale can't be animated.
3. Ramps: Retiming **Time in seconds**. Key **0 s at F0** and **100/30 = 3.333 s at F100** (expressions work in the field; use your project fps).
4. Timeline ▸ F-curve of the cache's time track: set both keys **Linear** (default Bezier eases in/out).
5. Ctrl-click on the curve where the slow-mo starts → key; another key ~**F50**.
6. Select **both** keys, drag them down (or later right) together: the in-between section flattens (slow-mo) while the outer slopes stay at full speed.
7. Optional Bezier easing between keys; a downward slope plays backwards.

## Gotchas
- Works only for **particle** caches — retimed OpenVDB mesh or trail caches won't play smoothly (see 2024-10-29 recipe for meshing from retimed particles).
- Don't distort the outer slopes, or "real-time" parts change speed.
