### Шанс вопроса: 3%

Data атрибуты в HTML предназначены для хранения данных, которые могут быть использованы JavaScript. Они позволяют привязывать произвольные данные к элементам HTML без нарушения чистоты DOM. Это особенно полезно для хранения информации, которая будет использоваться в клиентских скриптах, таких как идентификаторы, метаданные или другие данные, не относящиеся к содержимому страницы.

Пример использования data атрибутов:
```html
<div id="myElement" data-custom-attribute="someValue">
  Этот элемент содержит произвольные данные.
</div>
```
В JavaScript вы можете получить доступ к значению атрибута `data-custom-attribute` следующим образом:
```javascript
const element = document.getElementById('myElement');
const customAttribute = element.getAttribute('data-custom-attribute');
console.log(customAttribute); // Выведет: someValue
```
Таким образом, data атрибуты обеспечивают удобный способ хранения и доступа к произвольным данным в HTML-элементах.