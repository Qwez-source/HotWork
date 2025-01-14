### Шанс вопроса: 10%

Контекст в JavaScript относится к окружению, в котором выполняется код. Он определяет доступные переменные и функции, а также значения `this` и `arguments`. Существуют два основных типа контекста:

1. **Глобальный контекст**: Это верхний уровень контекста, в котором выполняется весь код, если он не внутри функции или блока. В глобальном контексте `this` ссылается на глобальный объект (например, `window` в браузере).

2. **Функциональный контекст**: Каждый раз, когда вызывается функция, создаётся новый функциональный контекст исполнения. Внутри функции `this` может иметь различные значения в зависимости от того, как функция была вызвана:
   - **Строгий режим**: Если код запущен в строгом режиме (`'use strict';`), `this` внутри функции будет `undefined`, если не привязан к объекту явно.
   - **Нестрогий режим**: В нестрогом режиме, если вызов происходит без контекста (например, через `call`, `apply` или `bind`), `this` будет ссылаться на глобальный объект.

Пример использования:
```javascript
// Глобальный контекст
console.log(this); // В браузере это будет window

function myFunction() {
  console.log(this); // В нестрогом режиме this будет window, в строгом режиме undefined
}
myFunction();
```

3. **Контекст выполнения**: Это внутренний механизм JavaScript, который управляет выполнением кода и определяет переменные и функции, доступные в текущей области видимости. Контекст выполнения включает `this`, локальные переменные и функции, а также цепочку областей видимости (Лексическое окружение).

Пример использования:
```javascript
function outerFunction() {
  const outerVar = 'Hello';
  function innerFunction() {
    console.log(outerVar); // Доступ к переменной из внешней функции
    console.log(this); // this в строгом режиме будет undefined, в нестрогом режиме window
  }
  innerFunction();
}
outerFunction();
```

В целом, контекст важен для понимания того, как работает `this` и как доступны переменные и функции в различных ситуациях.