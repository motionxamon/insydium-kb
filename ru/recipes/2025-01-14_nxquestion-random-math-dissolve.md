# Случайное растворение по полю (nxQuestion Field + Group + Math Random)

- Источник: Top Tip Tuesday — Random Math Effects — https://www.youtube.com/watch?v=wO5-UoWNTkA (2025-01-14)
- Хост / поколение: C4D; NeXus G2 (nxFollowGeo, nxTurbulence, nxQuestion) на xpEmitter; сферическое поле C4D
- Задача: частицы, облепившие текст, отпускаются движущимся полем и затухают вразнобой, а не все разом.

## Исходная сцена
xpEmitter из Connect/объединения текста → **nxFollowGeo** с тем же объединением в качестве поверхности + сильный **nxTurbulence**. По сцене проходит анимированное сферическое поле.

## Шаги
1. Эмиттер ▸ Groups: дважды Ctrl-клик **Add Group**, режим **First Group Only** (все рождаются в группе 1). [▶ 0:52](https://youtu.be/wO5-UoWNTkA?t=52)
2. nxFollowGeo ▸ Groups Affected: только **group 1**. [▶ 1:00](https://youtu.be/wO5-UoWNTkA?t=60)
3. **nxQuestion** ▸ вкладка Field: добавьте анимированное сферическое поле. [▶ 1:27](https://youtu.be/wO5-UoWNTkA?t=87)
4. Вопрос 1: Particle **Field > 0** (где угодно внутри) → Action **Set Group = group 2** → частица освобождается от FollowGeo, дальше работает турбулентность. [▶ 1:55](https://youtu.be/wO5-UoWNTkA?t=115)
5. Вопрос 2: Particle **Group = 2** → Action **Set Age 0** (один раз) + Action **Set Lifespan 45** кадров. [▶ 3:04](https://youtu.be/wO5-UoWNTkA?t=184)
6. Одинаковые 45 F выглядят как резкий щелчок, поэтому добавьте под Q2 дочерний вопрос в режиме **And**: **Math ▸ Random**, Time Variation **Particle**, диапазон **0–100**, условие **> 70**. Перенесите оба действия под этот подвопрос. [▶ 3:54](https://youtu.be/wO5-UoWNTkA?t=234)
7. Каждый кадр каждая частица получает новое число, поэтому сброс возраста/lifespan срабатывает в разные моменты → мягкое, рассыпанное затухание. [▶ 4:18](https://youtu.be/wO5-UoWNTkA?t=258)

## Как сейчас (новые инструменты)
nxFalloff (16 режимов в 2026.1 beta, например Sphere) может заменить поле C4D; в Fused 2025.4 в nxQuestion появилась встроенная вариация, которая может избавить от случайного подвопроса.
