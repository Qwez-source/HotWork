### Шанс вопроса: 3%

Паттерн Приспособленец (Flyweight) — это структурный паттерн проектирования, который позволяет вместить большое количество объектов в ограниченную память, используя разделяние и повторное использование общего состояния. Паттерн Flyweight полезен для эффективного управления ресурсами приложения, особенно когда приложение работает с большим количеством объектов, которые могут быть упрощены за счет разделения общего состояния.

### Основные компоненты паттерна Flyweight:
1. **Flyweight**: Это интерфейс или абстрактный класс, представляющий объект, который может быть разделяемым. Он содержит операции, через которые могут передаваться внешние состояния.
2. **ConcreteFlyweight**: Реализация интерфейса Flyweight, представляющая конкретный объект, который может быть разделяемым. Он хранит внутреннее состояние, которое не меняется.
3. **FlyweightFactory**: Создаёт и управляет Flyweight'ами. Он гарантирует, что Flyweight's уникальны или разделяемы, и возвращает кэшированные экземпляры Flyweight's.
4. **Client**: Клиент использует объекты Flyweight через интерфейс, не зная о том, что они могут быть разделяемыми.

### Пример на Python:
```python
from typing import Protocol

class Flyweight(Protocol):
    def operation(self, extrinsic_state: str) -> None:
        ...

class ConcreteFlyweight(Flyweight):
    def __init__(self, intrinsic_state: str) -> None:
        self._intrinsic_state = intrinsic_state

    def operation(self, extrinsic_state: str) -> None:
        print(f"ConcreteFlyweight: Intrinsic State = {self._intrinsic_state}, Extrinsic State = {extrinsic_state}")

class FlyweightFactory:
    _flyweights: dict[str, Flyweight] = {}

    def __init__(self, states: list[tuple[str, str]]) -> None:
        for state in states:
            self._flyweights[self.get_key(state)] = ConcreteFlyweight(state[0])

    @staticmethod
    def get_key(state: tuple[str, str]) -> str:
        return "_".join(sorted(state))

    def get_flyweight(self, state: tuple[str, str]) -> Flyweight:
        key = self.get_key(state)
        if not self._flyweights.get(key):
            print("Creating new ConcreteFlyweight")
            self._flyweights[key] = ConcreteFlyweight(state[0])
        return self._flyweights[key]

# Клиентский код
def client_code() -> None:
    factory = FlyweightFactory([("shared1", "unique1"), ("shared2", "unique2")])

    flyweight1 = factory.get_flyweight(("shared1", "unique1"))
    flyweight1.operation("Extrinsic State 1")

    flyweight2 = factory.get_flyweight(("shared2", "unique2"))
    flyweight2.operation("Extrinsic State 2")

if __name__ == "__main__":
    client_code()
```

### Применение:
Паттерн Flyweight полезен в играх, где может быть много однотипных объектов (например, частиц в игре), или в приложениях с большим количеством графических элементов, которые могут быть упрощены за счет разделения общего состояния.

### Преимущества:
1. **Экономия памяти**: Позволяет эффективно управлять большим количеством объектов, разделяя их общее состояние.
2. **Улучшение производительности**: Сокращает время выделения и освобождения памяти для объектов.

### Недостатки:
1. **Сложность реализации**: Может быть сложно реализовать, особенно когда объекты имеют много состояний.
2. **Усложнение кода**: Добавление дополнительных классов и интерфейсов может сделать код более запутанным.

### Заключение:
Паттерн Flyweight — мощное средство для оптимизации ресурсов в приложениях, особенно когда речь идет об управлении большим количеством объектов с общими свойствами.