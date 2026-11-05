# Струя жидкости вдоль спирального сплайна (nxFlowField Along/To Spline + Turbulence, PBD, удаление через nxQuestion при выходе)

- Источник: Top Tip Tuesday — Flowfield Fluids — https://www.youtube.com/watch?v=I9Fq5NPENdc (2026-09-22)
- Хост / поколение: Blender (NeXus for Blender 2026.0) — nxFlowField, nxFluids PBD, nxQuestion, nxMesher
- Задача: процедурная, управляемая лента жидкости, закручивающаяся вверх по кривой и исчезающая, когда покидает поле.

## Шаги
1. Кривая: Extra Curves ▸ Spirals (Archimedean), повыше и с небольшим ростом радиуса. [▶ 0:25](https://youtu.be/I9Fq5NPENdc?t=25)
2. **nxEmitter**: Shape **Disc**, направление **+Z**, Birth Rate **10,000**; размер точек на дисплее 2 (только отображение). [▶ 1:21](https://youtu.be/I9Fq5NPENdc?t=81)
3. **nxFlowField**: работает в домене — задайте размер Domain, охватывающий спираль (~**9 × 9 × 8 m**). Удалите слой по умолчанию **Radial** (он выталкивает наружу; с инвертированной силой — засасывает внутрь). [▶ 3:00](https://youtu.be/I9Fq5NPENdc?t=180)
4. Добавьте слой **Along Spline** (Targets & Surfaces) ▸ Generator ▸ спираль. [▶ 4:30](https://youtu.be/I9Fq5NPENdc?t=270)
5. Режим поля: переключите **Acceleration → Steer** — частицы сохраняют скорость эмиттера и лишь меняют направление, поэтому держатся кривой, а не разгоняются прочь. [▶ 5:42](https://youtu.be/I9Fq5NPENdc?t=342)
6. Детализация: voxel size домена **0.12 → 0.08**; поднимите Display ▸ Preview Density, чтобы видеть больше векторов; добавьте прозрачность отображения. [▶ 6:59](https://youtu.be/I9Fq5NPENdc?t=419)
7. Добавьте слой **Turbulence** (blend Add), поднимите его Generator Speed для анимации. [▶ 8:08](https://youtu.be/I9Fq5NPENdc?t=488)
8. Сверху добавьте слой **To Spline** (Add) → возвращает отбившиеся частицы. По умолчанию слишком сильный: уменьшите его Opacity, а лучше настройте **кривую falloff** (по умолчанию дистанция 2 m): 0 у сплайна с ростом до максимума на 2 m — притяжение действует только на улетевшие частицы; поднимите минимум кривой для более плотного следования. [▶ 10:00](https://youtu.be/I9Fq5NPENdc?t=600)
9. Выкрутите силу Turbulence, затем поставьте общий **Smoothing** поля на максимум; уменьшите scale noise для мелких завихрений. [▶ 12:12](https://youtu.be/I9Fq5NPENdc?t=732)
10. Скорость задаёт только emitter (режим Steer): Speed **2.5** с вариацией. [▶ 13:15](https://youtu.be/I9Fq5NPENdc?t=795)
11. **nxFluids PBD**: поднимите Smoothing Radius (~110), добавьте External Pressure и немного Repulsion для тягучих нитей; радиус частиц эмиттера **0.01 m**. [▶ 13:59](https://youtu.be/I9Fq5NPENdc?t=839)
12. Финал: вытащите последнюю точку кривой за пределы домена; в flow field ▸ **Flag on Escape**; **nxQuestion**: если флаг Escaped → Action **Kill Particle** (или задайте короткий lifespan с вариацией). [▶ 17:02](https://youtu.be/I9Fq5NPENdc?t=1022)
13. **nxMesher**: слой эмиттера, polygon size ~0.01, Surface **Zhu-Bridson**, radius ~0.015. [▶ 18:58](https://youtu.be/I9Fq5NPENdc?t=1138)

## Как сейчас (новые инструменты)
В 2026.1 beta **nxWarp** (Path / Helix, режим Guide или Flow) формирует потоки с меньшей настройкой, а в **nxFlowField** появился слой **Cyclic**; FLIP/APIC дают более тяжёлую жидкость, чем PBD.
