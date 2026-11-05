# Seamless infinite loop from a rendered particle sim (After Effects duplicate + opacity crossfade)

- Source: Bite-Sized — Particle Loop — https://www.youtube.com/watch?v=QprpMu4F_HM (2025-02-20)
- Host / generation: C4D + After Effects; NeXus modifiers (nxRotate mapped to Age, nxTurbulence) on a cached sim, rendered in Cycles
- Goal: turn a long, non-repeating particle render into a 5 s loop with no visible seam.

## Base
Cached sim: **nxTurbulence** + **nxRotate** whose rotation is mapped to particle **Age** (only old particles start spinning off). Key point: render far more frames than the loop length — 20 s here for a 5 s loop.

## Steps
1. AE: drop the image sequence into a new comp; trim away the start you don't want. [▶ 0:49](https://youtu.be/QprpMu4F_HM?t=49)
2. Pick the loop range with markers (numpad * key): **5 s → 10 s**. [▶ 1:01](https://youtu.be/QprpMu4F_HM?t=61)
3. Duplicate the layer (Ctrl/Cmd+D) and slide the copy so that its frame from the range start (5 s) now lands on the range end (10 s) — i.e. the copy (on top) is offset one loop length (5 s) later. [▶ 1:47](https://youtu.be/QprpMu4F_HM?t=107)
4. On the copy, Opacity (T): key **0% at 5 s → 100% at 10 s**. The very slow crossfade returns the image exactly to the start frame, so the fade itself is invisible. [▶ 2:08](https://youtu.be/QprpMu4F_HM?t=128)
5. Work area to the range (B / N) and play: the 5 s loop repeats seamlessly. [▶ 2:39](https://youtu.be/QprpMu4F_HM?t=159)
6. Tidy up: precompose both layers (Ctrl+Shift+C), trim to the range and move it to the comp start. [▶ 3:02](https://youtu.be/QprpMu4F_HM?t=182)
7. Optional grade on top: a **Curves** S-curve for contrast; motion blur can be added here too. [▶ 3:44](https://youtu.be/QprpMu4F_HM?t=224)

## Gotchas
- The loop only works if the overlap frames exist on both layers — hence the long render.
- Choose a stretch where the motion is steady (after the initial burst), or the crossfade reads as a dissolve.

## Newest equivalent
The comp trick is host-independent. In NeXus 2026.1, nxRotate/nxTurbulence age-mapping works the same, and the **Cyclic** layer (nxColor, nxFlowField) can make some attributes loop at the sim stage.
