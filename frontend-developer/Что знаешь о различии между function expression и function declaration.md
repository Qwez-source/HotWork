### Шанс вопроса: 20%

Function Expression и Function Declaration - это два основных способа определения функций в JavaScript. Вот основные различия между ними:

1. **Определение:**
   - **Function Declaration** (объявление функции) выглядит так:
     ```javascript
     function myFunc() {
       console.log('Hello!');
     }
     ```
     Она может быть определена в основном потоке кода, даже до того, как она будет вызвана.
   - **Function Expression** (выражение функции) выглядит так:
     ```javascript
     const myFunc = function() {
       console.log('Hello!');
     };
     ```
     Здесь функция определена как часть более крупного выражения, например, присваивание переменной или аргумент другой функции.

2. **Образование:**
   - **Function Declaration** может быть вызвана раньше, чем она определена в коде, потому что движок JavaScript поднимает (hoists) объявления функций в верхнюю часть их области видимости.
     ```javascript
     console.log(myFunc()); // 'Hello!'
     function myFunc() {
       return 'Hello!';
     }
     ```
   - **Function Expression** не может быть вызвана до его присваивания, так как оно обрабатывается во время выполнения:
     ```javascript
     console.log(myFunc()); // Error: myFunc is not a function
     const myFunc = function() {
       return 'Hello!';
     };
     ```

3. **Область видимости:**
   - **Function Declaration** доступна в пределах всей функции, в которой она определена (включая тело функции и её предков), а также в любом месте после своего определения:
     ```javascript
     function outerFunc() {
       function innerFunc() {
         console.log('Hello from inner!');
       }
       innerFunc(); // 'Hello from inner!'
     }
     outerFunc();
     innerFunc(); // Error: innerFunc is not defined
     ```
   - **Function Expression** доступна только в пределах блока, в котором она определена:
     ```javascript
     function executeExpression() {
       const localVar = 'local';
       myFunc(); // Error: myFunc is not defined
       if (true) {
         const myFunc = function() {
           console.log('Hello from expression!');
         };
         myFunc(); // 'Hello from expression!'
       }
     }
     ```

4. **Использование:**
   - **Function Declaration** часто используется для объявления функций, которые будут вызываться в различных частях кода.
   - **Function Expression** предпочтительнее применять тогда, когда функция нужна только локально или является частью более крупного выражения (например, присваивание переменной).

Понимание этих различий помогает в написании более эффективного и читаемого кода, а также правильном использовании функций в зависимости от контекста.