# Три поколения спавна из одного эмиттера (уровни xpMultiSpawn + группы для отображения)

- Источник: Top Tip Tuesday — xpMultiSpawn — https://www.youtube.com/watch?v=XwQyDoAPNa4 (2023-03-21)
- Хост / поколение: C4D; CPU X-Particles (xpEmitter, xpMultiSpawn, xpTurbulence, группы)
- Задача: стрелки разлетаются на квадраты, а те — на короткоживущие точки: взрывающиеся/распадающиеся потоки.

## Исходная сцена
xpEmitter с частицами в отображении **Arrow** и модификатором турбулентности.

## Шаги
1. Modifiers ▸ Generate ▸ **xpMultiSpawn** (в отличие от xpSpawn ему не нужен отдельный эмиттер для спавна). Уровень по умолчанию: 10 новых на каждую исходную частицу в возрасте 0, в течение одного кадра. [▶ 0:39](https://youtu.be/XwQyDoAPNa4?t=39)
2. **Level 1**: при возрасте исходной частицы **50**, количество **5**; направление **Random Spherical → Relative to Source Particle** + немного spread (читается как наследование движения); **Kill Source Particle**. [▶ 2:57](https://youtu.be/XwQyDoAPNa4?t=177)
3. Группы: эмиттер ▸ вкладка Groups, Ctrl+Alt-клик по кнопке добавления → **3 группы**; режим эмиттера **First Group Only** (исходные → группа 1). [▶ 3:34](https://youtu.be/XwQyDoAPNa4?t=214)
4. **Level 2**: возраст **30**, количество **5**, Relative + большой spread, kill source, новые частицы → **группа 2** (отображение группы: **Squares**). [▶ 3:51](https://youtu.be/XwQyDoAPNa4?t=231)
5. **Level 3**: возраст **20**, количество **100**, kill source, время жизни **20 F** (вариация ~5), Relative + большой spread, → **группа 3** (отображение: **Dots**). [▶ 5:00](https://youtu.be/XwQyDoAPNa4?t=300)

## Подводные камни
Если группа не назначена, заспавненные частицы сохраняют отображение эмиттера (стрелки).

## Как сейчас (новые инструменты)
**nxSpawn** (2026.1 Beta 3: Instant / At Age / On Collision / On Death, 8 подслоёв); в стабильном Fused — действие Spawn в nxQuestion.
