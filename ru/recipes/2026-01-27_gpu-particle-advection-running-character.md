# Дымчатый шлейф частиц за бегущим mocap-персонажем (EFX advection)

- Источник: Top Tip Tuesday — GPU Particle Advection — https://www.youtube.com/watch?v=LPu79OH-yC0 (2026-01-27)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX, particle advection, nxKill FOV) + Redshift
- Задача: жидкие полосы срываются с ног бегущего персонажа и уносятся ветром назад.

## Шаги
1. Домен EFX подогнан по размеру, **Voxel 2**. Источник = **низкополигональный прокси** персонажа (быстро с Motion Gap Fill + Velocity from Object Motion) — см. "Mocap Sim Proxy".
2. Buoyancy **Gravity off**; Dynamics ▸ Forces: добавьте **Wind** (по умолчанию 50), дующий назад.
3. Эмиссия только с ног: у источника Temperature и Fuel **Weight by Tag** = polygon selection tag ног. **Pressure 0** (сохраняет наследование движения), **Motion Gap Fill** вкл. Высокая диссипация температуры.
4. Частицы: xpEmitter Object = высокополигональный персонаж для рендера, Polygon Area, **Selection** = тег ног, speed 0, radius 1 ±, старт с кадра 5 (пусть жидкость сначала сформируется), **Rate 50 000**.
5. EFX ▸ Particle Advection: добавьте эмиттер (настройки по умолчанию).
6. **nxKill → Outside Camera FOV** (подключите камеру) → огромная экономия.
7. Redshift Object tag ▸ **Point Instances**, размер ~0.03, простой белый материал → чёткие завитки.
