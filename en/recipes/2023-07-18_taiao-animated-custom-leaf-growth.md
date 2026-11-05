# Plant growth that plays back keyframed leaf unfurling (toLeaf animated modifiers as toPlant Custom leaf, Growth keyframe modes)

- Source: Top Tip Tuesday — toPlant Keyframe Growth — https://www.youtube.com/watch?v=KBSBpoeeVPo (2023-07-18)
- Host / generation: C4D; Taiao (toPlant, toLeaf)
- Goal: leaves on a growing plant unfurl using their own keyframed animation instead of just scaling on.

## Base
toPlant with a Trunk layer and a Leaf layer in **Basic** geometry mode (curve shape, furling, angle). Plain growth (global, or per-layer with variation) only scales the leaves — looks fake.

## Steps
1. Build one **toLeaf** whose Modifiers stack has Bend, Fold, Furling plus **three extra Furling layers with keyframed Furling Angle**: one for the main unfurl, one only at the tip, one wider global furl → a non-intersecting unfurl. [▶ 1:57](https://youtu.be/KBSBpoeeVPo?t=117)
2. toPlant ▸ Plant Layers ▸ Leaf layer ▸ Geometry: Basic → **Custom**, drag the animated toLeaf in. [▶ 2:45](https://youtu.be/KBSBpoeeVPo?t=165)
3. Playback alone shows no leaf animation: toPlant ▸ **Growth** tab ▸ click the **keyframe symbol** on the Leaf layer for the animation options. [▶ 3:14](https://youtu.be/KBSBpoeeVPo?t=194)
4. Mode **Growth Slider**: animating it scales and unfurls the leaves. Trigger **Random** (default) or **Sequence** (bottom → top). [▶ 3:39](https://youtu.be/KBSBpoeeVPo?t=219)
5. Mode **Global Growth Slider**: the plant's global growth drives it; leaves unfurl from the bottom up as it grows. [▶ 3:54](https://youtu.be/KBSBpoeeVPo?t=234)
6. Mode **Animate Slider**: separate slider just for the leaf animation (Sequence or Random), while the growth slider still handles scale. [▶ 3:39](https://youtu.be/KBSBpoeeVPo?t=219)
7. Trigger **Field**: add a **Linear field** pointing **−Y**, length greatly reduced; animate it up the plant → leaves unfurl as it passes. [▶ 5:00](https://youtu.be/KBSBpoeeVPo?t=300)
8. Works for custom toFlower objects too. [▶ 5:26](https://youtu.be/KBSBpoeeVPo?t=326)

## Newest equivalent
Same Taiao workflow in Fused 2025.x (Fused 2023.3 overhauled Taiao growth animation; 2024.2 added toLeaf venation + presets for richer custom leaves). No NeXus replacement.
