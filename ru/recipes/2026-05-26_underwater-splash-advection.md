# Подводные пузыри от всплеска (адвекция EFX + nxMesher + дымка из частиц)

- Источник: Top Tip Tuesday — Underwater Splash — https://www.youtube.com/watch?v=Lds-YgrX6RE (2026-05-26)
- Хост / поколение: C4D, Fused 2025.4+ (nxExplosiaFX как невидимое поле скоростей, nxMesher) + Redshift
- Задача: объект падает в воду: крупные неровные пузыри плюс молочная дымка из мелких пузырьков, которые сначала уходят вниз, а потом всплывают.

## Поле скоростей EFX (не рендерится)
1. Домен nxExplosiaFX, **Voxel Size 3**. Источник: падающая Sphere, **Motion Gap Fill** (быстрый объект), Emit From Surface, **Surface Width 0**, Fuel 0.3 **weighted by Noise** (неравномерная эмиссия).
2. **Velocity From Object Motion 400%** → флюид уходит вниз, прежде чем плавучесть вернёт его наверх.
3. Simulation ▸ Dissipation: **выкл.** (дым/температура не исчезают).
4. Dynamics ▸ Forces: оставьте Turbulence/Vorticity по умолчанию + добавьте **Turbulence FBM**, очень сильный, scale ~38, octaves 1, **с маппингом на Document Time** (кривая перевёрнута: полная сила на 0 с → ноль к 0.15 с) → разбивает шлейф только в начале.
5. Display Draw Mode **Off**.

## Частицы
6. **Emitter Big**: Object = Sphere, Polygon Area, Rate 30 000/s только на кадрах 3–20, speed 0, radius 2 ±1.5. EFX ▸ Particle Advection → режим **Position**, strength **~83%** (частицы не прилипают к флюиду → пузыри слипаются в комки).
7. **Emitter Small**: дубликат, radius 1 ±0.2, **1.5 M/s**, отображение Dots; адвекция Position **100%**.
8. Помощник: сила **Wind**, направленная вверх (strength ~30), внутри Forces у EFX → помогает всплытию.
9. **xpCache** — Inclusion: снимите EFX (только частицы). Build. Затем отключите EFX.

## Мешинг и рендер
10. **nxMesher** на Emitter Big: Surface Size **Source 150%**, Polygon Size **1.5** (следите за VRAM), **Zhu-Bridson** → неровные капли-пузыри, без сглаживания. Кэшируйте через **Build Cache → Continue** (кэш частиц сохраняется).
11. Emitter Small → **Redshift Object tag** ▸ Particles: Sphere Instances, scale ~0.4, материал мелких пузырьков → мутная взбаламученная вода.
