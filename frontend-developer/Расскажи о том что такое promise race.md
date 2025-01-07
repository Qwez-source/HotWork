### Шанс вопроса: 3%

Promise.race() — это метод JavaScript, который принимает массив промисов (promises) и возвращает новый промис. Этот новый промис выполняется или отклоняется с результатом первого завершенного (выполненного или отклоненного) промиса в переданном массиве.

Пример использования:
```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 500, 'First');
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(reject, 100, 'Second');
});

Promise.race([promise1, promise2]).then((value) => {
  console.log('Promise.race:', value); // Выполнится с результатом 'Second' (первый отклоненный промис)
}).catch((error) => {
  console.log('Promise.race Error:', error);
});
```
В этом примере, `promise1` выполняется через 500 миллисекунд, а `promise2` отклоняется через 100 миллисекунд. Метод `Promise.race([promise1, promise2])` вернет новый промис, который будет выполнен или отклонен с результатом первого завершенного промиса в массиве. В данном случае это будет `promise2`, так как она быстрее отклоняется, и её результат (или ошибка) будет передан обработчику.