### Шанс вопроса: 3%

Observable — это объект, который может наблюдать за изменениями своего состояния или данных и уведомлять подписчиков (наблюдателей) о произошедших изменениях. В контексте фронтенд-разработки Observable часто используется в библиотеках для управления состоянием, таких как RxJS или Vuex.

Пример использования в библиотеке RxJS:
```javascript
import { Subject } from 'rxjs';

const observable = new Subject();

observable.subscribe(value => {
  console.log('Observer got a value of ' + value);
});

observable.next(1); // Observer got a value of 1
observable.next(2); // Observer got a value of 2
```

В этом примере `Subject` является объектом, который может передавать значения подписчикам. Когда мы вызываем `observable.next(value)`, все подписчики получают новое значение.

Использование в Vuex для управления состоянием:
```javascript
import { observable, observe } from 'mobx';

const state = observable({ count: 0 });

observe(state, change => {
  console.log('State changed:', change);
});

state.count++; // State changed: { name: "count", object: {...}, newValue: 1, oldValue: 0 }
```

В этом примере `observable` используется для создания наблюдаемого объекта `state`, который может отслеживать изменения своего состояния. При каждом изменении состояния вызывается функция-наблюдатель, которая будет выполнять определенные действия (в данном случае, просто логирует новое значение).

Таким образом, Observable — это мощный инструмент для управления состоянием и отслеживания изменений в приложениях фронтенд-разработки.