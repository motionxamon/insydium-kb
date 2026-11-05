# Режиссируемые slow-mo всплески частиц над ступенями и песком (nxFluids SPH, скрытые tfRock-«отбойники», xpCache Continue/Hold, Cycles 4D)

- Источник: Black Friday Breakdown — Particle Splash — https://www.youtube.com/watch?v=t-1ZIIRF8Jg (2023-11-20)
- Хост / поколение: C4D; G2 — xpEmitter + GPU **nxGravity / nxFluids (SPH)**, CPU xpCollider/xpJoin/xpCache; TerraformFX + MeshTools; рендер Cycles 4D
- Задача: несколько отдельно просчитанных цветных всплесков, которые разбиваются о камни над пятигранными ступенями на склоне, засыпанном песком.

## Исходная сцена
tfTerrain с уклоном вниз (500 сегментов, оставляем для рендера), пятигранные ступени = Cylinder с 5 rotation segments, 4 объекта **tfRock** как невидимые «отбойники» для всплесков.

## Шаги
1. Оптимизируйте коллизионную геометрию: копия террейна → **mtRemesh** (Delaunay), поднимайте Edge Length, пока форма ещё держится → C, оставьте только полигональный объект («terrain sim»); удалите полигоны вне кадра. У tfRock Subdivisions → 0.
2. Тег **xpCollider** на terrain sim (Bounce 0, Friction 0). Ступени и камни — каждые в свой **xpJoin** (один тег коллайдера на join); у камней Bounce 10, Friction 5. Цвет отображения всех коллайдеров — чёрный.
3. Эмиттер: Shape **Box** (тонкий, низкий), наклонён к камням, Direction **−Z**; Emission **Shot**, Shot type **Hexagonal**; Radius 7 (HUD ≈16,000 частиц для черновика).
4. **nxGravity** 981 → **60** (слабая гравитация имитирует slow motion). **nxFluids SPH**, Substeps 5.
5. Цвет во viewport: Gradient Parameter по **Speed**, 0–120 (позже 140); отображение Square, меньший size factor.
6. Форма всплеска: выше эмиттер = больше частиц = сильнее удар; nxFluids **Viscosity 15**, **Surface Tension 10** (вода «большего масштаба» с бусинами-тендрилами); Speed эмиттера 150 → **100**. Двигайте/вращайте камни, открывая щели → листы и струи жидкости.
7. Финальное разрешение Radius **0.5** (число частиц растёт очень быстро) → **xpCache** (внешние файлы, Compress on build) — 35 с в демо.
8. Следующий всплеск: дублируйте эмиттер (удалите его cache tag), измените форму/положение, новый цвет, выключите закэшированный эмиттер; Build Cache ▸ **Continue** кэширует только новый (Override пересчитывает всё; если оба живые — они взаимодействуют).
9. Песок: коллайдеры выкл., новый эмиттер «sand» с render-террейна (Polygon Area), Shot, Random, Speed 0, **1,000,000**, режим Simulate (рождение на кадре 0), отображение Dots; у эмиттера **Falloff Sphere** с радиусом 300 → растушёванная плотность. Кэшируйте **один кадр**, затем в cache tag переопределите playback на **Hold** и верните диапазон в 90 кадров.
10. Cycles 4D: два soft box (key 20, rim 3, тёплый оттенок), защищённая камера. Террейн: Principled BSDF, чёрный base, подстройка Specular/Roughness. **Cycles 4D Instance tag** на каждый эмиттер (песок: меньше сегментов, Size 50%, Size Variation 60, Size Multiplier 20 → 10; всплески ~70%). Материал частиц = **Translucent BSDF** + чёрный Principled (specular) через **Add Shader**; оранжевая/синяя копии на каждый всплеск. Ступени: Principled с размытым specular + **Fillet** на капах Cylinder для бликов на кромках. Скройте камни. DOF в теге камеры, фокус на ступени.

## Подводные камни
- SPH: у всех частиц во fluid-симуляции должен быть одинаковый радиус, иначе она нестабильна.
- Всплески, закэшированные по отдельности, проходят друг сквозь друга — симулируйте вместе, если в кадре они пересекаются.
- Для финала нужно ~4 миллиона более мелких песчинок и ~6–7 наложенных всплесков.

## Как сейчас (новые инструменты)
Fused 2025.4: nxFluids **FLIP/APIC** с тендрилами от surface tension, **nxSplash** для корон и GPU **nxMesher**, если нужен меш. NeXus 2026.1 beta (G3): nxEmitter + объекты **nxCollider** + **nxCache** (frame range); в Blender то же через NeXus Hierarchy.
