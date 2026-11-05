# Эмиссия из анимированных живых выделений (MeshTools Select + noise shader → xpEmitter + nxFollowGeo режим Edge)

- Источник: Top Tip Tuesday — Custom Particle Emission — https://www.youtube.com/watch?v=AmfN_ZlpBcE (2025-01-28)
- Хост / поколение: C4D; MeshTools (объект Select) + xpEmitter с NeXus G2 nxFollowGeo / turbulence; сферическое поле C4D
- Задача: частицы рождаются только из шумных, ползущих по модели пятен полигонов/рёбер, проявляемых полем.

## Исходная сцена
xpEmitter на голове волка + **nxFollowGeo** (режим Edge = ползание по сетке) + turbulence.

## Шаги
1. INSYDIUM ▸ MeshTools ▸ **Select**; сделайте модель его дочерним объектом. По умолчанию создаётся полигональное выделение всего (видно через Display ▸ Polygon Selection). [▶ 1:22](https://youtu.be/AmfN_ZlpBcE?t=82)
2. В объекте Select используйте **Noise shader**, поднимите Tolerance → остаются только разбросанные полигоны; noise Animation Speed **0.4** → живое анимированное выделение. [▶ 1:47](https://youtu.be/AmfN_ZlpBcE?t=107)
3. xpEmitter ▸ Object: источник = **объект Select** (не модель), Polygons, перетащите полигональное выделение; nxFollowGeo тоже использует объект Select. [▶ 1:41](https://youtu.be/AmfN_ZlpBcE?t=101)
4. Эмиссия: на всех кадрах с более коротким lifespan → непрерывное рождение из движущихся пятен. [▶ 2:42](https://youtu.be/AmfN_ZlpBcE?t=162)
5. Вариант с рёбрами: nxFollowGeo **Edge mode, Edge 100%, offset 2 cm**; в Select отключите polygon, включите **Edge selection**; эмиттер — emit from **Edges** с выделением рёбер. [▶ 3:23](https://youtu.be/AmfN_ZlpBcE?t=203)
6. Select ▸ вкладка **Fields**: добавьте сферическое поле → выделения (и рождения) только там, где поле; анимируйте его для проявления. [▶ 4:34](https://youtu.be/AmfN_ZlpBcE?t=274)

## Как сейчас (новые инструменты)
В Fused 2025.4 nxFollowGeo получил несколько сплайнов + режимы Guide/Force; в бете 2026.1 режимы nxFalloff и falloff на каждом слое позволяют ограничивать эффекты без полей C4D.
