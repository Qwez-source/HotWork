### Шанс вопроса: 6%

Оператор spread (`...`) в JavaScript позволяет расширять элементы iterable (например, массивы или строки) в местах, где ожидаются отдельные аргументы. Это удобно для копирования массивов, объединения массивов, передачи аргументов функции и т.д.

**Пример использования оператора spread:**

1. **Копирование массива:**
   ```javascript
   const originalArray = [1, 2, 3];
   const copiedArray = [...originalArray];
   console.log(copiedArray); // Output: [1, 2, 3]
   ```

2. **Объединение массивов:**
   ```javascript
   const array1 = [1, 2, 3];
   const array2 = [4, 5, 6];
   const combinedArray = [...array1, ...array2];
   console.log(combinedArray); // Output: [1, 2, 3, 4, 5, 6]
   ```

3. **Передача аргументов функции:**
   ```javascript
   function sum(a, b, c) {
       return a + b + c;
   }
   
   const numbers = [1, 2, 3];
   console.log(sum(...numbers)); // Output: 6
   ```

4. **Создание нового объекта с расширением свойств:**
   ```javascript
   const obj1 = { a: 1, b: 2 };
   const obj2 = { b: 3, c: 4 };
   const mergedObj = { ...obj1, ...obj2 };
   console.log(mergedObj); // Output: { a: 1, b: 3, c: 4 }
   ```

Оператор spread упрощает работу с данными, делая код более чистым и читаемым.