### Шанс вопроса: 14%

Метрика Intersection over Union (IoU), также известная как Jaccard Index, используется для измерения степени пересечения между двумя объектами, обычно прямоугольниками или полигонами. Формула IoU выглядит следующим образом:

\[ \text{IoU} = \frac{\text{Площадь пересечения}}{\text{Объединенная площадь}} \]

Для прямоугольников формула вычисления IoU может быть реализована следующим образом:

```python
def calculate_iou(box1, box2):
    # Проверяем, что входные данные корректны (прямоугольники не должны перекрываться)
    if box1[0] >= box2[2] or box1[2] <= box2[0] or box1[1] >= box2[3] or box1[3] <= box2[1]:
        return 0.0
    
    # Находим координаты пересечения
    x_left = max(box1[0], box2[0])
    y_top = max(box1[1], box2[1])
    x_right = min(box1[2], box2[2])
    y_bottom = min(box1[3], box2[3])
    
    # Вычисляем площадь пересечения
    intersection_area = max(0, x_right - x_left) * max(0, y_bottom - y_top)
    
    # Вычисляем площади обоих прямоугольников
    box1_area = (box1[2] - box1[0]) * (box1[3] - box1[1])
    box2_area = (box2[2] - box2[0]) * (box2[3] - box2[1])
    
    # Вычисляем IoU
    iou = intersection_area / float(box1_area + box2_area - intersection_area)
    
    return iou
```

Пример использования функции:

```python
box1 = [1, 1, 3, 3]
box2 = [2, 2, 4, 4]
iou = calculate_iou(box1, box2)
print("IoU:", iou)
```

Этот код вычисляет IoU для двух прямоугольников `box1` и `box2`. Результат будет показывать степень пересечения между этими прямоугольниками.