# Распад / проявление текста (nxQuestion field → смена группы → сброс возраста → задать lifespan)

- Источник: Top Tip Tuesday — Particle Reveal — https://www.youtube.com/watch?v=bnaV15UoBRI (2024-12-17)
- Хост / поколение: NeXus (nxExplode, nxTurbulence, nxQuestion, группы, spherical field)
- Задача: частицы осыпаются с текста по мере прохождения растущего поля; cache, проигранный задом наперёд, даёт проявление.

## Шаги
1. Emitter **Shot** по поверхности текста (текст скрыт). [▶ 0:21](https://youtu.be/bnaV15UoBRI?t=21)
2. **nxExplode** от **позиции модификатора** (не от центра масс), скорость 150 ± 100, **Speed at Start Only выкл.** (продолжает толкать). [▶ 1:10](https://youtu.be/bnaV15UoBRI?t=70)
3. **nxTurbulence** под ним: шум Boron, strength 25, больше octaves, **persistence ниже** (сохраняет крупные завихрения + мелкие детали). [▶ 1:45](https://youtu.be/bnaV15UoBRI?t=105)
4. Groups у emitter: создайте 2 группы, режим **First Group Only** → все рождаются в группе 1. У обоих модификаторов ▸ Groups Affected = **group 2**. [▶ 2:19](https://youtu.be/bnaV15UoBRI?t=139)
5. **nxQuestion**: `Field (spherical) → Set Group 2` → затем **Set Age 0** (once) → **Set Lifespan 85**. [▶ 4:41](https://youtu.be/bnaV15UoBRI?t=281)
6. Анимируйте размер поля от 0 до охвата всего текста (кадры ~41 → 152). [▶ 4:06](https://youtu.be/bnaV15UoBRI?t=246)
7. Закэшируйте, затем проиграйте в обратную сторону — получится формирующееся проявление. Смените текст → новый эффект (полностью процедурно). [▶ 5:30](https://youtu.be/bnaV15UoBRI?t=330)

## Как сейчас (новые инструменты)
Falloffs из беты 2026.1 (16 режимов) на модификаторах в простых случаях могут заменить связку поле + смена группы.
