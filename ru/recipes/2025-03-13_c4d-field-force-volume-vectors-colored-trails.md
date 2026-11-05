# Завихрения-шлейфы по касательной к поверхности (C4D Field Force + векторы Volume Builder Cross Product + nxColor ▸ xpTrail Per Vertex в Redshift)

- Источник: Bite-Sized — X-Particles C4D Forces — https://www.youtube.com/watch?v=W8E4taTkKag (2025-03-13)
- Хост / поколение: нативные силы/Volume Builder C4D управляют xpEmitter; NeXus GPU nxColor; CPU xpTrail; Redshift
- Задача: частицы хаотично кружат, но остаются на торе и рисуют шлейфы, цвет которых прорисовывается по мере смены направления.

## Шаги
1. xpEmitter испускает статичные частицы с поверхности **Torus**. Любой объект C4D Simulate ▸ Forces действует на X-Particles/NeXus (например Attractor).
2. **Field Force** с **Random field** (scale ~700%), Velocity Type **Set Absolute Velocity**, ~**50** → шумный поток (для простого noise лучше GPU **nxTurbulence**).
3. Трюк с поверхностью: **Volume Builder**, Volume Type **Vector**; внутри тор *под* Random field; у Random field blend **Cross Product** и Creation Space **Objects Below** → случайные векторы, всегда касательные к поверхности тора.
4. Больше детализации: больше pipe segments у тора, у Volume Builder **Voxel Size ~2**.
5. Field Force: уберите random field, добавьте **Volume Builder** как volume-объект; скройте builder → частицы циркулируют по поверхности.
6. **xpTrail** на эмиттер.
7. **nxColor ▸ Gradient by Parameter ▸ Direction**, загрузите пресет градиента (например Violet).
8. Материал Redshift на шлейф: Standard ▸ Emission weight **2**; нода **Vertex Attribute**, Attribute Name из пресетов **Curves ▸ curve color** → Geometry ▸ Opacity для аддитивного вида. Redshift Object tag на шлейфе: толще, с сужением к кончикам.
9. xpTrail ▸ Thickness and Color ▸ **Trail Color Mode**: Particle Color перекрашивает весь шлейф сразу; **Per Vertex** прорисовывает смену цвета во времени (с Tracer в C4D так не сделать).

## Как сейчас (новые инструменты)
nxFollowGeo (преемник xpFollowSurface) плюс слоёный nxTurbulence удерживают частицы на поверхности на GPU; nxTrail — объект шлейфов NeXus, а nxWarp (2026.1) может дополнительно формировать потоки.
