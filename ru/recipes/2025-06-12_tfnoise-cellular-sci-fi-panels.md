# Ландшафт из sci-fi панелей / города (TerraformFX tfNoise Advanced, Cellular + Manhattan)

- Источник: Bite-Sized — Sci-Fi Panels — https://www.youtube.com/watch?v=IsjrmNr63A4 (2025-06-12)
- Хост / поколение: C4D; TerraformFX (tfTerrain + оператор tfNoise, режим noise Advanced)
- Задача: блочные, угловатые паттерны высот, которые читаются как панели обшивки корабля или сетка города.

## Шаги
1. Меню INSYDIUM ▸ **tfTerrain**; удалите операторы и материал по умолчанию. [▶ 0:16](https://youtu.be/IsjrmNr63A4?t=16)
2. Add Operator ▸ **tfNoise** — по умолчанию он в новом режиме **Advanced** (noise от Maxon тоже доступны). [▶ 0:32](https://youtu.be/IsjrmNr63A4?t=32)
3. Тип noise **Simplex → Cellular**; Distance function **Euclidean → Manhattan**. [▶ 1:00](https://youtu.be/IsjrmNr63A4?t=60)
4. Понизьте **Octaves**, понизьте **Lacunarity** (крупнее детали), подстройте **Persistence**; **Scale 250**. [▶ 1:18](https://youtu.be/IsjrmNr63A4?t=78)
5. **Jitter 0** = квадратные блоки; поднимите Persistence для разной высоты, Lacunarity — для вложенной детализации. [▶ 1:43](https://youtu.be/IsjrmNr63A4?t=103)
6. Поднимите Jitter для угловатых, неровных панелей; **Gain** сдвигает смещение по высоте; больше Octaves = больше деталей. [▶ 2:09](https://youtu.be/IsjrmNr63A4?t=129)
