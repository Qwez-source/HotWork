### Шанс вопроса: 13%

В разработке фронтенд-приложений можно использовать множество хуков, которые предоставляют React для управления состояниями и жизненным циклом компонентов. Некоторые из часто используемых хуков включают:

1. **useState**: Используется для добавления состояния в функциональные компоненты.
   ```javascript
   import React, { useState } from 'react';

   function Example() {
     const [count, setCount] = useState(0);

     return (
       <div>
         <p>You clicked {count} times</p>
         <button onClick={() => setCount(count + 1)}>
           Click me
         </button>
       </div>
     );
   }
   ```

2. **useEffect**: Используется для выполнения побочных эффектов, таких как получение данных или подписка на изменения.
   ```javascript
   import React, { useEffect, useState } from 'react';

   function DataFetchingComponent() {
     const [data, setData] = useState(null);

     useEffect(() => {
       fetch('https://api.example.com/data')
         .then(response => response.json())
         .then(data => setData(data));
     }, []); // Пустой массив зависимостей означает, что эффект выполняется только один раз при монтировании компонента

     return (
       <div>
         {data ? <p>{data}</p> : <p>Loading...</p>}
       </div>
     );
   }
   ```

3. **useContext**: Используется для чтения и подписки на контекст (Context API).
   ```javascript
   import React, { useContext, useState } from 'react';

   const MyContext = React.createContext();

   function App() {
     const [value, setValue] = useState('Hello, World!');

     return (
       <MyContext.Provider value={value}>
         <ChildComponent />
       </MyContext.Provider>
     );
   }

   function ChildComponent() {
     const value = useContext(MyContext);
     return <p>{value}</p>;
   }
   ```

4. **useReducer**: Используется для управления более сложным состоянием с использованием редюсера (reducer).
   ```javascript
   import React, { useReducer } from 'react';

   const initialState = { count: 0 };

   function reducer(state, action) {
     switch (action.type) {
       case 'increment':
         return { count: state.count + 1 };
       case 'decrement':
         return { count: state.count - 1 };
       default:
         throw new Error();
     }
   }

   function Counter() {
     const [state, dispatch] = useReducer(reducer, initialState);

     return (
       <>
         Count: {state.count}
         <button onClick={() => dispatch({ type: 'increment' })}>+</button>
         <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
       </>
     );
   }
   ```

5. **useRef**: Используется для сохранения значений, которые не нужно перерендерировать при каждом рендере компонента.
   ```javascript
   import React, { useRef } from 'react';

   function FocusInput() {
     const inputRef = useRef(null);

     const handleClick = () => {
       inputRef.current.focus();
     };

     return (
       <>
         <input ref={inputRef} type="text" />
         <button onClick={handleClick}>Focus Input</button>
       </>
     );
   }
   ```

Эти хуки помогают управлять состояниями и выполнять побочные эффекты в функциональных компонентах, что делает код более чистым и легко читаемым.