### Шанс вопроса: 6%

Z-index — это CSS-свойство, которое определяет порядок наложения (z-порядок) элементов друг над другом. Это свойство работает только с элементами, у которых задано положение position со значением отличным от static (по умолчанию). Значения z-index могут быть целыми числами, причем большие значения будут накладываться поверх меньших. Если два элемента имеют одинаковый z-index, то порядок их наложения определяется HTML-кодом: последний в коде будет выше предыдущего.

Пример использования:
```css
.element1 {
  position: absolute;
  z-index: 2;
}

.element2 {
  position: relative;
  z-index: 1;
}
```
В этом примере элемент с `z-index: 2` будет отображаться поверх элемента с `z-index: 1`, даже если первый элемент находится ниже по коду.