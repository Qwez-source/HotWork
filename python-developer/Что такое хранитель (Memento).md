### Шанс вопроса: 3%

Хранитель (Memento) — это паттерн проектирования, который позволяет сохранять и восстанавливать предыдущие состояния объекта, не нарушая принцип инкапсуляции. Он используется для реализации механизма снимков состояния объекта.

### Основные компоненты:
1. **Originator**: Класс, который создаёт и может возвращать свой текущий состояние через Memento.
2. **Memento**: Простой класс данных для хранения состояния объекта Originator.
3. **Caretaker**: Класс, который отвечает за хранение и управление Memento.

### Пример на Python:

```python
class Memento:
    def __init__(self, state):
        self._state = state

    def get_state(self):
        return self._state

class Originator:
    def __init__(self, state):
        self._state = state

    def get_state(self):
        return self._state

    def set_state(self, state):
        self._state = state

    def save_state_to_memento(self):
        return Memento(self._state)

    def restore_state_from_memento(self, memento):
        self._state = memento.get_state()

class Caretaker:
    def __init__(self, originator):
        self._mementos = []
        self._originator = originator

    def backup(self):
        self._mementos.append(self._originator.save_state_to_memento())

    def undo(self):
        if len(self._mementos) > 0:
            memento = self._mementos.pop()
            self._originator.restore_state_from_memento(memento)

# Пример использования
originator = Originator("State1")
caretaker = Caretaker(originator)

print(f"Current State: {originator.get_state()}")  # Current State: State1

# Сохраняем состояние
caretaker.backup()

# Изменяем состояние
originator.set_state("State2")
print(f"Changed State: {originator.get_state()}")  # Changed State: State2

# Восстанавливаем предыдущее состояние
caretaker.undo()
print(f"Restored State: {originator.get_state()}")  # Restored State: State1
```

### Особенности:
- **Хранение состояния**: Memento позволяет хранить состояние объекта в момент времени, что может быть полезно для реализации отмены операций или возврата к предыдущему состоянию.
- **Инкапсуляция**: Состояние объекта хранится внутри Memento и доступ к нему ограничен, что обеспечивает инкапсуляцию.
- **Восстановление состояния**: Объект Originator может восстановить своё состояние из Memento, даже если это состояние было создано другим объектом.

Этот паттерн полезен в ситуациях, когда необходимо предоставить механизм для фиксации и возврата состояния объекта без нарушения его инкапсуляции.