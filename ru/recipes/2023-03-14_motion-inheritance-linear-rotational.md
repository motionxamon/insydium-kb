# Частицы, наследующие движение объекта-эмиттера (Motion Inheritance linear + rotational, xpTurbulence)

- Источник: Top Tip Tuesday — Motion Inheritance — https://www.youtube.com/watch?v=pwEBS2tOgNw (2023-03-14)
- Хост / поколение: C4D; CPU X-Particles (xpEmitter, xpTurbulence)
- Задача: органичные завитки в духе advection, которые задаёт хаотично движущийся объект.

## Исходная сцена
Platonic с C4D-тегом **Vibrate** (позиция + вращение). xpEmitter: форма Object, эмиссия с **Edges**, все кадры, lifespan **50 ± 10**, speed 0.

## Шаги
1. Для сравнения (по желанию): **xpTurbulence** (Modifiers ▸ Motion) с настройками по умолчанию — красиво, но никак не связано с движением объекта. На время настройки отключите.
2. Отображение: точки, цвет **Gradient Parameter** по Age (пастельный пресет: жёлтые молодые → розовые старые).
3. Emission ▸ **Motion Inheritance** вкл. Типы: **Linear Direction** и **Rotational Direction**.
4. Сначала только Linear: при хаотичном движении эффект очень сильный — сильно уменьшите **Speed Blend**.
5. Статичные частицы на первом кадре (наследовать пока нечего): выключите Emit All Frames, эмиссия с **кадра 2 → 600** (конец сцены).
6. Только Rotational — чтобы увидеть вклад вращения; финал = оба включены с низким Speed Blend.
7. Снова включите турбулентность: Strength **16**, масштаб чуть меньше.

## Как сейчас (новые инструменты)
Motion inheritance в nxEmitter + **nxTurbulence** (Curl Add / Curl Blend) на GPU.
