### Шанс вопроса: 10%

Props — это аргументы, передаваемые в компонент React при его создании. Они позволяют передавать данные от родительского компонента к дочернему, делая компоненты более гибкими и переиспользуемыми. Вот основные моменты о props:

1. **Передача Props**: Компонент может принимать пропсы через параметры функции или в виде атрибутов JSX при вызове компонента. Например:
   ```jsx
   function Welcome(props) {
     return <h1>Привет, {props.name}!</h1>;
   }

   // Вызов компонента с пропсами
   ReactDOM.render(<Welcome name="Мир" />, document.getElementById('root'));
   ```

2. **Чтение Props**: Дочерний компонент может читать переданные ему props через `this.props` или `props` в функциональных компонентах. Например:
   ```jsx
   function Greeting(props) {
     return <p>Привет, {props.name}!</p>;
   }

   // Вызов компонента с пропсами
   ReactDOM.render(<Greeting name="Мир" />, document.getElementById('root'));
   ```

3. **Деструктуризация Props**: Для упрощения доступа к отдельным props можно использовать деструктуризацию объекта:
   ```jsx
   function Greeting({ name }) {
     return <p>Привет, {name}!</p>;
   }

   // Вызов компонента с пропсами
   ReactDOM.render(<Greeting name="Мир" />, document.getElementById('root'));
   ```

4. **Проверка Типов Props**: Для улучшения безопасности и ясности кода можно использовать библиотеки для проверки типов данных, такие как PropTypes в React:
   ```jsx
   import PropTypes from 'prop-types';

   function Greeting(props) {
     return <p>Привет, {props.name}!</p>;
   }

   Greeting.propTypes = {
     name: PropTypes.string.isRequired,
   };
   ```

5. **Пропсы по умолчанию**: Для предотвращения ошибок при отсутствии пропсов можно задать значения по умолчанию:
   ```jsx
   function Greeting({ name = 'Гость' }) {
     return <p>Привет, {name}!</p>;
   }
   ```

Использование props делает компоненты более универсальными и позволяет легко управлять данными между различными частями приложения.