# Чистая эмиссия частиц с mocap-персонажа (xpJoin → Alembic → запекание PLA)

- Источник: Top Tip Tuesday — X-Particles and Mocap — https://www.youtube.com/watch?v=Qd_kEHZ-4JY (2025-08-12)
- Хост / поколение: C4D (mocap из Asset Browser Maxon + character solver) + эмиттер X-Particles / xpTrail (для nxEmitter работает так же)
- Задача: частицы, жёстко привязанные к скиннутому mocap-персонажу, без отставания на один кадр.

## Шаги
1. Asset Browser ▸ Motion Capture: mocap-клип (например, «Fireball») + подходящая модель-марионетка; на теге **Character Solver** марионетки поставьте Source = тег **Character Definition** клипа. [▶ 0:40](https://youtu.be/Qd_kEHZ-4JY?t=40)
2. Alt + **xpJoin** над null'ом меша → части тела становятся одним объектом. [▶ 1:24](https://youtu.be/Qd_kEHZ-4JY?t=84)
3. Эмиссия прямо со скиннутого / объединённого объекта **отстаёт на один кадр** (порядок вычислений C4D — на месте не исправить). [▶ 2:51](https://youtu.be/Qd_kEHZ-4JY?t=171)
4. Решение: ПКМ по xpJoin ▸ **Bake as Alembic** → это всё ещё генератор, всё ещё отстаёт → перетащите в Timeline Dope Sheet ▸ Functions ▸ **Bake Objects** с **Create Copy + PLA** → полигональный объект с анимацией на уровне точек. [▶ 4:30](https://youtu.be/Qd_kEHZ-4JY?t=270)
5. Эмиттер: режим Object, **Polygon Area**, **Stick Particles to Source**, Shot ~3000 → держится намертво. [▶ 6:08](https://youtu.be/Qd_kEHZ-4JY?t=368)
6. Запечённый меш сохраняет отдельные части → выделите кисти в режиме полигонов ▸ Set Selection → передайте **тег полигонального выделения** в эмиттер → эмиссия только с кистей. [▶ 5:55](https://youtu.be/Qd_kEHZ-4JY?t=355)
7. Пример эффекта: эмиссия 25/кадр + **xpTrail** (length 25, variation 12) → световые шлейфы за движениями. [▶ 6:23](https://youtu.be/Qd_kEHZ-4JY?t=383)

## Подводные камни
В продакшене держите Alembic / оригинал как бэкап; файлы с PLA тяжёлые.

## См. также
«Mocap Sim Proxy» (2026) — про использование прокси для симуляций.
