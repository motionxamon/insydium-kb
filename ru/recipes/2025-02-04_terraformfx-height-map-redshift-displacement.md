# Рельеф брусчатки → экспорт карты высот → displacement в Redshift при рендере (оператор noise TerraformFX + Redshift Displacement)

- Источник: Top Tip Tuesday — Custom Displacement Maps — https://www.youtube.com/watch?v=ZEh3icEFM_g (2025-02-04)
- Хост / поколение: C4D; TerraformFX (terrain + оператор Noise) + Redshift; без частиц
- Задача: детализированная плоскость брусчатки без тяжёлой геометрии, с displacement, точно совпадающим с рельефом.

## Шаги
1. Terrain TerraformFX + **оператор Noise**; пока задаёте форму, фрактальную детализацию выключите.
2. Тип noise **Simplex → Cellular**, поднимите **Jitter** (ячейки Voronoi); тип возврата **Cell → Distance Sub** — для скошенных краёв вместо плоских обрывов.
3. Warp ▸ поднимите fractal warping для неровных камней.
4. Трюк с инструментом Scale: в режиме Model масштабируется высота; **в режиме Object масштабируется сам noise**. Поставьте у оператора **Gain ровно 25** и запомните.
5. Объект terrain: разрешение **4000 × 4000** (= размер карты). Вкладка Preview ▸ карта **Altitude** ▸ **Write File**.
6. Отключите terrain; используйте очень низкополигональную плоскость (всего ~10 сегментов).
7. Материал Redshift: нода **Texture** (загрузите карту высот) → нода **Displacement** → Output Displacement; поднимите roughness.
8. Плоскость ▸ **Redshift Object tag ▸ Geometry**: Override, Enable Tessellation, Smooth Subdivision выключить, **Displacement включить**.
9. Тег ▸ Displacement: **Max Displacement = Displacement Scale = 25** (как gain) → точное совпадение с рельефом.

## Подводные камни
Совпадение работает, только если масштаб в Redshift равен gain оператора — держите это число круглым.
