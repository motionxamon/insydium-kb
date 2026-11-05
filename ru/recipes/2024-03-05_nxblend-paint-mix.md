# Смешивание густых красок (nxFluids SPH + nxConstraints Viscosity + nxBlend)

- Источник: Top Tip Tuesday — nxBlend Paint Mix — https://www.youtube.com/watch?v=IG5GdX9U4lM (2024-03-05)
- Хост / поколение: C4D; NeXus GPU (nxFluids, nxConstraints, nxBlend, nxGravity) на xpEmitter
- Задача: три цветных вязких потока, цвета которых смешиваются в местах встречи, но сохраняют завихрения.

## Исходная сцена
xpEmitter Circle, плоскость −Y, Hexagonal, speed 0, radius 1 cm. **nxGravity 500**. **nxFluids SPH, substeps 4**.

## Шаги
1. **nxConstraints**: Iterations 3, слой **Viscosity** (не Birth): до 3 связей в пределах 20 cm → густо и тягуче. [▶ 1:14](https://youtu.be/IG5GdX9U4lM?t=74)
2. На эмиттер **Vibrate tag**: position, amplitude X 100 / Z 100, низкая частота. [▶ 1:56](https://youtu.be/IG5GdX9U4lM?t=116)
3. Дублируем эмиттер дважды; меняем цвет отображения; сдвигаем **seed** у каждого тега Vibrate для разного движения. [▶ 4:46](https://youtu.be/IG5GdX9U4lM?t=286)
4. **nxBlend**: по умолчанию смешивает Color (также scale, rotation, mass, radius). Стандартная сила 10% слишком слабая → **200%**; distance 10 cm; max blend duration 300 F. [▶ 4:08](https://youtu.be/IG5GdX9U4lM?t=248)
5. Distance 40 cm = всё быстро становится одного молочного цвета; возврат к 10 cm сохраняет исходные цвета вдали от зон контакта. [▶ 5:02](https://youtu.be/IG5GdX9U4lM?t=302)
6. Для мраморных полос: ещё поднимаем силу, режем **max duration до ~20 F** — сильное смешивание при первом контакте, затем цвета замирают. [▶ 5:45](https://youtu.be/IG5GdX9U4lM?t=345)

## Как сейчас (новые инструменты)
FLIP/APIC с вязкостью через **Mixer** на эмиттер (2026.1 beta) для густоты; nxBlend для смешивания цвета без изменений.
