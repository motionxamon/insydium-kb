# Чистая эмиссия частиц с mocap-персонажа (xpJoin → Alembic → запекание PLA)

- Источник: Top Tip Tuesday — X-Particles and Mocap — https://www.youtube.com/watch?v=Qd_kEHZ-4JY (2025-08-12)
- Хост / поколение: C4D (mocap из Asset Browser Maxon + character solver) + эмиттер X-Particles / xpTrail (для nxEmitter работает так же)
- Задача: частицы, жёстко привязанные к скиннутому mocap-персонажу, без отставания на один кадр.

## Шаги
1. Asset Browser ▸ Motion Capture: mocap-клип (например, «Fireball») + подходящая модель-марионетка; на теге **Character Solver** марионетки поставьте Source = тег **Character Definition** клипа.
2. Alt + **xpJoin** над null'ом меша → части тела становятся одним объектом.
3. Эмиссия прямо со скиннутого / объединённого объекта **отстаёт на один кадр** (порядок вычислений C4D — на месте не исправить).
4. Решение: ПКМ по xpJoin ▸ **Bake as Alembic** → это всё ещё генератор, всё ещё отстаёт → перетащите в Timeline Dope Sheet ▸ Functions ▸ **Bake Objects** с **Create Copy + PLA** → полигональный объект с анимацией на уровне точек.
5. Эмиттер: режим Object, **Polygon Area**, **Stick Particles to Source**, Shot ~3000 → держится намертво.
6. Запечённый меш сохраняет отдельные части → выделите кисти в режиме полигонов ▸ Set Selection → передайте **тег полигонального выделения** в эмиттер → эмиссия только с кистей.
7. Пример эффекта: эмиссия 25/кадр + **xpTrail** (length 25, variation 12) → световые шлейфы за движениями.

## Подводные камни
В продакшене держите Alembic / оригинал как бэкап; файлы с PLA тяжёлые.

## См. также
«Mocap Sim Proxy» (2026) — про использование прокси для симуляций.
