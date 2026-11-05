# Взрывающийся гранулярный бюст: рендер как песок и как снег (nxFluids SPH Granular, nxExplode, stability через Speed, xpOpenVDBMesher)

- Источник: INSYDIUM Training — Granular Collapse — https://www.youtube.com/watch?v=fxJI8py9BzU (2025-05-07)
- Хост / поколение: C4D; G2 NeXus (nxFluids SPH Granular, nxGravity, nxExplode, nxPush, nxKill) внутри xpEmitter + CPU **xpOpenVDBMesher**, xpCollider, xpCache; Redshift
- Задача: плотно упакованный песчаный бюст трескается от внутреннего взрыва и осыпается крупными и мелкими кусками; та же симуляция рендерится как песок из частиц и как снег из mesh с SSS.

## Исходная сцена
- Бюст из content browser C4D, увеличенный (Y ≈ 160 cm — объём определяет число частиц), на полу-кубе.
- **xpCollider** на полу: Bounce 0, Friction 100% (позже 20%).
- **xpEmitter** Shape Object (бюст), Emission **Shot** на 1-м кадре, тип Shot **Hexagonal**, Speed 0, Radius **1.3** для черновика (~85k частиц).
- Display ▸ Gradient Parameter = данные **Granular**, max ~30, градиент из пресета flame.
- Ctrl+D ▸ X-Particles ▸ **Subframe steps 4** (substeps флюида дробят только расчёт флюида; этот параметр дробит ещё и gravity/explode).

## Шаги — симуляция
1. **nxGravity** (по умолчанию) + **nxFluids** в режиме **SPH ▸ Granular**.
2. Влажный комковатый песок: Granular **Friction 90**, **Substeps** солвера **3 → 12** (больше итераций трения, конструкция держит собственный вес).
3. **Stability** — проверка скорости: частицы, расходящиеся быстрее этого значения, теряют трение. Опустить до ~**4**, чтобы пошли трещины.
4. **nxExplode**: центр = **This Modifier** (а не центр масс частиц), Timing **Scene Time = F5**. Fields ▸ **Spherical field**, Inner Offset 100%, радиус ~15, внутри бюста; вынести field из модификатора (в папку Utilities), чтобы двигать/нацеливать модификатор (назад и вбок) отдельно. На черновом количестве частиц нужна гораздо большая скорость (+300 variation).
5. Фейк «стоящей» фазы: nxGravity ▸ Mapping ▸ **Age** map F5–F7, сила 0 → полная, чтобы до взрыва ничего не оседало.
6. Продакшн: Radius **0.4** → чуть меньше 3 M частиц (для песка в таком кадре автор советует ~6 M). xpCache (compress on build): ~27 мин / 100 F. С теми же настройками взрыв теперь слишком сильный и дробит слишком мелко.

## Шаги — ломаем гексагональную сетку (проход рождения на один кадр)
7. Выключить модификаторы и коллизии пола (Collider ▸ снять Enable Collisions, куб оставить активным). Emission ▸ **Jitter XY/Z 0.3** (чуть меньше радиуса).
8. **nxPush**: Distance = **Particle Radius**, Strength 100, **Iterations 1000**. Под ним **nxKill**, Volume = Objects ▸ куб пола, Inside → убивает зёрна, вдавленные в пол.
9. Прогнать один кадр, затем Emitter ▸ Object ▸ **Initial State ▸ Set State** (~114 MB); Emission ▸ **Controlled only**. Выключить push/kill, включить обратно explode/fluids/gravity **и коллизии**.

## Шаги — управляемое осыпание
10. Friction коллайдера **20%** (зёрна скользят), nxExplode Speed **500**.
11. nxFluids ▸ Data Mapping ▸ map **Speed**, категория SPH, параметр **Stability**, диапазон **20–60 cm/s**, кривая от полного к низкому: медленные = крупные куски, быстрые = мелкая крошка. Перекэшировать. Display ▸ Dots + Force Display, чтобы смотреть кэш.

## Шаги — рендер
12. Песок: **Redshift Object tag** на эмиттере ▸ Particles ▸ **sphere instances**; стандартный материал (оранжевый оттенок, выше roughness) перекрывает цвет granular.
13. Снег: **xpOpenVDBMesher**, связанный с кэшем: Voxel Size **4 → 0.5**, Point Radius **10 → 1.9**; Filters ▸ удалить Median, добавить **Curvature** (Strength 100, Iterations 2) — сохраняет трещины, лёгкая шероховатость помогает SSS. Кэшировать mesher через **Build Cache ▸ Continue** (~10 мин), затем выключить эмиттер.
14. Материал снега (один Standard node): шероховатые отражения; **Transmission** с синим scatter color, Depth 100, weight ~0.2; **SSS** светло-голубой, weight 1, Scale 100, серый Radius, чтобы приглушить глубину. На пол — дефолтный материал ради отражений.
15. Настройки рендера: 100 F, Bucket 512 (зависит от VRAM). Снег: **denoising включён + Random Noise Pattern выключен**. Песок: denoising выключен (он размажет зёрна), threshold ниже, Random Noise Pattern включён. Pixel motion blur — на посте.

## Подводные камни
- Зёрна после jitter рождаются пересекающимися → SPH взрывается; всегда расталкивайте их и убирайте пересечения с полом до Set State.
- Не забудьте включить коллизии пола после прохода рождения.
- Рост числа частиц меняет картинку (взрыв сильнее, осколки мельче) — перенастройте скорость explode и stability.

## Как сейчас (новые инструменты)
2026.1 beta: материалы Sand / Snow в **nxMPM** (через пресеты **nxMaterial**, Auto Sleep, смена материала по скорости/damage) заменяют SPH granular; **nxBind** может держать форму и отпускать по age/speed; **nxMesher** (Fused 2025.4, GPU) заменяет xpOpenVDBMesher. Стабильный Fused 2025.4: тот же путь SPH granular, но с nxMesher.
