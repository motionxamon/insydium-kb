# Ландшафт из sci-fi панелей / города (TerraformFX tfNoise Advanced, Cellular + Manhattan)

- Источник: Bite-Sized — Sci-Fi Panels — https://www.youtube.com/watch?v=IsjrmNr63A4 (2025-06-12)
- Хост / поколение: C4D; TerraformFX (tfTerrain + оператор tfNoise, режим noise Advanced)
- Задача: блочные, угловатые паттерны высот, которые читаются как панели обшивки корабля или сетка города.

## Шаги
1. Меню INSYDIUM ▸ **tfTerrain**; удалите операторы и материал по умолчанию.
2. Add Operator ▸ **tfNoise** — по умолчанию он в новом режиме **Advanced** (noise от Maxon тоже доступны).
3. Тип noise **Simplex → Cellular**; Distance function **Euclidean → Manhattan**.
4. Понизьте **Octaves**, понизьте **Lacunarity** (крупнее детали), подстройте **Persistence**; **Scale 250**.
5. **Jitter 0** = квадратные блоки; поднимите Persistence для разной высоты, Lacunarity — для вложенной детализации.
6. Поднимите Jitter для угловатых, неровных панелей; **Gain** сдвигает смещение по высоте; больше Octaves = больше деталей.
