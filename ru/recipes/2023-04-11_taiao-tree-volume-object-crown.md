# Дерево, растущее внутри объёма любого объекта (Taiao Tree: Volume Objects, точки притяжения, листья через multi-instance)

- Источник: Top Tip Tuesday — Taiao toTree — https://www.youtube.com/watch?v=G7vDdlvLIzM (2023-04-11)
- Хост / поколение: C4D; Taiao Tree (в духе space colonisation; без частиц); материалы C4D
- Задача: дерево, крона которого принимает форму модели или логотипа (в демо — резиновая уточка INSYDIUM).

## Шаги
1. INSYDIUM ▸ Taiao ▸ **Taiao Tree** (+ Growth Point = начало ствола). Ветки тянутся к **точкам притяжения** в объёме кроны, не пересекаясь. [▶ 0:31](https://youtu.be/G7vDdlvLIzM?t=31)
2. Display: включите показ точек притяжения + **Crown Mesh** (по умолчанию цилиндр), чтобы понять принцип. [▶ 0:48](https://youtu.be/G7vDdlvLIzM?t=48)
3. Вкладка Volume Points: точки притяжения **100 → 1000** (больше точек = больше веток). Форма кроны может браться из сплайна Tree Crown Profile, или… [▶ 1:08](https://youtu.be/G7vDdlvLIzM?t=68)
4. Generation Method → **Volume Objects**; перетащите туда модель и скройте её — теперь точки заполняют модель. Отключите отображение. [▶ 1:21](https://youtu.be/G7vDdlvLIzM?t=81)
5. Меш полегче: **Ring Segments 6**, **Resolution Length 5 → 10** (новый сегмент каждые 10 cm). [▶ 2:20](https://youtu.be/G7vDdlvLIzM?t=140)
6. Режим Organ (листья/плоды — это органы): Single Poly → **Multi-Instances**. Вкладка Leaves ▸ **Use Leaves**. [▶ 2:45](https://youtu.be/G7vDdlvLIzM?t=165)
7. Leaf Geometry: **Length segments 3**; сожмите сплайн **Leaf Profile** у основания и на кончике; Size **0.95**, вариация **20%**. [▶ 3:27](https://youtu.be/G7vDdlvLIzM?t=207)
8. Distribution ▸ сплайн **Position on Tree**: сдвиньте узел основания, чтобы листья не росли из ствола. [▶ 4:12](https://youtu.be/G7vDdlvLIzM?t=252)
9. Заполнение: точки притяжения **5000** (считается дольше). [▶ 4:29](https://youtu.be/G7vDdlvLIzM?t=269)
10. Вкладка Materials: кора → Trunk (+ назначить на дочерние стволу = ветки); Leaf 1 и Leaf 2 оба на Leaf → смесь светлого и тёмного. [▶ 5:00](https://youtu.be/G7vDdlvLIzM?t=300)
11. Object Properties: анимируйте **growth**, чтобы выращивать/убирать дерево и листья. [▶ 5:23](https://youtu.be/G7vDdlvLIzM?t=323)

## Как сейчас (новые инструменты)
Ветвление на частицах сегодня: **nxDendrite** (ветки/сеть) или nxBioLogic (2026.1 beta); сам Taiao получил анимацию роста и силы в Fused 2023.3.
