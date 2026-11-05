# Колышущиеся стеклянные щупальца с частицами на концах (xpTendril + xpTrail Tendrils + xpSplineMesher + тег xpTrailTip)

- Источник: Top Tip Tuesday — xpTrail Tip — https://www.youtube.com/watch?v=M4z3kOU4YEw (2023-12-19)
- Хост / поколение: C4D; **CPU G1 X-Particles** (xpEmitter, xpTendril, xpTurbulence, xpTrail, xpSplineMesher, xpColor)
- Задача: стилизованная подводная сцена — закрученные стеклянные щупальца растут из ландшафта, и на конце каждого сидит цветная сфера.

## Исходная сцена
**xpEmitter** с ландшафта TerraformFX, Polygon Area; **Shot 50**, радиус No Intersection **15 cm**, скорость **150 cm**, радиус **3**.

## Шаги
1. Modifiers ▸ Generate ▸ **xpTendril**: Full Scene Length **выкл.**, Tendril Length **16 кадров ±4**. [▶ 0:57](https://youtu.be/M4z3kOU4YEw?t=57)
2. Motion ▸ **xpTurbulence**, сила **18** (щупальца выглядят неподвижными, но на деле это постоянный поток новых частиц). [▶ 1:32](https://youtu.be/M4z3kOU4YEw?t=92)
3. Emitter ▸ Groups: дважды Ctrl+Alt-клик → группы 1 и 2, **First Group Only**. xpTendril ▸ **Tendril Group = группа 2**. [▶ 2:01](https://youtu.be/M4z3kOU4YEw?t=121)
4. Группа 1 (источники): Editor Display **None**; у группы 2 радиус совсем маленький (~0.7). [▶ 2:16](https://youtu.be/M4z3kOU4YEw?t=136)
5. **xpTrail** с эмиттером, **Algorithm: Tendrils** → по одному динамическому трейлу на каждое щупальце. [▶ 3:02](https://youtu.be/M4z3kOU4YEw?t=182)
6. **xpSplineMesher** на трейл: Joints и Vertex Colors выкл., **1 subdivision**, Size **1.5**, сужение к острию графиком **Scale Along Spline**. Трейл скрыть, назначить стеклянный материал. [▶ 3:41](https://youtu.be/M4z3kOU4YEw?t=221)
7. Трейл ▸ Tags ▸ X-Particles ▸ тег **xpTrailTip** → новый эмиттер «emitter tip». В списке Modifiers этого эмиттера **исключить xpTendril**; отображение Spheres. [▶ 4:50](https://youtu.be/M4z3kOU4YEw?t=290)
8. **xpColor**, режим **Immediate**, Shader **Gradient** (Spherical) с пресетом, **Turbulence 20%**. [▶ 5:24](https://youtu.be/M4z3kOU4YEw?t=324)
9. Камера с DOF; плоскость фона. [▶ 5:36](https://youtu.be/M4z3kOU4YEw?t=336)

## Как сейчас (новые инструменты)
Эффекты щупалец/ветвления в NeXus 2026 (G3) — это **nxDendrite**, трейлы — **nxTrail**; сама связка xpTrailTip/xpTendril в Fused по-прежнему работает только на CPU.
