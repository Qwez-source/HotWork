### Шанс вопроса: 3%

Наблюдатель (Observer) — это поведенческий паттерн проектирования, который позволяет объектам оповещать друг друга о своих изменениях. Он состоит из двух основных компонентов: субъекта (subject) и наблюдателей (observers). Субъект отслеживает своих наблюдателей и уведомляет их, когда происходит какое-либо событие.

**Пример реализации на Python:**

```python
class Subject:
    def __init__(self):
        self._observers = []
        self._state = None

    def add_observer(self, observer):
        self._observers.append(observer)

    def remove_observer(self, observer):
        self._observers.remove(observer)

    def notify_observers(self):
        for observer in self._observers:
            observer.update(self._state)

    def set_state(self, state):
        self._state = state
        self.notify_observers()

class Observer:
    def update(self, state):
        pass

class ConcreteObserver(Observer):
    def __init__(self, name):
        self._name = name

    def update(self, state):
        print(f"{self._name} received an update. New state: {state}")

# Создаем субъект
subject = Subject()

# Создаем наблюдателей
observer1 = ConcreteObserver("Observer 1")
observer2 = ConcreteObserver("Observer 2")

# Добавляем наблюдателей к субъекту
subject.add_observer(observer1)
subject.add_observer(observer2)

# Изменяем состояние субъекта и уведомляем наблюдателей
subject.set_state("State 1")
```

В этом примере:
- `Subject` представляет собой субъект, который может добавлять и удалять наблюдателей, а также уведомлять их о своих изменениях.
- `Observer` — это интерфейс для всех конкретных наблюдателей.
- `ConcreteObserver` — конкретная реализация наблюдателя, которая получает обновление при каждом вызове метода `update`.

Таким образом, Наблюдатель позволяет легко добавлять новые типы наблюдателей без изменения существующего кода субъекта.