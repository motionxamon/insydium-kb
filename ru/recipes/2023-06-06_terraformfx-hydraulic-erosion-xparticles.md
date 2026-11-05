# Реалистичные горы с эрозией от дождя из частиц (слои tfNoise + tfErosion Hydraulic в режиме X-Particles)

- Источник: Top Tip Tuesday — Hydraulic Erosion — https://www.youtube.com/watch?v=VhWfWcvuV4I (2023-06-06)
- Хост / поколение: C4D; TerraformFX (tfTerrain, tfNoise, фильтр tfErosion)
- Задача: прорезать русла и наносы в долинах на noise-ландшафте, симулируя дождь, стекающий по склонам.

## Шаги
1. **tfTerrain** ▸ Add Operator ▸ **tfNoise** (детали): тип billowy, **Octaves 12**, у оператора **Gain 4 cm**. [▶ 0:42](https://youtu.be/VhWfWcvuV4I?t=42)
2. Второй **tfNoise** (горы): **Turbulence**, Octaves **12**, Scale **120%**, Gain **70**. [▶ 0:59](https://youtu.be/VhWfWcvuV4I?t=59)
3. Добавьте фильтр **tfErosion**. Режим по умолчанию **Thermal weathering** (сглаживание) → **Hydraulic**: *2D Particle* = быстрая математическая аппроксимация; ***X-Particles*** = полноценная 3D-симуляция частиц, больше настроек, медленнее, результат лучше — используйте его. [▶ 1:46](https://youtu.be/VhWfWcvuV4I?t=106)
4. По умолчанию: **10,000** частиц, жизнь **30** кадров, скатываются вниз по склону. Зона дождя Everywhere → **Above**, **30 cm** (дождь только на вершинах). [▶ 2:29](https://youtu.be/VhWfWcvuV4I?t=149)
5. Erosion ▸ кривая **Erode Life**: по умолчанию растёт от 0 при рождении; поднимите первый узел, чтобы частицы сильно размывали с самого начала. [▶ 3:05](https://youtu.be/VhWfWcvuV4I?t=185)
6. **Iterations 10** (повтор симуляции; прогресс внизу слева) → появляются русла. [▶ 3:54](https://youtu.be/VhWfWcvuV4I?t=234)
7. Частиц **20,000**; включите **Liquid**, чтобы частицы взаимодействовали как вода (медленнее, реалистичнее). [▶ 4:34](https://youtu.be/VhWfWcvuV4I?t=274)
8. Сравнивайте через **Blend** оператора эрозии (0 = без эрозии, полное = размыто). [▶ 5:00](https://youtu.be/VhWfWcvuV4I?t=300)
9. Финальный дожим (на время правок отключайте фильтр, чтобы не пересчитывалось): Lifetime **55**, частиц **30,000** → гораздо более глубокие русла. [▶ 5:22](https://youtu.be/VhWfWcvuV4I?t=322)

## Как сейчас (новые инструменты)
Тот же tfErosion в Fused 2025.x; текстурируйте результат через **Advanced Terrain Shader** / канал curvature (Fused 2024.2) и раскидывайте объекты через **tfDistribute**. См. "TerraformFX animated terrain trough" (2024-11-19).
