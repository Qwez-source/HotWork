### Шанс вопроса: 3%

Да, drag and drop является частью стандарта W3C HTML5. Он определяет интерфейс API для перетаскивания объектов по графическому пользовательскому интерфейсу (GUI). Это позволяет пользователям перетаскивать элементы с одного места на другое в пределах веб-приложения или между приложениями.

Основные компоненты drag and drop включают:
1. **Перетаскиваемый элемент (Draggable Element)**: Это элемент, который пользователь может перетащить. Для создания перетаскиваемого элемента используется атрибут `draggable="true"` или JavaScript-событие `dragstart`.
2. **Область приёмника (Drop Zone)**: Это область, в которую пользователь может перетащить элемент. Она реагирует на события `dragover` и `drop`.

Пример HTML для создания перетаскиваемого элемента:
```html
<div id="draggable" draggable="true">Drag me!</div>
```

События, связанные с drag and drop:
- **dragstart**: Срабатывает, когда пользователь начинает перетаскивать элемент.
- **dragover**: Срабатывает, когда перетаскиваемый элемент находится над областью приемника.
- **drop**: Срабатывает, когда элемент отпускается в области приемника.

Пример обработки событий:
```javascript
document.getElementById('draggable').addEventListener('dragstart', function(event) {
  event.dataTransfer.setData("text", event.target.id);
});

document.getElementById('dropZone').addEventListener('dragover', function(event) {
  event.preventDefault();
});

document.getElementById('dropZone').addEventListener('drop', function(event) {
  event.preventDefault();
  var data = event.dataTransfer.getData("text");
  document.getElementById(data).style.left = (event.clientX - 25) + "px";
  document.getElementById(data).style.top = (event.clientY - 25) + "px";
});
```

Этот код создает перетаскиваемый элемент и область приемника, где можно отпустить перетаскиваемый элемент.