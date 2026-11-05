# Замена дыма на детальную симуляцию, финальный тайминг и настройка рендера Cycles 4D (xpExplosiaFX, xpCache Offset, Cycles 4D)

- Источник: Maintenance Training — XP Countdown - Series 3 - Combining Scenes part 2 — https://www.youtube.com/watch?v=teKbNFK3H0E (2023-03-29)
- Хост / поколение: C4D; CPU xpExplosiaFX + xpCache; рендер Cycles 4D (CUDA)
- Задача: заменить дым/огонь горения на high-quality пересим, поправить тайминг шотов, настроить volume shader и отрендерить beauty + emission pass.

## Шаги
1. Подвох с видимостью: если у детей точки выставлены в зелёный, они перебивают выключенную ключом видимость родительского null → **Ctrl+Alt-клик** возвращает точки в серый, и они наследуют родителя.
2. Из HQ-файла горения скопировать только объект **xpExplosiaFX** + его **xpCache** (Copy Tag Data включён), вставить в новый null «5 burn HQ».
3. Подогнать под старый кэш: Playback **Hold**, **Offset −50**. HQ-кэш ≈576 MB, поэтому скраб медленный.
4. **Hardware OpenGL** render 0–130 — проверить, что *цифры* читаются достаточно долго. Вывод: держать 5 примерно на 15 F дольше → у обоих кэшей Offset **−65**.
5. Сдвинуть ключи Linear field (растворение PolyFX) на те же 15 F в **Timeline F-Curve**: выделить все, тащить с **Shift** по горизонтали (F50 → F65). Подправить Y-кривую, чтобы полигоны не распадались раньше, чем до них дойдёт огонь.
6. Node tree пресета Cycles 4D **ExplosiaFX fire & smoke**: Point Density (плотность дыма) → Math Multiply → Volume Scatter / Volume Absorption → Add; Point Density (burn) → Color Ramp → Multiply → **Emission** (Blackbody) → Add → Volume.
7. Дым тоньше: оба multiply делятся на 5 (scatter **100 → 20**, absorption **13 → 2.6**). Яркость огня — temperature/strength у emission, оставили **60**; если отключить Blackbody, огонь берёт плоский цвет (например, зелёный).
8. Растворение дыма после появления 4: поставить ключи на оба multiply, а чуть позже — ключи в **0** (к ~F160 дыма нет).
9. Samples: real-time preview на 10; **25 = 625** path-tracing samples, **22 = 484** (использовали; немного шумно, для продакшена лучше 25). Шум проверять на нескольких кадрах в полном разрешении, а не только в превью.
10. Render settings ▸ Cycles 4D: Device **CUDA**; indirect clamping оставить; уменьшить **Volume Step Size**, если в дыме видны полосы-срезы (рендер медленнее); Film **Transparent Glass** включить; Render Elements ▸ **Emission** (светится только огонь).
11. Output 720p, **30 fps** (как в Ctrl+D project), кадры 0–160. Save: **OpenEXR 16-bit**, Alpha включён. **Multi-Pass** включён, тот же путь, EXR, **Multi-Layer File** выключен, **Layer Name as Suffix** включён, и в списке multipass нужно включить **Post Effects**, иначе pass от Cycles не сохранится.
12. Сохранить отдельную сцену «v13 render settings»; рендер занял ~3 ч.

## Подводные камни
- Если навигировать с зажатыми 1/2/3, когда поле параметра выделено, его значение меняется.
- HQ-сим заспавнен из позиций существующей ткани, поэтому огонь больше не задерживается на появившейся 4 — такое взаимодействие сохраняется, только если с самого начала симулировать всё в большем разрешении.

## Как сейчас (новые инструменты)
**nxExplosiaFX** (GPU, Fused 2025.4) с volumetric GPU viewport — сдвиг по времени через **nxCache**; в 2026.1 beta в C4D есть дефолтный **Redshift smoke material** для nxExplosiaFX VDB и **Pyro link** (C4D 2025.3+); **nxWarp** может деформировать дым.
