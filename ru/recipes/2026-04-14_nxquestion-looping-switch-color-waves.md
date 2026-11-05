# Зацикленные цветовые волны, запускаемые касанием (переключатель-переменная в nxQuestion + nxBlend)

- Источник: Top Tip Tuesday — Looping Actions — https://www.youtube.com/watch?v=jw-XgGPX65E (2026-04-14)
- Хост / поколение: NeXus (nxQuestion Variable, nxBlend Addition) — C4D и Blender
- Задача: чёрные частицы на поверхности загораются, когда их касаются летящие частицы-«триггеры», а затем продолжают пульсировать чёрный↔белый расходящимися волнами.

## Цикл-переключатель (nxQuestion, Groups Affected = Group 2)
- Слой **Variable**: Integer, **Writeable**, **Particle** (на каждую частицу), имя `SWITCH`, по умолчанию 0.
- `If Math ▸ Variable SWITCH = 0 → Add Color white` (плавно светлеет)
- `If SWITCH = 1 → Set Color black` (плавно темнеет, чуть быстрее)
- `If Color Brightness < 0.05 → Set Variable SWITCH = 0`
- `If Color Brightness > 0.95 → Set Variable SWITCH = 1`
→ цвет управляет переключателем, а переключатель — цветом = бесконечный цикл. По той же схеме можно пульсировать радиус, скорость и т. д.

## Распространение по касанию
1. Эмиттер на поверхности: группы 1 и 2, First Group Only (все стартуют в группе 1, чёрные). Эмиттер-триггер стреляет сквозь них белыми сферами.
2. **nxBlend**: Color, **Blend: Addition** (только осветляет), небольшая Distance, Strength 300–800%, Max Blend = вся сцена, **Groups Affected: Group 1** (чтобы не мешать циклу). По желанию **Random field** на силу → неровное распространение.
3. Второй nxQuestion "group": `If Color Brightness > 0.9 → Set Group 2` → загоревшиеся частицы попадают в цикл-переключатель.
4. Быстрее/больше волн: поднимите силу Add Color (быстрее доходит до белого и раньше переключается).
5. На рендере замапьте чёрный/белый на цветные градиенты.
