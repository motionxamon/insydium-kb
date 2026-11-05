# Органичный колышущийся шипастый шар (mtSubdivider + mtInset на soft body через xpDynamics)

- Источник: Top Tip Tuesday — Dynamic MeshTools — https://www.youtube.com/watch?v=3YmhMKdK0o4 (2024-02-06)
- Хост / поколение: C4D; MeshTools (mtSubdivider, mtInset) + CPU X-Particles (xpDynamics tag, xpTurbulence, xpAttractor)
- Задача: процедурные анимированные геометрические шипы на мягкой, сминающейся soft-body сфере.

## Шаги
1. Сфера, тип **Icosahedron**. [▶ 0:14](https://youtu.be/3YmhMKdK0o4?t=14)
2. **mtSubdivider** (сфера дочерняя): level **5**, управление через **Noise shader** типа **Box** с пониженным High Clip → неравномерное подразбиение. [▶ 0:45](https://youtu.be/3YmhMKdK0o4?t=45)
3. **mtInset** (subdivider дочерний): поднимите Amount и Offset → шипы. [▶ 1:08](https://youtu.be/3YmhMKdK0o4?t=68)
4. Inset **Fields ▸ Random field**: Perlin, scale ~530, animation speed 20% → шипы «рябят»; поднимите Offset для преувеличения. [▶ 1:41](https://youtu.be/3YmhMKdK0o4?t=101)
5. Отключите MeshTools; на сферу добавьте **xpDynamics tag ▸ add Emitter** (по частице на вершину). [▶ 3:02](https://youtu.be/3YmhMKdK0o4?t=182)
6. **xpTurbulence**: scale 150, strength 15. [▶ 3:25](https://youtu.be/3YmhMKdK0o4?t=205)
7. В теге динамики **Rigidity** 0.5 → 0.1 (рыхлая). **xpAttractor** (по умолчанию) держит её по центру; **Pressure 0.5**; rigidity обратно до **0.4**, чтобы держала форму. [▶ 3:43](https://youtu.be/3YmhMKdK0o4?t=223)
8. Включите MeshTools обратно — процедурные шипы теперь едут на динамическом меше. Random field ▸ Remapping ▸ Contour **Curve** для более острого контраста шипов. [▶ 5:35](https://youtu.be/3YmhMKdK0o4?t=335)

## Как сейчас (новые инструменты)
Soft bodies на GPU: **nxMPM elastic** + **nxDeformer** (2026.1 beta), с nxTurbulence/nxAttract.
