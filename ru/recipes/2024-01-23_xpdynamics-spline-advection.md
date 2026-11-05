# Текстовый сплайн, раздуваемый взрывом (xpDynamics на сплайне + адвекция xpExplosiaFX)

- Источник: Top Tip Tuesday — Spline Advection — https://www.youtube.com/watch?v=2YkjQgmo8Ic (2024-01-23)
- Хост / поколение: C4D; CPU X-Particles (xpExplosiaFX + Source tag, xpDynamics tag)
- Задача: сделать любой сплайн C4D динамическим и дать симуляции дыма/огня его толкать.

## Шаги
1. Частицы-источник: **Shot**, 45 за кадр в течение 30 F, lifespan 30 (var 10), скорость 150 (var 50), радиус 5 (var 3). [▶ 0:36](https://youtu.be/2YkjQgmo8Ic?t=36)
2. **Extended Data** emitter: Temperature 1, Fuel 1; добавьте **xpExplosiaFX Source tag** (по умолчанию). [▶ 1:13](https://youtu.be/2YkjQgmo8Ic?t=73)
3. Source tag: **Velocity 100% → 500%**, чтобы огонь следовал направлению частиц, а не поднимался строго вверх. [▶ 1:43](https://youtu.be/2YkjQgmo8Ic?t=103)
4. Текстовый сплайн ▸ **xpDynamics tag** → по частице на каждую промежуточную точку. В теге **добавьте Emitter** («emitter dynamic») — для адвекции нужны настоящие частицы emitter-а. [▶ 2:54](https://youtu.be/2YkjQgmo8Ic?t=174)
5. xpExplosiaFX ▸ Advection ▸ **Advect Particles** включить. [▶ 3:24](https://youtu.be/2YkjQgmo8Ic?t=204)
6. Emitter-источник ▸ вкладка Modifiers: **исключите xpExplosiaFX** — иначе его адвектирует собственный взрыв и он дёргается. [▶ 4:05](https://youtu.be/2YkjQgmo8Ic?t=245)
7. Dynamics tag: **Rigidity 0**, затем **Constraints ▸ добавьте Structure** constraint (снизьте его силу), чтобы буквы покачивались, но держались вместе. [▶ 5:08](https://youtu.be/2YkjQgmo8Ic?t=308)
8. Процедурно: поменяйте текст — всё продолжит работать. Анимируйте rigidity keyframe-ами вверх ближе к концу шота, чтобы форма вернулась к исходной. [▶ 6:14](https://youtu.be/2YkjQgmo8Ic?t=374)

## Как сейчас (новые инструменты)
GPU-дым — **nxExplosiaFX** (Fused 2025.4); меш/сплайн, следующий за частицами, — **nxDeformer** (бета 2026.1); прежде чем переходить, проверьте, покрывает ли это адвекция в NeXus.
