# Пересимуляция огня в высоком разрешении из заспавненных частиц-топлива (xpSpawn на заражённых группах, cache Include, более мелкие воксели xpExplosiaFX)

- Источник: Maintenance Training - XP Countdown - Series 3 — xpExplosiaFX High Detail — https://www.youtube.com/watch?v=xoJcz9u3c8g (2023-03-29)
- Хост / поколение: C4D; CPU X-Particles (xpClothFX tearing, xpInfectio, xpPhysical, xpSpawn, xpExplosiaFX, xpCache); превью в Cycles 4D
- Задача: оставить существующую низкодетальную симуляцию xpExplosiaFX (она адвектирует рвущуюся ткань), но рендерить гораздо более детальный огонь из множества мелких частиц-топлива.

## Исходная сцена
Предыдущая сцена "Countdown 5 Burn": эмиттер ткани xpClothFX; xpInfectio распространяет группы infected/incubated вверх по ткани; xpPhysical даёт этим группам топливо; закэшированный xpExplosiaFX адвектирует ткань. Сохраните как новую версию "HQ" + папку для кэша.

## Шаги
1. Отключите тег кэша у эмиттера ткани. **xpSpawn** (Generate) ▸ Add spawning emitter → "Emitter Spawn"; позиция = **Source Particle**, скорость **Absolute** при скорости эмиттера **0** (их двигает только адвекция). [▶ 3:28](https://youtu.be/xoJcz9u3c8g?t=208)
2. Emitter Spawn ▸ вкладка Modifiers: **исключите xpInfectio** (иначе он поломает схему заражения). [▶ 4:07](https://youtu.be/xoJcz9u3c8g?t=247)
3. **xpPhysical** ▸ Groups Affected: удалите записи infected/incubated, чтобы топливо получали и заспавненные частицы. [▶ 4:49](https://youtu.be/xoJcz9u3c8g?t=289)
4. xpSpawn: **10 на кадр** (300/с по умолчанию — слишком много), **Spawn Once Only**, life Absolute → жизнь эмиттера **15 F, вариация 5**; **Groups Affected** = incubated + infected (спавн только там, где идёт горение). **Offset 2–3 см**, чтобы 10 частиц не сидели друг на друге. **Radius 1.5** у заспавненных. [▶ 6:29](https://youtu.be/xoJcz9u3c8g?t=389)
5. Ускорение: скройте ткань и выключите модификатор ткани — закэшированная адвекция всё равно двигает спавн точно так же. [▶ 7:54](https://youtu.be/xoJcz9u3c8g?t=474)
6. Новый **xpCache**, Inclusion **Include** = только Emitter Spawn; путь в HQ-папку кэша; Build (быстро). [▶ 10:19](https://youtu.be/xoJcz9u3c8g?t=619)
7. Новая сцена: скопируйте Emitter Spawn с его тегом кэша (**Copy Tag Data**), объект кэша и xpExplosiaFX (правильный размер домена); удалите старый тег кэша xpExplosiaFX. [▶ 12:51](https://youtu.be/xoJcz9u3c8g?t=771)
8. xpExplosiaFX: **Voxel Size 1** (мельче), **Advection выкл.** Повесьте на Emitter Spawn тег **xpExplosiaFX Source** — закэшированное топливо сразу загорается; спрячьте частицы. [▶ 13:44](https://youtu.be/xoJcz9u3c8g?t=824)
9. Сверьте с тканью (вставьте её кэш с Copy Tag Data); лишние куски ткани потом маскируются через PolyFX. [▶ 15:49](https://youtu.be/xoJcz9u3c8g?t=949)
10. Объёмный материал Cycles 4D (стандартный xpExplosiaFX fire/smoke) на xpExplosiaFX, real-time preview. [▶ 17:29](https://youtu.be/xoJcz9u3c8g?t=1049)
11. Кэш xpExplosiaFX: тот же объект кэша, Inclusion = только xpExplosiaFX; у тега кэша спавна override **Hold**; таймлайн 150 F (в демо остановлено на 120). ~20 мин, ~20 GB. [▶ 19:44](https://youtu.be/xoJcz9u3c8g?t=1184)
12. Импортируйте этот кэш в сцену для рендера вместо симуляции для адвекции. [▶ 22:02](https://youtu.be/xoJcz9u3c8g?t=1322)

## Подводные камни
- xpInfectio остаётся активным для исходных частиц, но исключён для спавна; топливо спавн получает от xpPhysical, когда с него снят фильтр по группам.
- Без Offset у спавна отображение точками выглядит редким, потому что частицы накладываются на исходную.

## Как сейчас (новые инструменты)
**nxExplosiaFX** (Fused 2025.4) пересимулирует на GPU из закэшированных частиц-топлива; **nxSpawn** (бета 2026.1 Beta 3: On Death / At Age, Rate/Burst) заменяет xpSpawn, **nxInfectio** — для распространяющихся групп; ткань по-прежнему на CPU xpClothFX (GPU-ткань пока только анонсирована). В C4D 2025.3+ Pyro link из 2026.1 умеет обмениваться дымом/огнём с nxExplosiaFX.
