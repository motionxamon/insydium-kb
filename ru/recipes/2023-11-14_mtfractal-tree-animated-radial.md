# Анимированное высокополигональное фрактальное дерево (mtFractal в режиме Tree, Multi-Instance, Levels + mtInset + mtShellGen)

- Источник: Top Tip Tuesday — mtFractal Tree — https://www.youtube.com/watch?v=2U0MH6xdGAk (2023-11-14)
- Хост / поколение: C4D; **MeshTools** (mtFractal, mtInset, mtShellGen)
- Задача: замысловатое фрактальное дерево из копий, которое раскрывается при анимации и при этом не тормозит во viewport.

## Шаги
1. **mtFractal** с высоким **Cube** в качестве дочернего объекта; Core Shape **Tree** (по умолчанию); Clone Type **Multi-Instance**. [▶ 0:42](https://youtu.be/2U0MH6xdGAk?t=42)
2. **Steps** (по умолчанию 3) добавляют уровни; **Branches** на шаг 2 → 3 для объёмного дерева (поиграйтесь на 4 steps / 2 branches). Growth и scale оставляем по умолчанию. [▶ 1:39](https://youtu.be/2U0MH6xdGAk?t=99)
3. Анимируем **Angle Open** (по умолчанию 45°; 0 = закрыто, 180° = загнуто назад к основанию). [▶ 2:06](https://youtu.be/2U0MH6xdGAk?t=126)
4. Анимируем угол **Radial** (при 0 выглядит как одна ветка) — на **6 steps / 4 branches** дерево эффектно раскрывается. [▶ 2:30](https://youtu.be/2U0MH6xdGAk?t=150)
5. **Number of Copies**: 2 даёт зеркало, 4 или 6 — равномерно расставленные копии (верните на 1). [▶ 2:55](https://youtu.be/2U0MH6xdGAk?t=175)
6. **Levels**: добавляем уровень для **Step Level 2**, чтобы переопределить углы только там (его углы начинаются с 0), или переключаем его тип **Angle → Branch**, чтобы задать число веток на шаг (например, 2 против 4 на остальных). Уровни складываются. [▶ 4:59](https://youtu.be/2U0MH6xdGAk?t=299)
7. Украшаем: помещаем куб в **mtInset** (поднимаем amount, включаем опцию, скрывающую вставленные грани → вид wireframe), кладём inset в **mtShellGen** (добавляем толщину), затем возвращаем shell gen обратно в mtFractal. [▶ 5:45](https://youtu.be/2U0MH6xdGAk?t=345)
8. Анимируем Radial; добавляем steps/branches — viewport остаётся отзывчивым благодаря multi-instances. [▶ 6:24](https://youtu.be/2U0MH6xdGAk?t=384)
