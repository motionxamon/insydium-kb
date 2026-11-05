# Slime-mold growth over a log (mtRemesh + mtShortestPath + xpSplineMesher)

- Source: Bite-Sized — MeshTools Slime Mold — https://www.youtube.com/watch?v=POC6gx3p4rc (2025-09-18)
- Host / generation: C4D; MeshTools (**mtRemesh**, **mtShortestPath**) + CPU **xpSplineMesher** (X-Particles Generators)
- Goal: organic, growing slime-mold veins spreading from one point across part of a mesh.

## Steps
1. Duplicate the log (Ctrl-drag), keep only the polygon selection where the mold should grow (invert selection, delete). Keep it **triangulated** — triangles give organic paths, quads give grid-like ones. [▶ 0:57](https://youtu.be/POC6gx3p4rc?t=57)
2. **mtRemesh** (Delaunay triangulation): **Feature angle 180°** (follow the surface), **Edge length ~0.3** for a dense triangle network. Make editable, drop the null. [▶ 1:36](https://youtu.be/POC6gx3p4rc?t=96)
3. Pick one vertex in a damp crevice ▸ Select ▸ **Set Selection** = start point. [▶ 2:16](https://youtu.be/POC6gx3p4rc?t=136)
4. **mtShortestPath** ▸ Objects: the remeshed piece; Start = **Source** → the point selection tag. [▶ 2:53](https://youtu.be/POC6gx3p4rc?t=173)
5. **End number** = how many points the network reaches: **800** for work, ~5,000 to cover the mesh; it animates as growth. Hide start/end point display. [▶ 3:42](https://youtu.be/POC6gx3p4rc?t=222)
6. Spline: **Linear → B-Spline**, Intermediate points **Uniform** → smooth curves. [▶ 4:13](https://youtu.be/POC6gx3p4rc?t=253)
7. **xpSplineMesher** with the shortest-path object as source: turn off **joins**, **size 2**, **subdivisions 2** (round instead of box section). [▶ 4:35](https://youtu.be/POC6gx3p4rc?t=275)
8. Size ▸ **Scale spline**: add a bump at one end for bulbous tips. [▶ 5:13](https://youtu.be/POC6gx3p4rc?t=313)
9. Animate the mesher's **Growth** slider for the creeping reveal. Optional: Displacer for bubbly surface. [▶ 5:56](https://youtu.be/POC6gx3p4rc?t=356)

## Newest equivalent
**nxBioLogic** (2026.1 beta) has a Physarum (slime-mold) mode with tube meshes — a GPU-simulated alternative to this geometric approach.
