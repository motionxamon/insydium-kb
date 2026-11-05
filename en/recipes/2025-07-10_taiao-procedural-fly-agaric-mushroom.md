# Procedural fly agaric mushroom (Taiao Plant trunk + Flower petal/pistil as annulus and cap, Redshift)

- Source: INSYDIUM Official Training — Taiao Mushrooms — https://www.youtube.com/watch?v=UenunlSJ1d8 (2025-07-10)
- Host / generation: C4D; Taiao (Plant, Flower; Displacer/Turbulence/Curl modifiers); Redshift materials
- Goal: Amanita-style mushroom (stalk, frilly ring, red cap with white gills and spots), fully procedural.

## Stalk (Taiao Plant ▸ Trunk)
1. **Taiao Plant** ▸ add **Trunk**: Height **10 cm** (default 300), Radius 5.
2. Geometry: Global Settings ▸ **Segment Resolution** way down (0.1 shown, then backed off slightly); raise trunk **Ring Segments** until polys are roughly square.
3. Profile spline: bulbous base flaring up, curve the top end down.
4. Modifiers ▸ **Displacer** with a Noise shader stretched tall and scaled small → vertical ridges; lower Strength to taste. Global Settings ▸ **Subdivisions** on to soften crisp edges.
5. Modifiers ▸ **Turbulence** at ~1% (it is scaled for a 300 cm tree), larger scale, bias off the base → slight wobble.

## Annulus (Taiao Flower ▸ Petal)
6. **Taiao Flower**, delete all layers except **Petal**; Type **Cone**. (Pulling the profile down already gives a cap shape — usable for cap mushrooms.)
7. Raise ring + length segments together (Ctrl-select), Thickness 2, Subdivision 1.
8. Modifiers: **Curl** to flare the top out, **Displacer** + Noise for frills.
9. On the Plant trunk add a **Leaf** layer: count off, **Leaf on End** on; Geometry **Custom** = the Flower object. Orientation: Up Vector **−Y World**, Y rotation ~−100; position/scale to sit under the cap.

## Cap (Taiao Flower ▸ Pistil)
10. Second Flower, keep only **Pistil**; widen, Subdivisions ~4–5; edit the profile spline end (Ctrl-add points) so the underside gets geometry; add height.
11. **Displacer** + Noise (value 10) → gills. Mask the top: Layer shader with a **Gradient** (V direction) as inverted **layer mask** under the noise, so gills stay underneath and just curl over the rim.
12. Plant ▸ add **Custom Object** layer, drop the cap in; lower it to blend into the stalk.

## Redshift materials
- Lights: Sun & Sky rig + Dome HDRI, a bounce plane below to see the gills.
- Cap: **Color Ramp** off-white gills → orange rim band → red top, slight ramp noise → base colour; same colour into **Subsurface Color**, Subsurface **Weight** from an inverted ramp (SSS only underneath); Maxon Noise (Wavy Turbulence) → reflection roughness.
- Spots: second RS Standard (white) mixed by **Material Blender**; blend mask = Maxon Noise **Dents** (contrast-crushed to sparse dots) × inverted ramp via **Color Layer** Multiply (no spots on gills); same mask → **Bump** on both materials.
- Stalk/annulus: ramp muddy green-brown at the base → off-white, a little subsurface, Maxon Noise **Cranal** (scale 2.5) → bump.

## Newest equivalent
Still a Taiao job in Fused 2025.x; no NeXus equivalent.
