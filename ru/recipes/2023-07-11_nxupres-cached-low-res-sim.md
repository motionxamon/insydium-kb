# Апрез закешированного сима с малым числом частиц в плотный (xpCache + nxUpres Velocity / Position / Push)

- Источник: Top Tip Tuesday — nxUpres — https://www.youtube.com/watch?v=RfvvtXkG8Y0 (2023-07-11)
- Хост / поколение: C4D; G2 NeXus (nxUpres, nxTurbulence — новинки Fused 2023.3) + CPU xpCache
- Задача: превратить редкий импульсный сим с турбулентностью в детализированный взрыв по скоростям, без модификаторов на high-res эмиттере.

## Исходная сцена
xpEmitter "base" в режиме **Ring**, **Pulse** каждые **60** кадров, **60** частиц за импульс; **nxTurbulence strength 15**.

## Шаги
1. **xpCache** ▸ кешируем во **internal memory** ▸ Build Cache. Турбулентность теперь можно удалить — движение читается из кеша.
2. Копируем эмиттер, переименовываем в "upres", удаляем его тег кеша; Display: зелёный, **Dots**. Эмиссия (по-прежнему Pulse/60) → **2,000** частиц за импульс.
3. NeXus ▸ **nxUpres**: Source = закешированный base-эмиттер, **Destination** = upres-эмиттер. С настройками по умолчанию зелёные частицы следуют за розовыми закешированными (скорость подмешивается).
4. Прячем base-эмиттер. На upres-эмиттере снимаем галку full lifespan → Life **70**, variation **20** → ровные импульсы.
5. Комкование: **Max Count** (сколько соседей из base смешивается на одну upres-частицу) по умолчанию **3** → **15**; максимум **64** (плавнее, но медленнее).
6. Передаваемые данные: velocity, radius, color, group, mass, **position**. Position вместо velocity стягивает частицы к родителям; включаем **Push**, чтобы раздвинуть их в рыхлые сгустки; меньше **Push Distance** → вид капель.
7. Для взрыва оставляем только **Velocity**, Push выключен.

## Как сейчас (новые инструменты)
nxUpres без изменений есть в NeXus 2026.x (C4D и Blender), источником служит **nxCache**; в 2026.1 у nxCache появились Disk Reserve/Alembic. См. "Upres granular sim" (2025-04-15) и "Upres explode position/velocity blend" (2025-05-27).
