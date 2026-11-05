# Taiao & Jidou (C4D, part of INSYDIUM Fused)

Source: docs.insydium.ltd/taiao/*, /jidou/* (Fused 2025, checked 2026-11-03). Paraphrased.

## Taiao — procedural nature
- **toPlant** — layer-stacked plant/tree builder. Add Part: **Growth Point, Trunk, Branch, Leaf, Custom Object** (e.g. a toFlower), Folder. Check = enable, circle = solo (don't forget solos!), triangle = per-layer selection tags. Low-poly simplification for backgrounds.
  - **Growth tab:** Global Growth scales all layers over time, or per layer; Mode Growth / Global Growth / Animate Slider; Trigger Mode Random / Sequence / **Field** (field disables Mode/Animate/Variation); After Growth delay; Variation. Keyframed leaves/flowers (key icon) become separate polygon objects → slower.
  - **Forces tab:** Wind Strength + Variation (>0%), Direction, Noise Type, Turbulence, Octaves, Seed, per-level Strength/Frequency/Layer Weight; set **Loop Time one frame past timeline end** for seamless loops; leaf wind = slower.
  - Can **emit X-Particles** (falling leaves).
- **toTree** — space-colonisation tree: branches grow toward **attraction points inside a volume** (Crown Shape or any Volume Object — text, logo, torus); link an **xpEmitter** (Speed 0) to use particles as attraction points; Attraction Points, Trunk Height, Seed; pass-through option. Great for motion-graphics "growing logo" trees.
- **toFlower** — procedural flower parts (Petal, Sepal, Pistil, Stamen, Receptacle) each with modifier stacks.
- **toLeaf** — Standard or Lobed leaves with veins and modifiers.
- **toGrass** — grass (or any object) scattered on terrains/objects/splines: Generate on list, Hierarchy, Texture/Shader + Tolerance, Density, Blade Width/Height/Bend/Turbulence, Height & Slope ranges, **Multi-Instances** (cheaper than Clones), **Field of View** culling, **Avoid Objects**.
- **Preset Browser** — library of real plant species.

## Jidou — procedural animation & rigging
- **jdDriver** — drive any C4D parameter from a signal: Add Drivers → pick type → **drag the parameter** (e.g. Size.X) onto the driver → Offset bar = active time. Types: **Color, Noise, Time, Value, Wave, Switch** + utilities **Folder, Merge, Sequencer** (combine/sequence drivers). Output Clamp / Remap (Include Zero). Cloners must be under a Null. Replaces lots of Xpresso/expressions for wiggles, pulses, loops.
- **jdAniMate** — store Start and End states (pos/rot/scale), interpolate with a timing spline (quick A→B animation).
- **jdFlowCam** — camera through CamPoints with weighted timing, easing, spring, focal length.
- **jdGeoFlow** — move objects along FlowPoints or preset spline with deformation, easing, loops.
- **jdGeoRoll** — roll objects over collider surfaces with handles; contact/rotation auto-computed (rolling dice, wheels, boulders).
