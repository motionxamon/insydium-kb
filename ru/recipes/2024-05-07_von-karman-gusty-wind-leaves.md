# Реалистичные листья на порывистом ветру (nxWind Von Karman: Scale Distance + Friction Velocity, simple spin, xpGenerator Multi-Instance)

- Источник: Top Tip Tuesday — Realistic Gusty Wind for NeXus Particles — https://www.youtube.com/watch?v=RRKxOyJVrO8 (2024-05-07)
- Хост / поколение: C4D; xpEmitter + NeXus GPU (nxWind, nxGravity) + CPU xpGenerator
- Задача: листья кувыркаются и подлетают от вихрей и порывов (подходит и для дюн, конфетти).

## Исходная сцена
xpEmitter Rectangle, Rate 20/s, радиус 5 (var 2), отображение — залитая плоскость. **nxGravity** 40, **nxWind** по умолчанию дует по +Z; пол с xpCollider.

## Шаги
1. Emitter ▸ Extended Data ▸ **Rotation: Random**; **Simple Spin** включён, 6 по каждой оси, вариация 5. [▶ 1:36](https://youtu.be/RRKxOyJVrO8?t=96)
2. Режим nxWind Standard → **Von Karman** (реалистичные вихри даже на дефолтах). [▶ 1:55](https://youtu.be/RRKxOyJVrO8?t=115)
3. **Wind strength 30**, чтобы листья в основном оседали; арт-дирекшн — через настройки турбулентности. [▶ 2:34](https://youtu.be/RRKxOyJVrO8?t=154)
4. **Scale Distance 5000 cm** → порывы влияют шире. [▶ 2:52](https://youtu.be/RRKxOyJVrO8?t=172)
5. Поднимайте **Friction Velocity**, усиливая порывы, пока часть листьев не начнёт подлетать; остановитесь на умеренном значении. [▶ 2:52](https://youtu.be/RRKxOyJVrO8?t=172)
6. **xpGenerator** от emitter, дочерние объекты = 4 однополигональные плоскости с материалами листьев с alpha-вырезом; **Multiple children ▸ Random**, тип клонов **Multi-Instance**. [▶ 5:02](https://youtu.be/RRKxOyJVrO8?t=302)
7. Достаточно дёшево, чтобы поднять до **500/s**; для более плотной толпы снова уменьшите Friction Velocity.

## Как сейчас (новые инструменты)
В NeXus 2026.1 у **nxWarp** есть warp Wind gust wave; **nxGenerator** заменяет xpGenerator на nxEmitters.
