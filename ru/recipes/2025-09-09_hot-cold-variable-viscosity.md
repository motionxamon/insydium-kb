# Горячая текучая / холодная тягучая жидкость, которая снова плавится при контакте (группы + nxBlend + mapping вязкости)

- Источник: Top Tip Tuesday — Variable Viscosity — https://www.youtube.com/watch?v=_k0LatnQQJw (2025-09-09)
- Хост / поколение: NeXus (nxFluids SPH, слой nxConstraints Viscosity, nxQuestion, nxBlend) — эпоха до FLIP
- Задача: жидкость вроде лавы: медленные частицы остывают и густеют, горячие брызги снова их расплавляют.

## Исходная сцена
Анимированный эмиттер на коллайдеры; **nxGravity 300**; **nxFluids SPH** Smoothing Radius **150%** (меньше брызг), substeps 8; слой **nxConstraints Viscosity** с высокой жёсткостью (тягучесть).

## Шаги
1. Группы эмиттера: **Hot** (группа 1, только первая группа — рождаются горячими) и **Cold** (группа 2). [▶ 1:59](https://youtu.be/_k0LatnQQJw?t=119)
2. nxQuestion:
   - `If Group = Cold → Set Color black` (низкий **Weight** → плавно темнеет до чёрного)
   - `If Speed < 25 cm/s → Set Group Cold` / `Else → Set Group Hot` (пересчитывается каждый кадр)
3. **nxBlend** Color, **Addition**, Distance 15, **Strength 1000%** → белые (горячие) частицы осветляют чёрные при контакте = повторное плавление. [▶ 6:59](https://youtu.be/_k0LatnQQJw?t=419)
4. **nxConstraints Mapping ▸ Color Brightness → Stiffness слоя Viscosity**: чёрный = полная жёсткость, белый ≈ 0 (резкий спад). [▶ 7:59](https://youtu.be/_k0LatnQQJw?t=479)
→ Непрерывный цикл нагрев/остывание/повторное плавление.

## Новые варианты
FLIP/APIC (Fused 2025.4) мапит вязкость напрямую (см. "Chocolate Set"); 2026.1 beta добавляет неньютоновские Flow Index / Yield Stress.
