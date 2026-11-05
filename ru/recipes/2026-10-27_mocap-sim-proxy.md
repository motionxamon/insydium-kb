# Живой лоупольный прокси для симуляции на мокап-персонаже (огонь / коллизии)

- Источник: Top Tip Tuesday — Mocap Sim Proxy — https://www.youtube.com/watch?v=C0P7UtWroDo (2026-10-27)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX, GPU) + инструменты Character в C4D; xpOpenVDBMesher (CPU) для прокси
- Задача: горящий персонаж, у которого источник дыма/огня и коллайдер — лёгкий прокси со скином, который остаётся рабочим при смене мокап-клипа.

## Дерево сцены
```
nxExplosiaFX domain
  Sources: Remesh (proxy)      Colliders: Remesh (proxy)   ← hierarchy options off
Walking/Stumbling Loop null (mocap asset, animated in Z)
  ├─ mocap joints (Character Definition tag)
  └─ Male Puppet (Maxon asset browser ▸ Motion Capture ▸ Model)
       ├─ Character Solver tag  (Source Character = mocap Character Definition)
       ├─ Mocap Rig Target null → joints
       ├─ high-poly mesh parts (render)
       └─ Remesh (low poly proxy) + Weight tag + Skin  (bound to the same joints)
```

## Шаги
1. Добавьте куклу из Maxon Motion Capture + мокап-клип. Перетащите тег **Character Definition** клипа в тег **Character Solver** куклы → Source Character. Положите куклу под анимированный null клипа, чтобы она тоже перемещалась.
2. Проблема: детализированное тело в роли источника EFX и коллайдера — очень медленно. Правило: **источники и коллайдеры должны быть лоупольными прокси**, а рендерится хайполи.
3. Делаем прокси: переключите Character Solver в **Reference Pose** (T-поза) и временно отвяжите клип. Ctrl-drag копию частей меша.
4. **xpOpenVDBMesher** с копией в качестве дочернего → voxel size ~3 для замкнутой оболочки; поднимите **Iso value**, чтобы тонкие части (кисти) не пропали. Сделайте редактируемым (C).
5. Положите под объект Maxon **Remesh** (Symmetry X, умеренный размер полигонов) → сделайте редактируемым → чистая лоупольная оболочка в той же позе.
6. Привязка: выделите иерархию джойнтов (первый джойнт → правый клик **Select Children**), с Ctrl выделите ремешнутый прокси → **Character ▸ Bind** → Weight tag + деформер Skin.
7. Положите прокси под null куклы, снова привяжите клип в Character Solver, верните под null клипа. Теперь прокси и хайполи следуют любому клипу (в видео — замена на походку зомби).
8. nxExplosiaFX: замените хайполи в **Sources** и **Colliders** на прокси; отключите hierarchy options → симуляция и кэширование намного быстрее.

## Заметки
- Та же техника работает для коллизий частиц и флюидов (статичных или анимированных).
- Новая альтернатива: nxMesher тоже умеет делать оболочку из испущенных частиц, но для персонажей со скином прокси VDB-mesh → Remesh → Bind остаётся самым чистым вариантом.
