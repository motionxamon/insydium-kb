# xpOcean — карточка инструмента

Встречается в **3** рецептах · 2023-04-20 → 2025-04-08 · хосты: C4D

_Собрано автоматически из рецептов: строки взяты из рецептов по видео (сначала новые). Значения — стартовые точки из речи в видео._

## Настройки и значения из видео
- **xpOcean** ▸ режим **Deformer** (не Primitive), дочерним к плоскости. [▶ 0:40](https://youtu.be/r_AyI7Bgi0U?t=40) — *[2025-04-08](../../recipes/2025-04-08_custom-object-ocean.md)*
- Зацикливание: xpOcean ▸ **Looping on**, Loop Time = последний кадр + 1 (**201** для сцены на 200 кадров). [▶ 5:38](https://youtu.be/r_AyI7Bgi0U?t=338) — *[2025-04-08](../../recipes/2025-04-08_custom-object-ocean.md)*
- X-Particles ▸ Generators ▸ **xpOcean**. Width / Height segments по **200** для детализации. [▶ 0:47](https://youtu.be/xQFbyD2fMNo?t=47) — *[2023-06-27](../../recipes/2023-06-27_xpocean-looping-deformer-layer.md)*
- **xpOcean** (Generators): снизить Wave Height и Time Scale, поднять **Wind Speed** для более длинной зыби, добавлять **Choppiness**, пока гребни не начнут заворачиваться. Материал для вьюпорта: без reflectance, шейдер **Fresnel** в Color, от глубокого синего к сероватому белому. [▶ 9:11](https://youtu.be/VuevOvpbvJY?t=551) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- Переключить xpOcean **Type: Primitive → Deformer** (работает как любой деформер C4D — дочерним объектом или соседом). [▶ 10:28](https://youtu.be/VuevOvpbvJY?t=628) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- **xpOpenVDBMesher**, source = base-эмиттер, **Point Radius 5**. Поставить xpOcean соседом мешера в папке Generators → живой меш деформируется. Перенести материал на мешер. [▶ 12:11](https://youtu.be/VuevOvpbvJY?t=731) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- Частицы тоже катятся по волнам: добавить деформер xpOcean в список **Modifiers** каждого цветного эмиттера (галочка = включён). [▶ 11:28](https://youtu.be/VuevOvpbvJY?t=688) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- После кэширования: **снять галочку xpOcean в Modifiers эмиттеров** (иначе кэшированные частицы деформируются дважды). [▶ 16:33](https://youtu.be/VuevOvpbvJY?t=993) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*
- VDB-меш исчезает при скрабе: положить мешер внутрь **xpJoin** (Utilities), xpOcean — его сосед. Опустить Join на **Y −7 cm**, чтобы частицы лежали на поверхности. [▶ 17:37](https://youtu.be/VuevOvpbvJY?t=1057) — *[2023-04-20](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)*

## Все рецепты (3)
- 2025-04-08 · [Анимированная поверхность океана внутри любого объекта (xpOcean Deformer + Boole Intersect, с зацикливанием)](../../recipes/2025-04-08_custom-object-ocean.md)
- 2023-06-27 · [Большой зацикленный океан без заметного тайлинга (xpOcean Looping + второй xpOcean как Deformer)](../../recipes/2023-06-27_xpocean-looping-deformer-layer.md)
- 2023-04-20 · [Цвет по скорости и подложка жидкости, деформированная океаном (Gradient Parameter по Speed, xpOpenVDBMesher, xpOcean Deformer, xpJoin)](../../recipes/2023-04-20_tension-fluids-speed-gradient-xpocean-deformer.md)
