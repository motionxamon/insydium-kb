# Огонь испускают только быстрые (или крупные) частицы — маппинг источника EFX

- Источник: Top Tip Tuesday — Particle Emission Map — https://www.youtube.com/watch?v=iPYPQGaz7zQ (2026-03-24)
- Хост / поколение: C4D, nxExplosiaFX (Mapping источника) + CPU xpGravity Newton (орбиты, масштаб по расстоянию)
- Задача: частицы, летающие по орбите вокруг сферы, оставляют огненный шлейф, только когда превышают порог скорости (или радиуса) — без ключей.

## Шаги
1. Частицы крутятся по орбите вокруг сферы с **xpGravity Type Newton** (сфера — аттрактор; её опция масштаба делает частицы крупнее рядом со сферой). [▶ 0:32](https://youtu.be/iPYPQGaz7zQ?t=32)
2. nxExplosiaFX: домен побольше → **Voxel 6**; Buoyancy **Gravity 0** (флюид остаётся на орбите). [▶ 4:14](https://youtu.be/iPYPQGaz7zQ?t=254)
3. Sources: эмиттер, **Temperature 0**, только Fuel (~42). Без тепла топливо не горит → Simulation ▸ Burning **Ignition Temperature 0**. [▶ 2:07](https://youtu.be/iPYPQGaz7zQ?t=127)
4. Отрицательная **Velocity** на источнике (флюид отбрасывается против направления частиц); **Motion Gap Fill 10** для быстрых частиц; поднимите **Burn Rate**, smoke production; поднимите **dissipation** дыма/тепла. [▶ 3:10](https://youtu.be/iPYPQGaz7zQ?t=190)
5. Вкладка **Mapping** в Sources: слой **Speed**, Source **X-Particles Emission Strength** (не Mesh Object!), цель **Fuel**. Диапазон 250–500 cm/s → медленные частицы ничего не испускают, быстрые дают полное топливо. Инвертируйте кривую (например, 200–300) → горят только замедляющиеся частицы. [▶ 5:37](https://youtu.be/iPYPQGaz7zQ?t=337)
6. Переключите слой на **Radius** (4–30 cm, от масштабирования гравитацией) → горят только крупные частицы рядом со сферой. [▶ 8:37](https://youtu.be/iPYPQGaz7zQ?t=517)

## Заметки
Любой канал (smoke, temperature, fuel, pressure) можно замаппить на любые данные частиц; сила эмиссии меша/сплайна, адвекция частиц и настройки горения тоже маппятся.
