# Burst particles that ease to an organic stop (nxSpeed Range + curl turbulence)

- Source: Top Tip Tuesday — Speed Range — https://www.youtube.com/watch?v=HvX6qaVei1o (2026-03-31)
- Host / generation: NeXus (nxTurbulence Curl, nxSpeed Range) + xpTrail — C4D
- Goal: particles shoot out from a circle, wander turbulently and decelerate naturally to a halt, drawing trails.

## Steps
1. Circle emitter firing outward; xpTrail on the emitter.
2. **nxTurbulence** → layer **Curl**, bigger Scale, lower Frequency (no jitter). **Add off**; **Blend ~64%** = how much motion comes from the curl vs the particle's own velocity (100% = only noise, 0 = only particle speed).
3. **nxSpeed** *below* turbulence → **Range** layer: Speed Start 0 / End 300 over 0–60 frames. **Flip the ease curve** so it starts at full speed (300) and ends at 0 → shoot out then stop, with an ease-in to the stop.
4. Variation on End Time (~36 F) and on max speed → particles stop at different moments = organic.
5. Longer trails: raise End Time (e.g. 85 F).

## Note
Range layers (nxSpeed, nxScale, nxSpin, nxColor…) are the recommended "do-everything" layers since Fused 2025.4: start/end value, start/end time, ease curve, variations on all.
