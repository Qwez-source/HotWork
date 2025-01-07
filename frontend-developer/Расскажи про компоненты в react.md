### Шанс вопроса: 6%

Компоненты являются основой построения пользовательских интерфейсов в React. Они позволяют разделять интерфейс на независимые, переиспользуемые части. Вот основные аспекты компонентов в React:

1. **Определение компонента**: Компонент может быть определен как функция или класс, который возвращает JSX (JavaScript XML). Функциональные компоненты используются чаще и проще в реактивном стиле работы с состояниями.

   ```jsx
   // Функциональный компонент
   function MyComponent(props) {
     return <div>Hello, {props.name}!</div>;
   }

   // Классовый компонент
   class MyComponent extends React.Component {
     render() {
       return <div>Hello, {this.props.name}!</div>;
     }
   }
   ```

2. **Использование пропсов**: Пропсы (props) — это объект, который содержит данные, передаваемые компоненту. Они используются для передачи информации от родительского компонента к дочернему.

   ```jsx
   function Greeting(props) {
     return <h1>Hello, {props.name}!</h1>;
   }

   // Использование компонента с пропсами
   ReactDOM.render(<Greeting name="John" />, document.getElementById('root'));
   ```

3. **Состояние**: В функциональных компонентах состояние (state) управляется с помощью хуков, таких как `useState`. Состояние позволяет компоненту реагировать на события и изменять свое поведение.

   ```jsx
   import React, { useState } from 'react';

   function Counter() {
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

4. **Жизненный цикл компонента**: В классовых компонентах жизненный цикл включает методы `componentDidMount`, `componentDidUpdate` и `componentWillUnmount`. В функциональных компонентах с помощью хуков можно имитировать некоторые из этих методов.

   ```jsx
   import React, { useEffect, useState } from 'react';

   function DataLoader() {
     const [data, setData] = useState(null);

     useEffect(() => {
       fetch('https://api.example.com/data')
         .then(response => response.json())
         .then(data => setData(data));
     }, []); // Пустой массив зависимостей означает, что эффект выполняется только при монтировании

     if (!data) return <div>Loading...</div>;

     return (
       <div>
         <h1>{data.title}</h1>
         <p>{data.content}</p>
       </div>
     );
   }
   ```

5. **Композиция компонентов**: Компоненты могут включать другие компоненты, что позволяет создавать сложные пользовательские интерфейсы из простых блоков.

   ```jsx
   function UserInfo({ user }) {
     return (
       <div>
         <h1>{user.name}</h1>
         <p>{user.bio}</p>
       </div>
     );
   }

   function UserCard({ userId }) {
     const [user, setUser] = useState(null);

     useEffect(() => {
       fetch(`https://api.example.com/users/${userId}`)
         .then(response => response.json())
         .then(data => setUser(data));
     }, [userId]);

     if (!user) return <div>Loading...</div>;

     return (
       <div>
         <UserInfo user={user} />
       </div>
     );
   }
   ```

Эти основные аспекты помогают понять, как компоненты используются в React для создания динамических и интерактивных пользовательских интерфейсов.