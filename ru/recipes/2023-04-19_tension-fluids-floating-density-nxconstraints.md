# Тягучие красочные щупальца на поверхности жидкости (nxFluids SPH, density в nxFluids tag, свои nxConstraints Forces на каждый эмиттер, nxDrag)

- Источник: NAB 2023 - INSYDIUM Training — Tension Fluids - Part 1 — https://www.youtube.com/watch?v=UQvPo7CCcIc (2023-04-19)
- Хост / поколение: C4D; NeXus GPU (nxFluids SPH, nxGravity, nxConstraints, nxDrag, nxTurbulence) внутри X-Particles с xpEmitter; CPU xpCache
- Задача: три цветные жидкости выплёскиваются на скрытый слой воды, и каждая собирается в свои тягучие щупальца (вид смешанной краски).

## Исходная сцена
Cube **700 × 50 × 700 cm**, сделать редактируемым, удалить верхний полигон → открытый лоток. Display tag (Lines). **xpCollider tag**: Bounce 0, нормали направить **внутрь** (иначе лоток «протекает»).

## Шаги
1. **Base-эмиттер**: форма Box, вписанная чуть внутрь лотка (через ортогональные виды), затем уменьшенная по высоте вдвое и опущенная — намного меньше частиц, а поверхность всё равно сплошная. **Shot**, тип Shot **Hexagonal**, скорость 0, **radius 2 cm**, Dots, Draw Emitter выключить. [▶ 2:25](https://youtu.be/UQvPo7CCcIc?t=145)
2. **nxGravity** (дефолт) + солвер **nxFluids** в режиме **SPH**, **Substeps 4**. [▶ 3:30](https://youtu.be/UQvPo7CCcIc?t=210)
3. **Цветные эмиттеры** (green, затем копии blue и red): тонкие box-эмиттеры, **Hexagonal** (непрерывно), Emit All Frames выключить, старт **F100**, конец **F300**, таймлайн 500 F, скорость 0, **тот же радиус 2 cm** (разные радиусы делают SPH нестабильным). [▶ 7:28](https://youtu.be/UQvPo7CCcIc?t=448)
4. **nxFluids tag** на каждом эмиттере: у base Density **1000**, viscosity сильно снизить; у цветных **Density 50**, Viscosity 1, Surface Tension 1 → они плавают сверху. [▶ 8:54](https://youtu.be/UQvPo7CCcIc?t=534)
5. Движение: **Vibrate tag** на цветных эмиттерах (position + rotation). С Regular Pulse: ~20 cm по X/Z, heading 60° → 40°. Без Regular Pulse (шум, свой Seed на эмиттер, например 73) поднять амплитуду до 60–100 при frequency 0.6. Каждую копию повернуть по-своему. [▶ 9:37](https://youtu.be/UQvPo7CCcIc?t=577)
6. **nxConstraints ▸ Forces** — по одному на цвет («constraints green/blue/red»). В список **Modifiers** каждого другого эмиттера добавить констрейнты, которые не должны на него действовать (минус = исключён), включая base-эмиттер. Repulsion и Inner сначала выключить; поднять Attraction (≈76), радиус **13**, limit 16 → частицы слипаются только со своим цветом. [▶ 17:28](https://youtu.be/UQvPo7CCcIc?t=1048)
7. Доводка: Inner radius **2**, Repulsion **10** с радиусом **4** — не даёт комкам схлопнуться. Меньше радиус / limit / attraction = тоньше и детальнее, меньше «блобов». [▶ 21:26](https://youtu.be/UQvPo7CCcIc?t=1286)
8. **nxDrag** (base исключить): Density Water, Drag Coefficient **Fighter Aircraft**, strength multiplier 110 → потом **150** (Sphere в воде слишком сильно тормозит). [▶ 23:14](https://youtu.be/UQvPo7CCcIc?t=1394)
9. **nxTurbulence** Simplex, strength **15**, масштаб чуть больше, ограничить **Spherical field** в центре бассейна; base-эмиттер исключить. [▶ 25:34](https://youtu.be/UQvPo7CCcIc?t=1534)
10. **xpCache** во внешние файлы, все эмиттеры: ~3 мин на 500 F в демо. [▶ 27:33](https://youtu.be/UQvPo7CCcIc?t=1653)

## Подводные камни
- Если нормали коллайдера смотрят наружу, открытый контейнер протекает.
- Перед перекэшированием снова включить кэш base-эмиттера.

## Как сейчас (новые инструменты)
Fused 2025.4 **nxFluids FLIP/APIC** со щупальцами от surface tension; в бете 2026.1 FLIP **Mixer** задаёт density, viscosity и surface tension для каждого эмиттера/группы, а **nxFalloff** заменяет поля C4D. Меш — **nxMesher**.
