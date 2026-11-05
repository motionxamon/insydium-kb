# Заспавненные частицы, которые органично растут и исчезают (кривая nxScale Range + kill)

- Источник: Top Tip Tuesday — Scale Range — https://www.youtube.com/watch?v=THuXYZmNZjQ (2026-04-28)
- Хост / поколение: C4D, NeXus (nxQuestion Spawn, nxScale Range, nxWind Von Karman) + Taiao toPlant
- Задача: частицы, похожие на пыльцу, слетают с кончиков веточек растущего растения; каждая плавно увеличивается, а потом уменьшается.

## Дерево сцены
```
Join  └─ toPlant (polygon selection tag generated on the last branch layer)
xpEmitter "source": Object = Join, Selection = branches tag, Polygon Area, Rate 20, frames 60→end,
                    lifespan 2 F, speed 0, Stick Particle to Source
xpEmitter "spawn": (created by Add Emitter in the Spawn action) Display Circles + Force Display
nxQuestion
  Action Spawn (no question → always): Distance 0, Inherit Parent off, Full Life, speed 0, radius 0, light pink
  If Age > 50  AND  Radius < 0.1  → Kill
nxWind  (+X, Von Karman, more variation, friction velocity, less turbulence)
nxScale (Groups: spawn) — Range layer: Radius 0 → End 3 (variation), End Time 110 F,
        ease curve: fast rise to peak, slow ease back to 0
```

## Шаги / ключевые идеи
1. Чтобы toPlant нормально эмитил, он должен лежать внутри **Join**; включите **polygon selection** у слоя растения, чтобы эмитить только с самых тонких веток.
2. Короткоживущие частицы «source», прилипшие к веткам → действие **Spawn** в nxQuestion без вопроса = непрерывный спавн во второй эмиттер.
3. **nxScale Range**: ось Y = Radius Start→End, ось X = время Start→End; рисуем кривую вверх, затем вниз → частица растёт и уменьшается за время жизни.
4. Убивайте невидимые частицы, чтобы сэкономить время симуляции — но новорождённые стартуют с радиусом 0, поэтому условие kill — **Age > 50 AND Radius < 0.1**.
5. Отображение Squares не показывает радиус — для оценки размера используйте Circles/Spheres.
