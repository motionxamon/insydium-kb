# Струя жидкости, бегущая по кругу вдоль кривой, мешинг с motion blur (сплайн nxFollowGeo + nxFluids PBD + nxMesher Transfer Velocity)

- Источник: NeXus for Blender Official Training — Follow Curve — https://www.youtube.com/watch?v=na6NGPw4XWM (2026-06-18)
- Хост / поколение: Blender (NeXus for Blender, G3); nxFollowGeo, nxFluids PBD, nxTurbulence, nxSpeed, nxMesher, nxCache; Cycles GPU
- Задача: турбулентная, брызгающая водяная лента, кружащая по Bezier circle, в рендере с motion blur меша.

## Шаги
1. **nxEmitter** Sphere, радиус **0.2**, направление **−Z**, Rate случайно **50,000/s**, радиус частиц **0.01**, эмиссия **120 кадров**. Bezier circle повёрнут по X лицом к камере; эмиттер на его краю. [▶ 0:38](https://youtu.be/na6NGPw4XWM?t=38)
2. **nxFollowGeo** ▸ Object = Bezier circle (сам определяет сплайн или полигоны). **Release ▸ Spline End: Loop**. **Extended Data**: удалите слой **Offset** по умолчанию (смещение ленты 0.2 m) — расстояние между частицами обеспечит солвер жидкости. [▶ 1:55](https://youtu.be/na6NGPw4XWM?t=115)
3. **nxFluids** солвер **PBD** (лучше всех справляется с сильными, нереалистичными силами). Вздутие при рождении = слишком плотно → включите проверку **Density** (убивает частицы, рождённые выше порога плотности). [▶ 3:19](https://youtu.be/na6NGPw4XWM?t=199)
4. Display эмиттера: точки меньше, Color **Gradient by Speed**, Auto Scale выкл., max 0.04. [▶ 4:42](https://youtu.be/na6NGPw4XWM?t=282)
5. **nxTurbulence** (Voronoi) Scale 120, Strength 25. [▶ 5:31](https://youtu.be/na6NGPw4XWM?t=331)
6. **nxSpeed** **последним** в стеке: слой Incremental со скоростью **0** — только как ограничитель, **Min 0.5, Max 4**. [▶ 6:17](https://youtu.be/na6NGPw4XWM?t=377)
7. Настройка nxFollowGeo: общая **Strength 50%**; больше **Attract Strength** = плотнее к кривой и глаже; **Active Range 2.5** позволяет струе разрываться и снова собираться. [▶ 8:47](https://youtu.be/na6NGPw4XWM?t=527)
8. Турбулентность поднята до Strength 35 → 45, Scale 130 для брызг. [▶ 11:02](https://youtu.be/na6NGPw4XWM?t=662)
9. Имитация поверхностного натяжения в PBD: поднимите **External Pressure** и немного **Repulsion**; **Smoothing Radius** 115–125 = длинные усики (медленнее); остановились на **105**. [▶ 10:39](https://youtu.be/na6NGPw4XWM?t=639)
10. **nxMesher** ▸ слой эмиттера: **Polygon Size 0.015**, **Radius 0.015**; Surface Type **Zhu-Bridson** (сам сглаживается, быстрый) вместо Spheres. Альтернатива: Radius 0.025 + сглаживание Mean Curvature 100%, 5 итераций (теряется немного деталей). [▶ 12:13](https://youtu.be/na6NGPw4XWM?t=733)
11. **Export Tags ▸ Transfer Velocity**, max speed **4** в каждом поле (совпадает с ограничением nxSpeed) → атрибут скорости вершин на меше. [▶ 14:58](https://youtu.be/na6NGPw4XWM?t=898)
12. Таймлайн 300 F, **nxCache** по умолчанию ▸ Build Cache (~20–30 s), затем отключите живые объекты. [▶ 15:28](https://youtu.be/na6NGPw4XWM?t=928)
13. Cycles GPU: noise threshold выше, 1000 сэмплов, без денойза; **Fast GI Approximation** для превью; **Motion Blur shutter 1 frame** (кэшированная скорость читается автоматически). Area-светильники (Normalize выкл.; например 50/40/30, Track To на nxFollowGeo в начале координат); Principled Transmission 1, roughness ~0, **IOR 1.33**; опционально DOF (F-stop ~3.3) на объект follow-geo. **Lock Interface** перед рендером. [▶ 18:39](https://youtu.be/na6NGPw4XWM?t=1119)

## Подводные камни
- Если оставить nxSpeed Incremental по умолчанию, частицы будут постоянно ускоряться.
- Слишком маленький радиус меша относительно polygon size выкидывает частицы из меша.

## Как сейчас (новые инструменты)
В бете 2026.1 **nxWarp Path / Helix** (режим Guide или Flow) формирует потоки вдоль пути для частиц, мешей и дыма; при более мягких силах реалистичная жидкость — через FLIP/APIC.
