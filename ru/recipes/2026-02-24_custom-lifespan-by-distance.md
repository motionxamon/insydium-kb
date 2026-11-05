# Убивать частицы по пройденному расстоянию (сброс age в nxQuestion + Set Life)

- Источник: Top Tip Tuesday — Custom Lifespan — https://www.youtube.com/watch?v=Lh_UZhFHCQ8 (2026-02-24)
- Хост / поколение: NeXus (nxQuestion, слои nxTurbulence, nxColor по скорости) — C4D и Blender
- Задача: турбулентные потоки, которые естественно редеют — медленные частицы задерживаются, быстрые умирают раньше.

## Варианты
1. Просто: у эмиттера Full Lifespan выкл, Lifespan ≈ 174 F + вариация.
2. Лучше: оставьте Full Lifespan, поставьте **nxQuestion после nxColor**:
   ```
   If Traveled > 650–750 cm (± variation)
     Action Set Color yellow (debug, remove later)
     Action Set Age = 0  [Set Once]
        └─ Action Set Life = 30 F (±20)
   ```
   Без **сброса age** частица, которой уже 300 кадров, умирает мгновенно, когда ей задают жизнь в 30 кадров. **Set Once** на действии с age позволяет возрасту снова отсчитываться вверх.

## Почему
Время жизни привязано к расстоянию → медленные частицы живут дольше, и шумные потоки затухают органично.
