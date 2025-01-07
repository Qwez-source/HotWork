### Шанс вопроса: 3%

Методы запрета обтекания (clearing) в CSS включают:

1. **clear: none** - По умолчанию это свойство не запрещает обтекание. Оно позволяет элементам обоих типов (левый и правый) располагаться по обе стороны от флоатинг-элементов.

2. **clear: left** - Запрещает обтекание элемента справа, позволяя только элементам слева располагаться ниже него при наличии флоатинга.

3. **clear: right** - Запрещает обтекание элемента слева, позволяя только элементам справа располагаться ниже него при наличии флоатинга.

4. **clear: both** - Запрещает обтекание как справа, так и слева, обеспечивая размещение всех последующих элементов только ниже предыдущего элемента при наличии флоатинга.

Пример использования:
```css
/* Пример с clear: left */
.container {
  border: 1px solid black;
}

.float-left {
  float: left;
  width: 200px;
  height: 200px;
  background-color: lightblue;
}

.clear-left {
  clear: left;
  background-color: lightgreen;
}
```

В этом примере `.float-left` будет обтекаться влево, а `.clear-left`, имеющий `clear: left`, не сможет разместиться ниже него и останется на том же уровне.

```css
/* Пример с clear: right */
.container {
  border: 1px solid black;
}

.float-right {
  float: right;
  width: 200px;
  height: 200px;
  background-color: lightblue;
}

.clear-right {
  clear: right;
  background-color: lightgreen;
}
```

В этом примере `.float-right` будет обтекаться вправо, а `.clear-right`, имеющий `clear: right`, не сможет разместиться ниже него и останется на том же уровне.

```css
/* Пример с clear: both */
.container {
  border: 1px solid black;
}

.float-both {
  float: left;
  width: 200px;
  height: 200px;
  background-color: lightblue;
}

.clear-both {
  clear: both;
  background-color: lightgreen;
}
```

В этом примере `.float-both` будет обтекаться влево, а `.clear-both`, имеющий `clear: both`, не сможет разместиться ниже него и останется на том же уровне.