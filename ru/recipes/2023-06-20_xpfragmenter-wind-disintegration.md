# Распад модели полигон за полигоном под управлением частиц (xpFragmenter Faces Polys, xpWind с linear field, xpTurbulence с маппингом на пройденную дистанцию)

- Источник: Top Tip Tuesday — xpFragmenter Destruction — https://www.youtube.com/watch?v=zA3IYXmyi5Q (2023-06-20)
- Хост / поколение: C4D; G1 CPU X-Particles (xpEmitter, xpFragmenter, xpWind, xpTurbulence, xpCollider)
- Задача: модель волка распадается по фейсам, пока по ней проходит фронт ветра, затем фейсы кувыркаются в турбулентности.

## Шаги
1. Новый **xpEmitter**, Shape **Object** = волк, эмиссия из **Polygon Center**, **One Particle per Source Element**; Emission **Shot**, Speed **0** → по одной частице на полигон. [▶ 0:49](https://youtu.be/zA3IYXmyi5Q?t=49)
2. Generators ▸ **xpFragmenter**, подключите эмиттер (волка положите дочерним просто для порядка). Режим **Faces (Polys)** = один объект с отдельными полигонами (Faces (Objects) создаёт отдельный объект на каждый полигон — тяжело). [▶ 1:42](https://youtu.be/zA3IYXmyi5Q?t=102)
3. Скройте исходного волка и частицы. Включите **Connect Polys** для гладкого шейдинга. [▶ 2:04](https://youtu.be/zA3IYXmyi5Q?t=124)
4. Скопируйте текстурный тег волка на xpFragmenter и отметьте **Remap Textures** (иначе текстура ляжет на каждый полигон отдельно). [▶ 2:24](https://youtu.be/zA3IYXmyi5Q?t=144)
5. **xpWind**, повёрнут на 90°, чтобы дул поперёк головы; strength снижен до **85 cm**.
6. Волк (скрытый) ▸ тег **xpCollider**: меньше отскока, немного трения → фейсы отскакивают от целой части модели.
7. **xpTurbulence**: Scale **30**, Strength **8**.
8. Turbulence ▸ **Mapping**: **Strength** турбулентности завязан на **Distance Travelled**, диапазон **0 → 30 cm**; сдвиньте начало кривой, чтобы первые несколько cm турбулентность не действовала (сначала их сдвигает ветер). [▶ 5:16](https://youtu.be/zA3IYXmyi5Q?t=316)
9. xpWind ▸ Fields: **Linear field**, направленное на **−Z**, с ключами по Z, чтобы проходило через сцену → ничего не движется, пока не дойдёт фронт. [▶ 5:53](https://youtu.be/zA3IYXmyi5Q?t=353)

## Как сейчас (новые инструменты)
Сегодняшний путь на GPU: двигайте частицы через **nxWind**, **nxTurbulence** (маппинг данных типа Distance во вкладке Mapping в NeXus) и анимированный **nxFalloff**; в NeXus 2026.1 — **nxDeformer** (меш следует за частицами, с разрывами) или **nxShatter** для разлёта крупными кусками. Для самого xpFragmenter nx-аналога нет, так что для распада по фейсам оставляйте его.
