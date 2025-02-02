### Шанс вопроса: 3%

Функция-стрелочка (arrow function) — это сокращенный синтаксис для определения функций в JavaScript. Она была введена в ES6 (ECMAScript 2015). В отличие от традиционных функций, функция-стрелочка не имеет своего контекста `this`, и ей не нужно использовать ключевое слово `function`.

**Синтаксис:**
```javascript
const myFunction = (arg1, arg2) => {
  // тело функции
};
```

**Основные особенности:**
1. **Контекст `this`:** Функции-стрелки не имеют своего контекста `this`. Вместо этого используется контекст `this` родительской функции или глобального объекта в зависимости от места вызова.
2. **Простота:** Функции-стрелки хорошо подходят для простых функций, особенно когда нужно передать анонимную функцию как аргумент или использовать в качестве callback'ов.
3. **Использование `this`:** Если вам нужен контекст `this` определенного объекта, вы можете использовать функции-стрелки внутри методов этого объекта или передать его через аргументы.

**Пример:**
```javascript
// Обычная функция
function classicFunction(arg) {
  console.log(this, arg);
}

// Функция-стрелочка
const arrowFunction = (arg) => {
  console.log(this, arg);
};

classicFunction('test'); // выведет глобальный объект и 'test'
arrowFunction('test');    // выведет глобальный объект и 'test'
```

**Преимущества:**
1. **Компактность:** Код становится более компактным, что улучшает читаемость при простых функциях.
2. **Явное возвращение:** Если тело функции состоит из одного выражения и нужно явно вернуть значение, синтаксис стрелки позволяет это сделать в более компактной форме.

**Пример использования:**
```javascript
const numbers = [1, 2, 3, 4];

// Использование функции-стрелочки для фильтрации массива
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // выведет [2, 4]
```

Функции-стрелки являются мощным инструментом в современном JavaScript и упрощают написание и чтение кода, особенно при работе с асинхронными операциями или функциями обратного вызова.