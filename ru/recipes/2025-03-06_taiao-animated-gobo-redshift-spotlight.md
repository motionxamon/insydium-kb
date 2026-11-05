# Зацикленный гобо с тенью растения (рендер ветровой петли Taiao ▸ текстура Redshift Spot Light)

- Источник: Bite-Sized — Animated Gobos — https://www.youtube.com/watch?v=AEsbVRNUK3E (2025-03-06)
- Хост / поколение: C4D; растение Taiao с Forces; Redshift
- Задача: бесшовно зацикленный чёрный силуэт растения на белом — анимированный гобо, падающий на стену.

## Шаги
1. **Taiao** ▸ дерево/растение по умолчанию. Plant Layers ▸ Leaves: длиннее, тоньше; вкладка Main **Count ~15**; Distribution: наклоните листья вверх. [▶ 0:34](https://youtu.be/AEsbVRNUK3E?t=34)
2. Чистый силуэт: материал Redshift без цвета и отражений (чёрный) на растении; **Redshift Camera ▸ Background ▸ Override**, цвет **белый**. [▶ 1:17](https://youtu.be/AEsbVRNUK3E?t=77)
3. Вкладка **Forces** растения ▸ включить (ветер); уменьшите силу ветра, а на уровне Leaf — frequency и strength для медленного плавного покачивания. [▶ 1:45](https://youtu.be/AEsbVRNUK3E?t=105)
4. **Loop time** = длине таймлайна (в демо работают в секундах: **3**) → бесшовная петля. [▶ 2:14](https://youtu.be/AEsbVRNUK3E?t=134)
5. Дешёвый рендер: sampling ~0.5 с denoise, buckets **512 × 512**, output **1280 × 1280**, PNG-секвенция (~6.5 мин). [▶ 2:40](https://youtu.be/AEsbVRNUK3E?t=160)
6. Сцена шота: меню Light ▸ **Spot Light**, направьте на поверхность. Spot ▸ Texture: загрузите PNG-секвенцию ▸ опции секвенции ▸ Animation ▸ Mode **Loop**, **Detect Frames**. [▶ 4:51](https://youtu.be/AEsbVRNUK3E?t=291)
7. Настройка: exposure для контраста тени, угол конуса, Details ▸ включите **Softness affects Gobo**, softness ~**5** (15 и 8 оказались слишком мягкими); intensity ~3. [▶ 5:24](https://youtu.be/AEsbVRNUK3E?t=324)
8. Жалюзи: Cloner из планок перед светом даёт тени ламелей поверх растения. [▶ 6:13](https://youtu.be/AEsbVRNUK3E?t=373)
