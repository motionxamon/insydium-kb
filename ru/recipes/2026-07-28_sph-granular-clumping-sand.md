# Слипающийся песок / снег через SPH Granular (nxFluids Granular: substeps, Friction, Stability, Cohesion)

- Источник: Top Tip Tuesday — NeXus Granular — https://www.youtube.com/watch?v=rkuNbceXolQ (2026-07-28)
- Хост / поколение: Blender (NeXus for Blender 2026.0) — nxEmitter Hexagonal, nxFluids SPH Granular, nxCollider, nxGravity
- Задача: Сюзанна из гранул падает и раскалывается на комья (сухой песок → комковатый песок/снег).

## Шаги
1. Большая скрытая плоскость + **nxCollider**: Bounce 0, Friction высокий (**80%**, до 100 для слипания). **nxGravity** по умолчанию. [▶ 0:57](https://youtu.be/rkuNbceXolQ?t=57)
2. Сюзанна (Subdivision 2, применён), поднята и повёрнута. **nxEmitter**: Object, **Volume**, **Shot**, **Hexagonal**, Speed 0. Display Spheres показывает реальную упаковку; радиус **0.01 m** для большего количества гранул (в продакшене: 3–4 M+). [▶ 2:14](https://youtu.be/rkuNbceXolQ?t=134)
3. **nxFluids** ▸ **SPH** ▸ Fluid Type **Granular** → сухой песок. Display Gradient по **Granular**, Auto Scale выкл., 0–20. [▶ 4:02](https://youtu.be/rkuNbceXolQ?t=242)
4. Substeps **6 → 12** и **Adaptive выкл.** — ключевая настройка для гранул (фиксированно высокие substeps на каждом шаге). [▶ 5:45](https://youtu.be/rkuNbceXolQ?t=345)
5. Friction **100%** → появляются первые комья; **Friction Iterations 30** (50 для крупных комьев; медленнее). [▶ 9:25](https://youtu.be/rkuNbceXolQ?t=565)
6. **Stability** = порог относительной скорости, выше которого гранулы вырываются из трения: ниже = много мелких кусков, **60** = куски крупнее. [▶ 9:19](https://youtu.be/rkuNbceXolQ?t=559)
7. На emitter **Subframe Emit выкл.**, чтобы все гранулы падали синхронно и не разделялись в воздухе. [▶ 7:47](https://youtu.be/rkuNbceXolQ?t=467)
8. **Cohesion** — пружинящий constraint: высокие значения (50) выглядят как желе; держите ≤ значения по умолчанию **10** (тестировали 5). [▶ 9:51](https://youtu.be/rkuNbceXolQ?t=591)
9. Слишком прыгучие удары: Smoothing Radius **120%** (медленнее); затем поднимите максимум отображения до ~40. [▶ 11:24](https://youtu.be/rkuNbceXolQ?t=684)
10. Трение коллайдера: низкое = гранулы растекаются при приземлении; полное = масса цепляется и остаётся комом. [▶ 13:12](https://youtu.be/rkuNbceXolQ?t=792)

## Как сейчас (новые инструменты)
В бете 2026.1 — **nxMPM** (снег, песок) / пресеты **nxMaterial** (Snow packed/sticky, Sand wet).
