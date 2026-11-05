# X-Particles — модификаторы Control, Generate и Sprite (CPU, `xp*`)

Источник: docs.insydium.ltd/x-particles/modifiers/* (Fused 2025, проверено 2026-11-03). Пересказ. У всех есть Mode Independent / Action-Controlled, Groups, Falloff/Fields, Mapping.

## Control
- **xpBlend** — смешивает radius/mass/color/scale/rotation между соседями в пределах Distance; Strength, Max Blend (конечный кадр), кривая Weight. → nxBlend (намного быстрее).
- **xpChangeGroup** — переводит частицы в New Group (обязательно), опционально меняет цвет/скорость/массу; Threshold, Probability. Быстрые частицы при низкой вероятности могут так и не переключиться.
- **xpColor** — Immediate / Fade Between / Gradient / Random…; также может менять форму отображения. Threshold 100% блокирует изменения. "Set Color" даёт переход только внутри falloff. → nxColor.
- **xpCustomData** — Increment/Decrement или Set Value для элементов Custom Data эмиттера (Data Type должен совпадать). Matrix/String не маппятся.
- **xpFreeze** — останавливает движение/вращение/масштаб (отметьте хотя бы одно), Freeze/Unfreeze, Set Speed to Zero. Быстрые частицы могут проскочить сквозь falloff.
- **xpHistory** — воспроизводит прошлое движение каждой частицы начиная с At Time (нужен **Rewind Data** в Extended Data эмиттера); Freeze During Playback. Применение: эффекты перемотки/реверса.
- **xpInfectio** — распространение от Seed Object(s) (обязательно); Search Radius, Max Infected, Incubation по цвету частиц, Immunity, Infected Lifespan 10 s. → nxInfectio.
- **xpInherit** — копирует velocity/color/radius/position у частиц **Target Emitter**; Distance Relative/Absolute, Time, Immediate; Probability, Weight. Применение: частицы «превращаются» в другую формацию.
- **xpKill** — Outside Bounds (по умолчанию) / Inside / Objects / Outside Camera FOV / Clamp to Max; Only Born; Isolated + Distance. → nxKill.
- **xpLife** — Kill / Increase-Decrease / Set New Lifespan / Set Relative to Age; New Lifespan меньше возраста = мгновенная смерть.
- **xpNegate** — сбрасывает флаги: frozen, stuck/sticky, привязку к источнику, разрыв constraints; ссылка Cover Modifier, чтобы не захватывало повторно.
- **xpPhysical** — меняет temperature, smoke, fuel, fire, bounce, friction во времени/заданием/шейдером (по умолчанию temp +100/кадр — уменьшите!). Питает xpExplosiaFX.
- **xpPython** — Python для каждой частицы в поле (`import xparticles; help(xparticles)` в консоли для API).
- **xpScale** — Radius (по умолчанию) / Scale / Mass; Operation Set Value, Falloff, Jiggle (только scale), Spline, Speed, Shader. Radius ≠ масштаб геометрии. → nxScale.
- **xpSound** — управляет параметрами по частоте/громкости .wav (FFT, диапазон dB, частотные полосы, Map Sound). Звук не воспроизводит — добавьте звуковую дорожку C4D.
- **xpTrailsMod** — Shrink / Expand / Grow (нужен xpTrail Length Mode Time) / Pulse длины трейла; Rate в точках трейла.
- **xpTransform** — частицы повторяют перемещение/масштаб/вращение связанного объекта.
- **xpTriggerAction** — запускает Actions (или переключает Action-Controlled модификаторы) при входе в falloff; Probability, Trigger Count. Перечисленные модификаторы должны быть Action-Controlled.
- **xpUnlinkTP** — отвязывает Thinking Particles (необратимо).
- **xpWeight** — дополнительный контроль силы других модификаторов по Age/Lifespan/Color/Speed/Shader (Weight Parameter по умолчанию None = без эффекта).

## Generate
- **xpSpawn** — см. таблицу движения (нужен Spawning Emitter).
- **xpMultiSpawn** — многоуровневый спаун *внутри того же эмиттера* (каждый уровень порождается от предыдущего): Spawn Count за кадр, Frames, Start At Age, Kill Source, Life/Speed/Direction дочерних. Применение: фейерверки. Рост экспоненциальный — держите число уровней и количество низкими.
- **xpBranch** — процедурное ветвление для xpTrail / xpSplineMesher; нужен дочерний объект **Sub-Branch**; Length Method Time 3 s, Bending Zigzag, Curl Angle <5°. Применение: молнии, деревья, трещины, корни.
- **xpTendril** — выпускает потоки частиц-усиков из каждого источника (щупальца); Interval 1 F, Tendril Length, Follow Source (игнорирует другие модификаторы), Max Tendril Particles.
- **xpDynamicParticles** — временные частицы-заполнители, которые появляются/исчезают по радиусу, сохраняя плотность (жидкости); не используйте исходный эмиттер как spawning emitter; Maintain Count + Max Count.
- **xpGeometry** — переключает, какой дочерний объект xpGenerator показывает частица (Index of Child Object; неверный = исчезает); Threshold.
- **xpMorph** — морфинг объектов генератора между целями (Morph Target Index с 1; Rate of Change). Threshold 100% может не сработать при subframes >1 → ставьте 98–99%.

## Sprites (с генератором xpSprite)
- **xpLight** — анимирует яркость/inner distance света спрайтов сплайнами (Particle Age или Step Count).
- **xpSpriteControl** — меняет тип/материал спрайта (Material Index) для каждой частицы.
- **xpSpriteShaderControl** — управляет xpSpriteShader на спрайтах.
- **xpText** — меняет текст на текстовых спрайтах (буквы/цифры/пользовательский текст, инкремент, регистр) — перекрывает настройки текста xpSprite. Применение: счётчики, текст «падающего кода».
