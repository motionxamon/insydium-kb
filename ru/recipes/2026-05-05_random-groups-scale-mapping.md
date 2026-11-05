# Немного крупных, много мелких: случайные подгруппы + nxScale с маппингом по группе

- Источник: Top Tip Tuesday — Random Data Control — https://www.youtube.com/watch?v=5OHld9QtCzI (2026-05-05)
- Хост / поколение: NeXus (nxQuestion Random, nxScale Range + Mapping, nxKill FOV) — C4D и Blender
- Задача: один эмиттер, один модификатор масштаба, но управляемое распределение: в основном мелкие частицы, немного средних и совсем чуть-чуть огромных.

## Шаги
1. Radius эмиттера 0 (Display: Spheres, чтобы видеть реальный размер). **Вкладка Groups**: создай 3 группы, режим **First Group Only**.
2. **nxQuestion**:
   - `If Math ▸ Random (Time Variation: None, 0–10000) < 100` → Set Color жёлтый + **Set Group 2**
   - копия: `Random within 2000–2020` → Set Color розовый + **Set Group 3** (ещё реже)
   - меняй **Seed** у Random, чтобы перетасовать, кто выбран.
3. Слой **nxScale** Range: radius 0 → End 60 cm с большой вариацией.
4. **Mapping**: добавь карту **Group** → Map Layer: Range, параметр **Radius End**, Range Min 1 / Max 3; пресет сплайна **Linear**; точки на X 0 (группа 1), 0.5 (группа 2), 1 (группа 3) с Y ≈ низко / 0.5 / 1 → группа 1 крошечная, группа 2 ~30 cm, группа 3 до 60 cm, и все по-прежнему с разбросом.
5. Пропорции подстраивай порогами random. nxKill Outside Camera FOV держит сцену лёгкой.

## Вывод
Math ▸ Random с **Time Variation None** = фиксированное случайное число на каждую частицу — самый чистый способ выбрать процент облака частиц. Так же можно мапить по группам и другие параметры (Variation, End Time).
