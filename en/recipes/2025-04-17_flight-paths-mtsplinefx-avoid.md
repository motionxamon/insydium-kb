# Procedural flight-path arcs over a globe (mtSplineFX start/end nulls + Avoid)

- Source: Bite-Sized — Flight Paths — https://www.youtube.com/watch?v=oruUSaTZAJ4 (2025-04-17)
- Host / generation: C4D; MeshTools **mtSplineFX** (no particles)
- Goal: arcs between cities on an Earth model that update live when the city markers move.

## Steps
1. One **Null** per city (rename e.g. UK, US, AF), display **Locator**, give it a color; place it on the globe surface.
2. **MeshTools ▸ mtSplineFX** — defaults to a lightning spline.
3. Objects tab: drag the start null and end null into the start/end lists.
4. Kill the lightning: Motion channel ▸ set the **Amplitude of both noises to 0**.
5. Avoid tab: Earth model in the list, enable **Avoid Ends**, raise **Weight** to lift the arc off the surface (weight = arc height); set **Pinch** to 0.
6. Display tab: contact points off, display gradient off (single color).
7. More routes: one mtSplineFX per route, reusing or duplicating city nulls (e.g. US → AF, a second UK → Australia gives a bigger arc for the longer distance).
8. Animate with the object's growth options to draw the routes on.

## Gotchas
- Each start/end pair is its own mtSplineFX; duplicate a null when a city is the start of several routes.
