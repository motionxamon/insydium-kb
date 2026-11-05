# City lights spreading along building edges (nxInfectio + groups)

- Source: Top Tip Tuesday — Particle Edge Infection — https://www.youtube.com/watch?v=veRxUHtrnFA (2025-10-14)
- Host / generation: NeXus (nxInfectio, nxColor Distance from Object) + MoGraph cloners in xpJoin
- Goal: a wireframe city lighting up building by building.

## Steps
1. MoGraph cityscape cloners inside **xpJoin**. Emitter Object = join, **Emit From Edges**, **Shot 200 000**, speed 0, black particles.
2. **nxInfectio** → **Add Seed Object** (volume — particles inside start infected), Search Radius 25 cm, Max Infected 3.
3. Default **Incubation Mode = Use Particle Color** — black never infects! → switch to **Set From Incubation Rate**, low rate + high variation (organic spread).
4. **Infected Lifespan** default 300 F kills them (nice for wipe-off) → set to scene length (500).
5. **Color Mode: Use Groups** → Incubating = Group 1, Infected = Group 2; **Group Color Change: No Color Changes** (only regroup).
6. **nxColor** with **Groups Affected 1 & 2**: layer **Distance from Object** (Null on rooftops), green far → blue near over 600 cm → lit edges graded by height.
7. Render particles as emissive lights over dark buildings.
