# Имитация качения твёрдых тел с помощью слоя nxSpin "Roll"

- Источник: Top Tip Tuesday — Rolling Particles — https://www.youtube.com/watch?v=OFx-ALGOlAU (2026-08-04)
- Хост / поколение: C4D, NeXus (nxConstraints, слой nxSpin Roll, nxTurbulence) + xpGenerator
- Задача: сотни платоновых тел кувыркаются во вращающемся кубе — выглядит как rigid-body sim, но это полностью управляемые частицы.

## Дерево сцены
```
Rotating Cube (xpCollider tag)
xpEmitter (spherical particles inside the cube) + nxGravity
nxConstraints  — Iterations ≥3; layers: Collisions, Friction (Strength/Static/Kinetic 100%, small Radius, Connection Limit ~18)
nxSpin        — default Range layer → change to **Roll**
nxTurbulence  — Voronoi(default), high Strength, big Scale
xpGenerator   — Emitter, Use Multiple Child Objects: Randomly, Clone Type Multi-Instance
   └─ 3 Platonic primitives
```

## Шаги
1. nxConstraints со слоем **Collisions** (≥3 итераций) → частицы перестают проникать друг в друга и катятся.
2. Инстансим несферические формы через **xpGenerator** (случайные дочерние объекты, **Multi-Instance** — самый быстрый вариант). Проблема: инстансы сохраняют ориентацию и скользят.
3. **nxSpin** → переключаем стандартный слой **Range** на **Roll**: частицы вращаются в зависимости от скорости и направления движения → читается как кувыркание твёрдых тел, при этом контроль над частицами сохраняется (kill, цвет, модификаторы).
4. Добавляем nxTurbulence для хаоса; если движение становится слишком дёрганым, добавляем слой constraints **Friction**, чтобы погасить контакты.
5. Цвет на частицу (например, градиент nxColor по Speed, 0–300 cm/s) **не** отображается при **Multi-Instance** (всё считается одним объектом) → переключаем xpGenerator на **Render Instances** (медленнее).

## Когда применять
Объекты примерно округлой формы, камера не слишком близко. Для точных контактов используйте rigid bodies xpBullet или, в свежей beta, nxMPM / грядущие rigid bodies в NeXus.
