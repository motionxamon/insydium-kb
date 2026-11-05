# Рвущаяся сетка из констрейнтов, сдуваемая с логотипа (xpConstraints Birth Connections, xpWind, xpChangeGroup, xpTrail ▸ Constraints, xpSplineMesher)

- Источник: Maintenance Training — Dynamics - Constraints - Tearing Net Tutorial — https://www.youtube.com/watch?v=WeuXOmENNXA (2023-06-12)
- Хост / поколение: C4D; CPU X-Particles (xpConstraints, xpWind, xpChangeGroup, xpTrail, xpSplineMesher, xpOpenVDBMesher)
- Задача: паутина связанных частиц на логотипе MoText, которую срывает ветер; срыв режиссируется движущимся полем, а затем превращается в рендерящиеся трейлы / меши.

## Исходная сцена
MoText «XP» (bold, по центру), экструзия чуть глубже, Fillet Caps 3 шага / радиус 3; позже текст скрывается.

## Шаги
1. **xpEmitter ▸ Object**: Emitter Shape Object = MoText, эмиссия из **Polygon Area**; **Offset Origin 1 cm**, чтобы частицы были чуть над поверхностью. [▶ 1:54](https://youtu.be/WeuXOmENNXA?t=114)
2. Emission: **Shot**, **2000** частиц, полный lifespan, скорость 0. Display: Squares + включить **Display Constraints**. [▶ 2:33](https://youtu.be/WeuXOmENNXA?t=153)
3. **xpConstraints ▸ Connections ▸ Birth Connections** включить с дефолтами → сразу получается вид сетки. [▶ 4:14](https://youtu.be/WeuXOmENNXA?t=254)
4. **xpWind** повернуть на 90°, чтобы дул вверх. На MoText повесить **xpCollider tag** — частицы скользят по тексту, связи натягиваются и рвутся (когда именно — задают настройки разрыва в объекте Constraints). [▶ 7:12](https://youtu.be/WeuXOmENNXA?t=432)
5. Режиссура через группы: в эмиттере **Groups** ▸ добавить 2 группы, Mode **First Group Only** (все стартуют в группе 1). Wind ▸ **Groups Affected** = только группа 2. [▶ 8:43](https://youtu.be/WeuXOmENNXA?t=523)
6. **xpChangeGroup** (Control modifiers): New Group = группа 2, falloff = **Spherical field**. Анимировать сферу по тексту → частицы переходят в группу 2, их сдувает, и они тянут за собой соседей — разрыв выглядит органично. [▶ 10:36](https://youtu.be/WeuXOmENNXA?t=636)
7. Вариант рендера 1: **xpTrail** с эмиттером, **Algorithm ▸ Connections: Constraints**, затем выбрать слой Birth Connections; Display Constraints выключить. Трейлам дать материал X-Particles — они рендерятся. [▶ 13:23](https://youtu.be/WeuXOmENNXA?t=803)
8. Вариант 2: **xpSplineMesher** по трейлу, радиус ~0.5, **Joins выключить** (Joins нужны для ветвления в духе xpBranch и триангулируют трейлы из констрейнтов). [▶ 15:05](https://youtu.be/WeuXOmENNXA?t=905)
9. Вариант 3 (органичный, вязкий вид): **xpOpenVDBMesher** с Spline Mesher в качестве source; уменьшить Voxel Size и увеличить радиус Spline Mesher, чтобы было достаточно объёма для меширования. [▶ 16:28](https://youtu.be/WeuXOmENNXA?t=988)

## Подводные камни
- Эмиссия Rate выдаст 2000 частиц в секунду — для разового заполнения нужен Shot.
- Ветер с falloff от поля — только демонстрация идеи; нормальный контроль даёт переключение групп.
- Трейлы и мешеры поверх симуляции констрейнтов заметно замедляют проигрывание.

## Как сейчас (новые инструменты)
**nxConstraints** (те же слои, GPU) + **nxPin** для закрепления и **nxDeformer** для рвущегося меша в бете 2026.1; **nxTrail** и **nxMesher** заменяют xpTrail/xpOpenVDBMesher. Нативные GPU cloth/tearing + fraying пока только анонсированы для будущей беты NeXus.
