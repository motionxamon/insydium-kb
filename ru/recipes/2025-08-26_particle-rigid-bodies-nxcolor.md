# Частицы → rigid body в C4D с цветом от nxColor (xpGenerator + теги Simulation + Redshift Object Color)

- Источник: Top Tip Tuesday — Particle Rigid Bodies — https://www.youtube.com/watch?v=eBnMW0v43Ac (2025-08-26)
- Хост / поколение: C4D; эмиттеры NeXus + **CPU xpGenerator** + теги симуляции C4D **Rigid Body / Collider** + Redshift
- Задача: точные столкновения объект–объект (черепа в коробке) солвером C4D, при этом цветом по-прежнему управляет NeXus.

## Шаги
1. Начните со сцены NeXus; **отключите nxGravity и nxConstraints** и xpCollider на коробке — физику берёт на себя солвер C4D.
2. XP System ▸ Generators ▸ **xpGenerator** на каждый эмиттер (переименуйте в "generator main", "generator lights"); копируемая геометрия — **дочерняя** к генератору.
3. На каждый генератор: **Tags ▸ Simulation ▸ Rigid Body**. На коробку: **Collider Body**, Collider ▸ сторона **Back** (запирает объекты внутри).
4. Частицы становятся rigid body при рождении (скорость эмиттера игнорируется, действует гравитация C4D). Поздний эмиттер (кадр 150) добавляет ещё.
5. Мелкие объекты слишком лёгкие, чтобы толкать крупные → Rigid Body ▸ Mass ▸ **Density ~15**.
6. Цвет: слои **nxColor** → *Gradient by Parameter* на **Random** (случайный цвет на частицу) + верхний слой чёрный→белый на **Age** в режиме **Multiply** → объекты рождаются чёрными и проявляются в свой случайный цвет. Цвет передаётся сгенерированным объектам.
7. Redshift: в материале Ctrl-клик по порту Subsurface Color (или Base) → нода **Color User Data** ▸ preset **Object ▸ Object Color** (не Particle Color — это геометрия).

## Подводные камни
- Пауза при проигрывании, когда появляются новые объекты (солвер перестраивается).
- Для геометрии xpGenerator используйте Object Color, а не Particle Color.

## Как сейчас (новые инструменты)
Следующая beta NeXus (анонс 2026-11-03) добавляет нативные **unified rigid bodies** с двусторонним взаимодействием; до тех пор этот мост через солвер C4D — точный способ. См. whats-new.md.
