### Шанс вопроса: 20%

В приложении React лучше всего хранить состояние в компоненте, если это возможно. Использование локального состояния (state) в компоненте позволяет управлять данными и поведением внутри самого компонента, что упрощает управление и отладку приложения. Однако, когда состояние становится сложным или требует общего доступа к нему в разных частях приложения, лучше использовать глобальное состояние с помощью библиотеки управления состоянием, такой как Redux или Context API.

### Пример использования локального состояния в компоненте React:
```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Current count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;
```
В этом примере состояние `count` хранится в компоненте `Counter`, и изменение его происходит через функцию `setCount`.

### Пример использования Redux для глобального состояния:
```javascript
import { createStore } from 'redux';

// Action types
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

// Action creators
function increment() {
  return { type: INCREMENT };
}

function decrement() {
  return { type: DECREMENT };
}

// Reducer
function counterReducer(state = { count: 0 }, action) {
  switch (action.type) {
    case INCREMENT:
      return { count: state.count + 1 };
    case DECREMENT:
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// Store
const store = createStore(counterReducer);

export default store;
```
В этом примере состояние управляется через Redux, где глобальное дерево reducer-ов может быть использовано для хранения и изменения состояния в разных частях приложения.

### Использование Context API:
```javascript
import React, { createContext, useReducer } from 'react';

// Initial state
const initialState = { count: 0 };

// Action types
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

// Reducer
function counterReducer(state, action) {
  switch (action.type) {
    case INCREMENT:
      return { count: state.count + 1 };
    case DECREMENT:
      return { count: state.count - 1 };
    default:
      return state;
  }
}

// Context
const CounterContext = createContext();

function CounterProvider({ children }) {
  const [state, dispatch] = useReducer(counterReducer, initialState);

  return (
    <CounterContext.Provider value={{ state, dispatch }}>
      {children}
    </CounterContext.Provider>
  );
}

// Component using context
function Counter() {
  const { state, dispatch } = React.useContext(CounterContext);

  return (
    <div>
      <p>Current count: {state.count}</p>
      <button onClick={() => dispatch({ type: INCREMENT })}>Increment</button>
      <button onClick={() => dispatch({ type: DECREMENT })}>Decrement</button>
    </div>
  );
}

export default Counter;
```
В этом примере используется Context API для создания глобального контекста, который может быть доступен всему приложению или его частям.