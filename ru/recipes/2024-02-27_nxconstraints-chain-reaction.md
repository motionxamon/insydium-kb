# Расходящаяся физическая цепная реакция (nxConstraints Birth + Collisions, nxScale/nxGravity с маппингом на Distance Travelled)

- Источник: Top Tip Tuesday — nxConstraints Reaction — https://www.youtube.com/watch?v=9w-L9qWwGqQ (2024-02-27)
- Хост / поколение: C4D; NeXus GPU (nxConstraints, nxScale, nxGravity, Mapping) + CPU xpTrail / xpSplineMesher
- Задача: поле связанных частиц в покое; лёгкий толчок — и они растут, задевают соседей и запускают волну.

## Исходная сцена
Плоскость пола + цилиндр, оба с тегами xpCollider. Эмиттер в режиме Object на плоскости (polygon area), **Shot 6000**, радиус 3.

## Шаги
1. **nxConstraints ▸ Birth**: до 3 связей в пределах **65 cm**, Stiffness **60%**, разрыв при растяжении более **150%** от длины при рождении. Их видно через Display эмиттера ▸ **Display Constraints**.
2. Добавьте слой **Collisions** (частица-частица); **Iterations 8** (точнее и жёстче).
3. **nxScale**: параметр Radius, операция **Set Value 10**.
4. nxScale ▸ Mapping ▸ **Distance (travelled)** → значение Radius, диапазон 0–100 cm. Кривая: старт с 0, почти сразу пик на максимуме, затем плавный спад — у несдвинутых частиц радиус 0, так что пока ничего не происходит.
5. Анимируйте/двигайте **цилиндр** в частицы как триггер: сдвинутые частицы растут, бьют соседей, и так далее.
6. **nxGravity** (по умолчанию) с Mapping ▸ Distance travelled → Gravity Strength, 0–100 cm: ноль до ~40 cm, полная к ~60 cm.
7. Быстрее распространение: диапазон distance в nxScale 100 → **50 cm**.
8. Чтобы рендерить/мешить пружины: **xpTrail ▸ Algorithm: Constraints ▸ Birth Constraints** вкл. → меш через **xpSplineMesher**.

## Как сейчас (новые инструменты)
В NeXus 2026 всё так же; **nxPin** (2026.1 beta) может закрепить части полотна; списки nxFalloff на каждом слое — для пространственного контроля.
