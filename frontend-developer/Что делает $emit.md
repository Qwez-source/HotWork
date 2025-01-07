### Шанс вопроса: 6%

`$emit` в Vue.js используется для вызова событий от дочернего компонента к родительскому компоненту. Это позволяет создать двустороннюю связь между компонентами, где дочерний компонент может передавать данные или сигнализировать о событиях родительскому компоненту.

Пример использования:
```javascript
// Дочерний компонент (ChildComponent.vue)
export default {
  methods: {
    emitEvent() {
      this.$emit('custom-event', { message: 'Hello, Parent!' });
    }
  },
  template: `<button @click="emitEvent">Emit Event</button>`
}
```

В этом примере, когда пользователь нажимает кнопку в дочернем компоненте, вызывается метод `emitEvent`, который генерирует событие `custom-event` и передаёт объект с сообщением.

```javascript
// Родительский компонент (ParentComponent.vue)
export default {
  methods: {
    handleEvent(payload) {
      console.log('Received from child:', payload);
    }
  },
  template: `<child-component @custom-event="handleEvent"></child-component>`
}
```

В родительском компоненте мы слушаем событие `custom-event` и вызываем метод `handleEvent`, который обрабатывает полученные данные.