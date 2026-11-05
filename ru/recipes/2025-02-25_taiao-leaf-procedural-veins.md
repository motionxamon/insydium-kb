# Процедурный лист со слоями прожилок (Taiao Leaf: Midvein, Lateral veins pinnate/dichotomous)

- Источник: Top Tip Tuesday — Taiao Leaf Veins — https://www.youtube.com/watch?v=eRnivIKK52M (2025-02-25)
- Хост / поколение: C4D; объект Taiao Leaf (система жилкования); материалы standard / Redshift / Octane; без частиц
- Задача: лист нужной формы, закрученный, с реалистичными прикреплёнными прожилками и отдельными материалами.

## Шаги
1. Leaf ▸ Geometry: сегменты **6 по ширине / 10 по длине**, 1 subdivision; включите форму **profile** и стяните основание и кончик в точки; добавьте **Edge Noise**. [▶ 0:27](https://youtu.be/eRnivIKK52M?t=27)
2. Модификаторы листа: **Fold**, **Furl** у основания, второй Furl в другую сторону → S-образный изгиб. [▶ 0:50](https://youtu.be/eRnivIKK52M?t=50)
3. Вкладка Main: переключите Geometry → **Veins** (вид со слоями-нодами). Добавьте **Midvein**; profile-сплайн сужает её к кончику; **Petiole offset** вытягивает черешок. [▶ 1:19](https://youtu.be/eRnivIKK52M?t=79)
4. Модификаторы Midvein: **Furl Petiole** (закрутить черешок, подстроить bias) + **Turbulence** (малая сила) для неровности. [▶ 2:21](https://youtu.be/eRnivIKK52M?t=141)
5. С выделенной midvein добавьте слой **Lateral Vein**. Структуры: Reticulate, **Pinnate** (по умолчанию), Palmate, Dichotomous. Настройте Angle, закрутку/bias угла к кончику, смещение, вариацию угла. [▶ 3:20](https://youtu.be/eRnivIKK52M?t=200)
6. У lateral-слоя свои модификаторы: Turbulence; через его profile опустите прожилки к краю. [▶ 4:42](https://youtu.be/eRnivIKK52M?t=282)
7. Вкладка Materials: материалы листа, midvein и прожилок назначаются по частям (любой рендер-движок). [▶ 4:13](https://youtu.be/eRnivIKK52M?t=253)
8. **Dichotomous**: повторяющиеся разветвления (уровни, число разделений) → веерные прожилки; сделайте их шире; Main ▸ **Remove Intersections** обрывает прожилки там, где они встречаются. [▶ 5:40](https://youtu.be/eRnivIKK52M?t=340)

## Подводные камни
Прожилки остаются прикреплёнными через все модификаторы листа (fold/furl/turbulence) — сначала форма, потом прожилки.
