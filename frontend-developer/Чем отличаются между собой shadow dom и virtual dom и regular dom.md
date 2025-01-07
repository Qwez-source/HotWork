### Шанс вопроса: 3%

Shadow DOM, Virtual DOM и Regular DOM - это три различных подхода к управлению структурой и представлением веб-страниц в JavaScript. Вот основные отличия между ними:

1. **Regular DOM**:
   - **Определение**: Обычное DOM (Document Object Model) является интерфейсом для HTML, который позволяет программно манипулировать содержимым веб-страницы.
   - **Пример использования**: Изменение стилей элемента на странице:
     ```javascript
     document.getElementById('myElement').style.color = 'red';
     ```

2. **Shadow DOM**:
   - **Определение**: Shadow DOM — это изолированное поддерево документа, которое существует внутри обычного DOM. Оно создаётся с помощью метода `attachShadow` в веб-компонентах или при использовании специальных атрибутов (например, `<video>` элемент).
   - **Пример использования**: Создание и использование веб-компонента с Shadow DOM:
     ```javascript
     class MyCustomElement extends HTMLElement {
       constructor() {
         super();
         const shadow = this.attachShadow({mode: 'open'});
         shadow.innerHTML = `<p>Hello, Shadow DOM!</p>`;
       }
     }
     customElements.define('my-custom-element', MyCustomElement);
     ```

3. **Virtual DOM**:
   - **Определение**: Virtual DOM — это концепция, в которой существует виртуальное представление реального DOM. Изменения в приложении производятся не напрямую в DOM, а сначала в виртуальном дереве, затем разница между старым и новым виртуальным деревом сравнивается, и только те изменения, которые произошли, применяются к реальному DOM.
   - **Пример использования**: Использование библиотеки React для управления виртуальным DOM:
     ```javascript
     class MyComponent extends React.Component {
       constructor(props) {
         super(props);
         this.state = { color: 'red' };
       }
       render() {
         return <div style={{ color: this.state.color }}>Hello, Virtual DOM!</div>;
       }
     }
     ```

**Основные отличия**:
- **Shadow DOM** изолирует компоненты и предоставляет API для доступа к его частицам.
- **Virtual DOM** используется в фреймворках (например, React) для оптимизации обновлений реального DOM.
- **Regular DOM** — это базовый интерфейс для манипуляций с HTML-элементами на странице.

Эти технологии помогают в разработке фронтенд-приложений, обеспечивая гибкость и производительность при работе с DOM.