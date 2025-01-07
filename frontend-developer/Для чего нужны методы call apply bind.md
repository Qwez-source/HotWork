### Шанс вопроса: 3%

Методы `call`, `apply` и `bind` в JavaScript являются способами вызова функций с указанием значения `this`. Они полезны для управления контекстом выполнения функции.

1. **Метод `call`:**
   - Используется для вызова функции с указанным значением `this` и аргументами, переданными по отдельности.
   ```javascript
   function greet() {
     console.log(`Hello, ${this.name}!`);
   }

   const person = { name: 'Alice' };
   greet.call(person); // Выведет: Hello, Alice!
   ```

2. **Метод `apply`:**
   - Похож на метод `call`, но аргументы передаются как массив.
   ```javascript
   function greet(greeting) {
     console.log(`${greeting}, ${this.name}!`);
   }

   const person = { name: 'Alice' };
   greet.apply(person, ['Hello']); // Выведет: Hello, Alice!
   ```

3. **Метод `bind`:**
   - Возвращает новую функцию с указанным значением `this`, которая при вызове будет иметь этот контекст.
   ```javascript
   function greet() {
     console.log(`Hello, ${this.name}!`);
   }

   const person = { name: 'Alice' };
   const boundGreet = greet.bind(person);
   boundGreet(); // Выведет: Hello, Alice!
   ```

Эти методы позволяют напрямую изменять контекст выполнения функции и передавать аргументы в нужном формате.