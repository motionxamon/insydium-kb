# Эмиссия со сплайна, спроецированного на волнующуюся поверхность (mtSplineSample + mtPointProject + кэш Jiggle)

- Источник: Top Tip Tuesday — Surface Project Particles — https://www.youtube.com/watch?v=iPU7lU5pCUA (2024-07-02)
- Хост / поколение: C4D; MeshTools (mtSplineSample, mtPointProject) + xpEmitter + NeXus (nxGravity, nxTurbulence, nxConstraints)
- Задача: текстовый сплайн «X» едет по анимированной пружинящей поверхности и испускает частицы, которые по ней кувыркаются.

## Поверхность
1. Plane 800×400, сегменты **80×40**. Дочерний **Displacer** с Noise, **global scale 2000**, **animation speed 1**.
2. Под ним дочерний **Jiggle**: **Stiffness 10**, **Structural 10**, **Strength 200%** → волнующаяся пружинящая поверхность.
3. Jiggle ▸ Cache ▸ **Calculate**, потом отключите Displacer (он уже запечён).

## Проекция
4. **mtSplineSample** с текстом в качестве дочернего, Method **Distance** (точка каждые 2 cm), замкните сплайн, скройте отображение точек/градиента.
5. **mtPointProject**: поверхность = плоскость, spline sample — дочерний. По умолчанию направление лучей Parallel +Y → поменяйте на **+Z**, чтобы попадать в плоскость. **Offset 1 cm**, **Blend 99%**.

## Частицы
6. xpEmitter Object = point project, **Edges**; Rate, lifespan 35 (вар. 10), **2000/frame**, speed 0, radius 2. xpCollider на плоскость.
7. **nxGravity** 200, **nxTurbulence**.
8. По желанию **nxConstraints ▸ Viscosity**: connection limit 4, radius 25 cm → частицы держатся вместе, пока поверхность их подбрасывает.
