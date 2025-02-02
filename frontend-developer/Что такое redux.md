### Шанс вопроса: 6%

Redux — это контейнер управления состоянием для приложений JavaScript, который использует однонаправленный поток данных. Он помогает управлять состоянием вашего приложения и обеспечивает предсказуемое управление изменениями состояния через действия (actions) и редьюсеры (reducers).

Основные компоненты Redux включают:
1. **Store**: Хранилище, которое содержит всё состояние приложения.
2. **Actions**: Объекты, описывающие события, происходящие в приложении.
3. **Reducers**: Функции, которые обрабатывают действия и изменяют состояние.

Пример использования Redux:
```javascript
// Действие (Action)
const increment = {
  type: 'INCREMENT'
};

// Редьюсер (Reducer)
const counterReducer = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    default:
      return state;
  }
};

// Хранилище (Store)
import { createStore } from 'redux';
const store = createStore(counterReducer);

// Диспатч действия для изменения состояния
store.dispatch(increment); // Теперь состояние равно 1
```

Это базовый пример, демонстрирующий как создать простейшее хранилище с использованием Redux для управления счетчиком.