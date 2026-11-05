# Тянущиеся и рвущиеся волокна (nxConstraints Birth + трейлы по констрейнтам + xpTrailDeformer)

- Источник: Top Tip Tuesday — GPU Constraints Sim — https://www.youtube.com/watch?v=_7bYCGydqXo (2025-09-16)
- Хост / поколение: NeXus (nxConstraints, nxFluids SPH, nxKill) + CPU xpTrail / xpTrailDeformer
- Задача: тягучие нити, которые тянутся между частицами и рвутся, отрендеренные как мягкие изогнутые волокна.

## Шаги
1. Анимированный эмиттер, распыляющий на коллайдер-трубу; **nxGravity 400**; **nxFluids SPH** substeps 6 (взаимодействие частица–частица); границы **nxKill**. [▶ 0:27](https://youtu.be/_7bYCGydqXo?t=27)
2. **nxConstraints → Connections Birth**: Connection Limit 8, Radius ~20. Показать связи: Display эмиттера ▸ **Display Constraints**. [▶ 1:21](https://youtu.be/_7bYCGydqXo?t=81)
3. Связи рвутся при **Break 50% (Relative Connected)** по умолчанию → **Break 500%**, понизьте **Stiffness** (тянучее). [▶ 2:22](https://youtu.be/_7bYCGydqXo?t=142)
4. Рендерящиеся линии: **xpTrail** → **Algorithm: Constraints → Birth** (вместо трассировки путей). [▶ 3:27](https://youtu.be/_7bYCGydqXo?t=207)
5. Констрейнты — прямые от точки к точке → смягчаем: xpTrail Spline **Intermediate Points Uniform 8** + дочерний **xpTrailDeformer** (формула по Y, небольшая **Amplitude ~1 cm**, подобранная Wavelength); используйте сплайн деформера, чтобы концы не двигались (0 в начале/конце, полная в середине). [▶ 5:12](https://youtu.be/_7bYCGydqXo?t=312)
