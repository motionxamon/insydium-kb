# Taiao и Jidou (C4D, часть INSYDIUM Fused)

Источник: docs.insydium.ltd/taiao/*, /jidou/* (Fused 2025, проверено 2026-11-03). Пересказ.

## Taiao — процедурная природа
- **toPlant** — послойный конструктор растений/деревьев. Add Part: **Growth Point, Trunk, Branch, Leaf, Custom Object** (например, toFlower), Folder. Галочка = включить, кружок = соло (не забывайте про соло!), треугольник = теги выделения для слоя. Low-poly упрощение для фонов.
  - **Вкладка Growth:** Global Growth масштабирует рост всех слоёв во времени, либо рост задаётся на слой; Mode Growth / Global Growth / Animate Slider; Trigger Mode Random / Sequence / **Field** (field отключает Mode/Animate/Variation); задержка After Growth; Variation. Листья/цветы с ключами (иконка ключа) превращаются в отдельные полигональные объекты → медленнее.
  - **Вкладка Forces:** Wind Strength + Variation (>0%), Direction, Noise Type, Turbulence, Octaves, Seed, Strength/Frequency/Layer Weight по уровням; для бесшовных лупов ставьте **Loop Time на один кадр дальше конца таймлайна**; ветер на листьях = медленнее.
  - Умеет **излучать X-Particles** (опадающие листья).
- **toTree** — дерево методом space colonisation: ветви растут к **точкам притяжения внутри объёма** (Crown Shape или любой Volume Object — текст, логотип, тор); подключите **xpEmitter** (Speed 0), чтобы использовать частицы как точки притяжения; Attraction Points, Trunk Height, Seed; опция прохождения насквозь. Отлично для моушн-дизайнерских деревьев «растущий логотип».
- **toFlower** — процедурные части цветка (Petal, Sepal, Pistil, Stamen, Receptacle), у каждой свой стек модификаторов.
- **toLeaf** — листья Standard или Lobed с прожилками и модификаторами.
- **toGrass** — трава (или любой объект), раскиданная по ландшафтам/объектам/сплайнам: список Generate on, Hierarchy, Texture/Shader + Tolerance, Density, Blade Width/Height/Bend/Turbulence, диапазоны Height и Slope, **Multi-Instances** (дешевле клонов), отсечение по **Field of View**, **Avoid Objects**.
- **Preset Browser** — библиотека реальных видов растений.

## Jidou — процедурная анимация и риггинг
- **jdDriver** — управляет любым параметром C4D от сигнала: Add Drivers → выберите тип → **перетащите параметр** (например, Size.X) на драйвер → полоса Offset = активное время. Типы: **Color, Noise, Time, Value, Wave, Switch** + утилиты **Folder, Merge, Sequencer** (объединяют/выстраивают драйверы в последовательность). Output Clamp / Remap (Include Zero). Клонеры должны лежать под Null. Заменяет кучу Xpresso/выражений для покачиваний, пульсаций, лупов.
- **jdAniMate** — запоминает состояния Start и End (pos/rot/scale) и интерполирует их по сплайну тайминга (быстрая анимация A→B).
- **jdFlowCam** — камера по CamPoints со взвешенным таймингом, easing, пружиной, фокусным расстоянием.
- **jdGeoFlow** — двигает объекты по FlowPoints или пресетному сплайну с деформацией, easing, лупами.
- **jdGeoRoll** — катит объекты по поверхностям-коллайдерам с хэндлами; контакт и вращение считаются автоматически (бросок кубиков, колёса, валуны).
