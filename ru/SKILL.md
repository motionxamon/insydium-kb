---
name: insydium-kb
description: База знаний по инструментам INSYDIUM — X-Particles (CPU xp*), NeXus GPU (nx*) в Cinema 4D и Blender, MeshTools, TerraformFX, Taiao, Jidou — плюс рецепты из Top Tip Tuesday. Использовать при сборке или отладке любых эффектов с частицами, жидкостями, дымом/огнём, тканью, MPM, trail'ами, рельефом, растениями или процедурными мешами в INSYDIUM Fused или NeXus for Blender.
---

# База знаний INSYDIUM (X-Particles · NeXus · Fused)

Справочник-пересказ, собранный по docs.insydium.ltd (Fused 2025 + NeXus 2026.1 Beta 3, проверено 2026-11-03) и публичным YouTube-туториалам INSYDIUM (Top Tip Tuesday и др.). Это не официальная документация — если что-то важно, откройте страницу-источник по ссылке.

## Как отвечать с помощью этого скилла
0. **Начинайте с самых новых инструментов.** Сначала прочитайте `references/whats-new.md`. По умолчанию предлагайте путь через NeXus 2026.1 (nxMPM, nxOcean, nxWarp, nxShatter, nxSpawn, nxBioLogic, новые falloff'ы, FLIP non-Newtonian…), затем стабильный путь через Fused 2025.4, затем legacy CPU — и указывайте, что в beta. По датам релизов оттуда сообщайте пользователю, если совет/туториал устарел.
1. **Определите хост и поколение** (читайте `references/legacy-vs-nexus.md`):
   - Cinema 4D CPU X-Particles (`xp*`), NeXus внутри X-Particles (`nx*` на оранжевом xpEmitter) или NeXus 2026 (`nxEmitter`, C4D beta / Blender).
   - Если пользователь не уточнил, спросите хост и версию либо дайте сначала современный путь через NeXus, а вторым — запасной вариант на CPU.
2. **Найдите эффект** в `INDEX.md` (задача → объекты → файлы рецептов).
3. **Прочитайте нужные справки по объектам** из `references/` и подходящие файлы из `recipes/` — их находит `grep -i <tool or effect> recipes/README.md` (309 рецептов, новые сверху; рецепты для Blender помечены `blender-` / Host: Blender).
4. **Отвечайте в виде рецепта сборки:** иерархия сцены (дерево), объекты по порядку, несколько важных параметров со стартовыми значениями, как кэшировать/мешить/рендерить и типичные подводные камни. Указывайте, к какому поколению относится каждый шаг. Для Blender переводите единицы (C4D cm/Y-up → Blender m/Z-up).
5. Если рецепт из старой версии, отметьте, что изменилось (см. "Things that changed" в legacy-vs-nexus.md).
6. Не выдумывайте названия параметров. Если названия нет в этих файлах, так и скажите и предложите проверить страницу документации.

## Файлы
- `references/whats-new.md` — хронология релизов (2022 → 2026.1 Beta 3) + шпаргалка «как делать по-новому». **Читать первым.**
- `INDEX.md` — индекс по эффектам/задачам.
- `references/legacy-vs-nexus.md` — поколения, таблица соответствия xp→nx, ломающие изменения.
- `references/video-facts.md` — параметры, значения по умолчанию и поведение, собранные из ~310 видео INSYDIUM (2023–2026), а также `references/legacy-catalog/` — краткий каталог ~220 старых видео 2017–2022 (X-Particles 3.5/4, Premium/Maintenance Training): что показано и чем это делать сейчас, сгруппированы по поколениям. Для вопросов «что делает эта настройка / какое значение по умолчанию».
- `references/c4d/xp-emitter.md` — xpEmitter, все вкладки.
- `references/c4d/xp-system-cache-control.md` — xpSystem, xpCache, настройки проекта, Questions/Actions, маппинг данных, QuickTools, xpPainter.
- `references/c4d/xp-modifiers-motion.md` — таблица CPU-модификаторов движения (+xpSpawn).
- `references/c4d/xp-modifiers-control-generate.md` — CPU-модификаторы control/generate/sprite.
- `references/c4d/xp-generators-dynamics.md` — генераторы (xpGenerator, xpTrail, мешеры, xpShatter…), CPU-динамика (ExplosiaFX, жидкости, ткань, Bullet), теги.
- `references/c4d/xp-utilities-render.md` — утилиты, группы/действия, рендер и шейдеры.
- `references/c4d/nexus-core.md` — концепции NeXus, nxConstraints, nxFluids, nxExplosiaFX, nxMesher.
- `references/c4d/nexus-dynamics-logic.md` — nxFoam/Splash/Wave, nxQuestion (GLSL), Mapping, nxFalloff, настройки, nxTurbulence.
- `references/c4d/nexus-modifiers.md` — все nx-модификаторы.
- `references/c4d/meshtools.md`, `terraformfx.md`, `taiao-jidou.md`.
- `references/blender/nexus-blender.md` — настройка NeXus for Blender, объекты только для Blender, 2026.1 Beta (nxMPM, nxOcean, nxWarp, nxShatter, nxSpawn…).
- `recipes/` — по файлу на каждый туториал/Top Tip: задача, дерево сцены, шаги, версия, ссылка.

- `references/tools/` — карточки инструментов: по странице на инструмент (79 шт.) со всеми настройками и значениями из видео, подводными камнями и всеми рецептами. Начинай отсюда для вопросов «как настроить nxMPM / nxFLIP / xpTrail».
