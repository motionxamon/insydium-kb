# Стилизованные микроскопические клетки в чашке (nxFluids PBD External Pressure + nxConstraints Surface Tension + Initial State)

- Источник: Top Tip Tuesday — Micro Cells — https://www.youtube.com/watch?v=Z_JR2deKwqE (2024-08-20)
- Хост / поколение: C4D; NeXus G2 (nxGravity, nxTurbulence, nxFluids PBD, nxConstraints, nxColor) на xpEmitter; xpTrail; тег xpCollider
- Задача: закручивающиеся, собирающиеся в капли сгустки частиц с чёткими краями и тонкими усиками — как клетки под микроскопом.

## Исходная сцена
- Чашка: цилиндр без верхней крышки, тег **xpCollider**, Normals **Inside**, Friction **41 %**; чёрный материал.
- xpEmitter Circle, радиус **50 cm**; эмиссия **Shot Hexagonal**, shot time 1, full lifespan, speed 0, radius **1 cm**.

## Шаги
1. **nxGravity** (по умолчанию) укладывает сетку частиц на дно.
2. **nxTurbulence** Simplex, Strength **50**, Scale ~**70**, частота пониже (позже силу сильно подняли). [▶ 1:02](https://youtu.be/Z_JR2deKwqE?t=62)
3. **nxFluids** солвер **PBD** → частицы взаимодействуют. **External Pressure 100 %** → более плотные границы сгустков и длинные тонкие усики при разделении. [▶ 2:18](https://youtu.be/Z_JR2deKwqE?t=138)
4. У PBD нет surface tension → слой **nxConstraints ▸ Surface Tension**, поднять Iterations и Tension → капельки-глобулы. [▶ 2:45](https://youtu.be/Z_JR2deKwqE?t=165)
5. **nxColor ▸ Gradient by Parameter: Speed**, градиент из пресета, max speed ~**9 cm** (15 было слишком много для таких медленных частиц). [▶ 3:20](https://youtu.be/Z_JR2deKwqE?t=200)
6. Пропускаем этап оседания: на удачном кадре в эмиттере ▸ **Initial State ▸ Use Initial State + Set State**, затем режим Emission **Controlled Only**, чтобы загружалось только сохранённое состояние. [▶ 3:58](https://youtu.be/Z_JR2deKwqE?t=238)
7. Вьюпорт: оставить отображение **Squares**, но поднять **Display Size Factor** (дешевле, чем Circles). [▶ 4:48](https://youtu.be/Z_JR2deKwqE?t=288)
8. По желанию — кластеризация: слой **nxConstraints ▸ Forces**, attraction 0, repulsion с меньшим радиусом / большей силой → отдельные группы клеток. [▶ 6:14](https://youtu.be/Z_JR2deKwqE?t=374)
9. Бонус-лук: скрыть чашку и частицы, **xpTrail** (не трейлы на всю сцену), длина ~20–50 кадров → плавные закрученные линии потока. [▶ 5:32](https://youtu.be/Z_JR2deKwqE?t=332)

## Как сейчас (новые инструменты)
2026.1 beta: Initial State в nxEmitter (+ Keep Stored Age); **nxBioLogic** (particle life, Physarum) — альтернатива для живых/клеточных паттернов; в Beta 2 изменились силы PBD, так что старые значения нужно перенастроить.
