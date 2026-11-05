# Рост слизевика по бревну (mtRemesh + mtShortestPath + xpSplineMesher)

- Источник: Bite-Sized — MeshTools Slime Mold — https://www.youtube.com/watch?v=POC6gx3p4rc (2025-09-18)
- Хост / поколение: C4D; MeshTools (**mtRemesh**, **mtShortestPath**) + CPU **xpSplineMesher** (X-Particles Generators)
- Задача: органичные растущие прожилки слизевика, расползающиеся из одной точки по части меша.

## Шаги
1. Дублируем бревно (Ctrl-перетаскивание), оставляем только ту полигональную выделенную область, где должен расти слизевик (инвертируем выделение, удаляем). Оставляем меш **триангулированным** — треугольники дают органичные пути, квады — сеткоподобные. [▶ 0:57](https://youtu.be/POC6gx3p4rc?t=57)
2. **mtRemesh** (триангуляция Делоне): **Feature angle 180°** (следовать поверхности), **Edge length ~0.3** для плотной сети треугольников. Делаем editable, выкидываем null. [▶ 1:36](https://youtu.be/POC6gx3p4rc?t=96)
3. Выбираем одну вершину во влажной расщелине ▸ Select ▸ **Set Selection** = стартовая точка. [▶ 2:16](https://youtu.be/POC6gx3p4rc?t=136)
4. **mtShortestPath** ▸ Objects: ремешнутый кусок; Start = **Source** → тег выделения точек. [▶ 2:53](https://youtu.be/POC6gx3p4rc?t=173)
5. **End number** = сколько точек охватывает сеть: **800** для работы, ~5,000 чтобы покрыть весь меш; при анимации это выглядит как рост. Отключаем отображение стартовой/конечной точек. [▶ 3:42](https://youtu.be/POC6gx3p4rc?t=222)
6. Сплайн: **Linear → B-Spline**, Intermediate points **Uniform** → плавные кривые. [▶ 4:13](https://youtu.be/POC6gx3p4rc?t=253)
7. **xpSplineMesher** с объектом shortest-path в качестве источника: выключаем **joins**, **size 2**, **subdivisions 2** (круглое сечение вместо квадратного). [▶ 4:35](https://youtu.be/POC6gx3p4rc?t=275)
8. Size ▸ **Scale spline**: добавляем горб на одном конце для вздутых кончиков. [▶ 5:13](https://youtu.be/POC6gx3p4rc?t=313)
9. Анимируем слайдер **Growth** у мешера для ползущего проявления. Опционально: Displacer для пузырчатой поверхности. [▶ 5:56](https://youtu.be/POC6gx3p4rc?t=356)

## Как сейчас (новые инструменты)
У **nxBioLogic** (2026.1 beta) есть режим Physarum (слизевик) с трубчатыми мешами — альтернатива этому геометрическому подходу, симулируемая на GPU.
