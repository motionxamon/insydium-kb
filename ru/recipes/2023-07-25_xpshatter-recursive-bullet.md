# Рекурсивное разрушение при ударе (слои Voronoi в xpShatter с триггером Collision, твёрдые тела Bullet)

- Источник: Top Tip Tuesday — xpShatter Recursion — https://www.youtube.com/watch?v=oY_h7s9RyVI (2023-07-25)
- Хост / поколение: C4D; G1 CPU (xpShatter + теги INSYDIUM Bullet)
- Задача: модель волка при приземлении раскалывается на крупные куски, а те при следующих ударах раскалываются снова (и снова) — полностью процедурно.

## Шаги
1. Подними модель; выдели её и плоскость пола ▸ Tags ▸ INSYDIUM Bullet ▸ **Rigid Body**. Тег пола ▸ Simulation ▸ режим **Collider**.
2. X-Particles Generators ▸ **xpShatter**; сделай волка его дочерним объектом и **перенеси тег Bullet наверх, на xpShatter** → динамические осколки.
3. Display: сними галку **Draw Cut Edges**.
4. UV: перенеси материал на xpShatter; Selections ▸ создай **выделение полигонов внешних граней**, перетащи этот тег в поле Selection материала → снаружи сохраняется UV-развёртка, внутренние грани получают свой материал.
5. Point generator первого слоя **Voronoi**: **40 → 12** точек (меньше кусков, но крупнее).
6. Add Layer ▸ второй слой **Voronoi**, point generator **10** точек (каждый кусок может расколоться на 10).
7. Его Trigger: Always → **Collision**; отключи particle-particle и particle-polygon, оставь **xpBullet collisions**. **Collision Speed 4**, вариация **2** (при 3/2 ломалось слишком сильно; при 5/3 оставалось много крупных кусков).
8. Третий слой Voronoi: **10** точек, триггер Collision (Bullet), speed **2**, вариация **2** → третий уровень осколков.

## Как сейчас (новые инструменты)
**nxShatter** (бета NeXus 2026.1, GPU): Voronoi/Glass/Wood/Bricks с подразрушением и триггерами, управляется эмиттером или повреждениями nxMPM. В стабильном Fused 2025.4: xpShatter + Bullet, как показано. Учти, что GPU-динамика твёрдых тел пока только анонсирована (в следующей бете), так что для столкновений здесь по-прежнему нужен Bullet.
