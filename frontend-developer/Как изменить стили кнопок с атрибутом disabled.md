### Шанс вопроса: 3%

Когда элемент кнопки имеет атрибут `disabled`, его стилизация может быть изменена с помощью CSS. Обычно браузеры применяют дефолтные стили для отключенных кнопок, но вы можете переопределить их, чтобы соответствовать вашему дизайну. Вот как это можно сделать:

1. **Использование псевдокласса `:disabled`**:
   CSS предоставляет псевдокласс `:disabled`, который позволяет стилизовать отключенные элементы. Вы можете использовать его для изменения стилей кнопки при её состоянии `disabled`.

   ```css
   button[disabled] {
       background-color: gray;
       color: #ccc;
       border-color: #999;
   }
   ```

2. **Использование JavaScript для изменения стилей**:
   Если вам нужно динамически изменить стили кнопки при её состоянии `disabled`, вы можете использовать JavaScript. Это может быть полезно, если состояние зависит от какого-то условия в приложении.

   ```javascript
   const button = document.querySelector('button[type="submit"]');
   button.disabled = true; // Устанавливаем кнопку в состояние disabled

   // Изменяем стили с помощью JavaScript
   function updateButtonStyle() {
       if (button.disabled) {
           button.style.backgroundColor = 'gray';
           button.style.color = '#ccc';
           button.style.borderColor = '#999';
       } else {
           // Возвращаем исходные стили при необходимости
           button.style.backgroundColor = '';
           button.style.color = '';
           button.style.borderColor = '';
       }
   }

   updateButtonStyle(); // Вызов функции при каждом изменении состояния кнопки
   ```

Эти методы позволяют вам управлять стилями для отключенных кнопок, обеспечивая гибкость в зависимости от требований проекта и дизайна.