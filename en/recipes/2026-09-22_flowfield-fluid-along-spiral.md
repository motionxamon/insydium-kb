# Liquid stream steered along a helix spline (nxFlowField Along/To Spline + Turbulence, PBD, nxQuestion escape kill)

- Source: Top Tip Tuesday — Flowfield Fluids — https://www.youtube.com/watch?v=I9Fq5NPENdc (2026-09-22)
- Host / generation: Blender (NeXus for Blender 2026.0) — nxFlowField, nxFluids PBD, nxQuestion, nxMesher
- Goal: a procedural, art-directable fluid ribbon spiralling up a curve, then dying once it leaves the field.

## Steps
1. Curve: Extra Curves ▸ Spirals (Archimedean), taller with some radius grow. [▶ 0:25](https://youtu.be/I9Fq5NPENdc?t=25)
2. **nxEmitter**: Shape **Disc**, direction **+Z**, Birth Rate **10,000**; display point size 2 (display only). [▶ 1:21](https://youtu.be/I9Fq5NPENdc?t=81)
3. **nxFlowField**: domain-based — set Domain size to enclose the helix (~**9 × 9 × 8 m**). Delete the default **Radial** layer (it pushes outward; inverted power sucks inward). [▶ 3:00](https://youtu.be/I9Fq5NPENdc?t=180)
4. Add layer **Along Spline** (Targets & Surfaces) ▸ Generator ▸ the spiral. [▶ 4:30](https://youtu.be/I9Fq5NPENdc?t=270)
5. Field mode: switch **Acceleration → Steer** — particles keep their emitter speed and are only redirected, so they hug the curve instead of speeding off. [▶ 5:42](https://youtu.be/I9Fq5NPENdc?t=342)
6. Detail: Domain voxel size **0.12 → 0.08**; raise Display ▸ Preview Density to see more vectors; add display transparency. [▶ 6:59](https://youtu.be/I9Fq5NPENdc?t=419)
7. Add **Turbulence** layer (Add blend), raise its Generator Speed to animate. [▶ 8:08](https://youtu.be/I9Fq5NPENdc?t=488)
8. Add **To Spline** layer on top (Add) → pulls strays back. Too strong by default: lower its Opacity, or better use its **falloff curve** (default 2 m distance) set to 0 at the spline rising to full at 2 m — pull only acts on particles that drift out; raise the curve minimum for tighter following. [▶ 10:00](https://youtu.be/I9Fq5NPENdc?t=600)
9. Crank Turbulence strength, then set the field's overall **Smoothing to full**; lower noise scale for smaller swirls. [▶ 12:12](https://youtu.be/I9Fq5NPENdc?t=732)
10. Speed comes from the emitter only (Steer mode): Speed **2.5** with variation. [▶ 13:15](https://youtu.be/I9Fq5NPENdc?t=795)
11. **nxFluids PBD**: raise Smoothing Radius (~110), add External Pressure + a little Repulsion for stringy tendrils; emitter radius **0.01 m**. [▶ 13:59](https://youtu.be/I9Fq5NPENdc?t=839)
12. Ending: drag the last curve point outside the domain; flow field ▸ **Flag on Escape**; **nxQuestion**: if flag Escaped → Action **Kill Particle** (or set a short varied lifespan). [▶ 17:02](https://youtu.be/I9Fq5NPENdc?t=1022)
13. **nxMesher**: emitter layer, polygon size ~0.01, Surface **Zhu-Bridson**, radius ~0.015. [▶ 18:58](https://youtu.be/I9Fq5NPENdc?t=1138)

## Newest equivalent
2026.1 beta **nxWarp** (Path / Helix, Guide or Flow mode) can shape streams with less setup, and **nxFlowField** gains a **Cyclic** layer; FLIP/APIC gives a heavier liquid than PBD.
