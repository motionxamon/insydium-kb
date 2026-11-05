# Самопрорастающие усики по полю (nxQuestion Variable + Spawn + Set Age/Life, nxPush по радиусу)

- Источник: Top Tip Tuesday — Spawning Particle Tendrils — https://www.youtube.com/watch?v=LB-aA-N-2b0 (2024-08-27)
- Хост / поколение: C4D; NeXus G2 (**nxQuestion**, nxPush) на xpEmitters; C4D Spherical Field; xpCollider на сфере-источнике
- Задача: там, где поле проходит по покрытой частицами сфере, на заданное время прорастают непересекающиеся усики.

## Шаги
1. Родительские частицы эмитятся с примитива-сферы (на сфере тег xpCollider).
2. Слой **nxQuestion ▸ Variable**: Integer, Writable, Particle variable, имя **spawn**, значение 0.
3. Вкладка Field у nxQuestion: добавьте **Spherical Field**, разместите/отмасштабируйте его на части сферы.
4. Question (под переменной): Particle ▸ **Field > 0** → Action **Set Variable** spawn = 1.
5. Второй Question: **Math ▸ Variable** «spawn» **= 1** → проверьте через Set Color (жёлтый), затем замените на action **Spawn**: 1 частица, в пределах ~**0.3 cm**, новый spawn-emitter (размещён выше), Inherit выкл., полный lifespan, скорость 0, радиус **3**.
6. **nxPush** ставим **ниже** nxQuestion (порядок меняет лук), режим Distance **Particle Radius**, Strength **100 %** → нет начального разлёта, усики вытягиваются.
7. Убираем отставших: question **Neighbor Search** — меньше **2** соседей в пределах **5 cm** → **Set Speed 0**.
8. Ограничиваем рост каждого усика: в question spawn = 1 после Spawn добавьте **Set Age 0 (once)** и **Set Life 90 (once)** для родителя — умирают через 90 F только сработавшие родители, остальные остаются доступными для новых усиков.

## Подводные камни
- Не задавайте родительскому emitter lifespan 90 F — тогда умрут все родители и новые усики не смогут начаться.

## Как сейчас (новые инструменты)
**nxSpawn** в 2026.1 Beta 3 (On Age / Rate и т. д.) может заменить action Spawn; **nxDendrite** покрывает ветвящийся рост; nxFalloff заменяет поле C4D.
