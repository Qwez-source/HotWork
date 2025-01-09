### Шанс вопроса: 14%

В области компьютерного зрения (CV, Computer Vision) существует множество различных детекторов и архитектур, которые можно использовать для анализа изображений. Некоторые из наиболее известных включают:

1. **YOLO (You Only Look Once)**: YOLO — это быстрый детектор объектов, который использует сеть для прямого предсказания bounding boxes и классов объектов на изображении. Архитектура YOLOv3, в частности, известна своей высокой скоростью и эффективностью.

2. **SSD (Single Shot MultiBox Detector)**: SSD — еще один быстрый детектор объектов, который использует несколько предварительно определенных bounding boxes для каждого пикселя сетки. Это позволяет модели эффективно находить объекты на разных масштабах.

3. **Faster R-CNN**: Faster R-CNN — это популярная архитектура, в которой используются два основных компонента: региональная нейронная сеть (RPN) для предсказания возможных bounding boxes и классификации объектов. Архитектура обеспечивает высокую точность при относительно низком уровне производительности.

4. **RetinaNet**: RetinaNet — это архитектура, разработанная для решения проблемы несбалансированного распределения объектов в маленьких выборках (class imbalance problem). Она использует feature pyramid network (FPN) и focal loss для улучшения точности на фоне низкого качества классификаторов.

5. **Mask R-CNN**: Mask R-CNN — это расширение Faster R-CNN, которое добавляет дополнительное параллельное клонирование для предсказания масок объектов вместе с bounding boxes и классами. Это позволяет не только детектировать объекты, но и сегментировать их.

Пример кода на Python для YOLOv3 можно найти на GitHub:
```python
import cv2
import numpy as np

# Загрузка предварительно обученной модели YOLOv3
net = cv2.dnn.readNet("yolov3.weights", "yolov3.cfg")
layer_names = net.getLayerNames()
output_layers = [layer_names[i[0] - 1] for i in net.getUnconnectedOutLayers()]

# Загрузка изображения
image = cv2.imread("dog.jpg")
height, width, channels = image.shape

# Нормализация и создание blob-файла из изображения
blob = cv2.dnn.blobFromImage(image, 0.00392, (416, 416), (0, 0, 0), True, crop=False)
net.setInput(blob)
outs = net.forward(output_layers)

# Обработка выходов
class_ids = []
confidences = []
boxes = []
for out in outs:
    for detection in out:
        scores = detection[5:]
        class_id = np.argmax(scores)
        confidence = scores[class_id]
        if confidence > 0.5:
            # Объект обнаружен
            center_x = int(detection[0] * width)
            center_y = int(detection[1] * height)
            w = int(detection[2] * width)
            h = int(detection[3] * height)
            x = int(center_x - w / 2)
            y = int(center_y - h / 2)
            boxes.append([x, y, w, h])
            confidences.append(float(confidence))
            class_ids.append(class_id)

# Применение немаксимального подавления для уменьшения ложных срабатываний
indexes = cv2.dnn.NMSBoxes(boxes, confidences, 0.5, 0.4)

for i in range(len(boxes)):
    if i in indexes:
        x, y, w, h = boxes[i]
        label = str(class_ids[i])
        cv2.rectangle(image, (x, y), (x + w, y + h), (0, 255, 0), 2)
        cv2.putText(image, label, (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)

cv2.imshow("Image", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
Этот код демонстрирует загрузку предварительно обученной модели YOLOv3, обработку изображения и обнаружение объектов с последующим отображением результатов на изображении.