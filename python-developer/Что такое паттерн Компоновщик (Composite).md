### Шанс вопроса: 3%

Паттерн Компоновщик (Composite) — это структурный паттерн проектирования, который позволяет создавать древовидные структуры и работать с ними как с единой структурой. Он используется для представления части-целого отношения между объектами. В Python этот паттерн можно реализовать, определив общий интерфейс для компонентов, которые могут быть как простыми, так и сложными (содержащими другие компоненты).

### Пример реализации в Python

Предположим, у нас есть иерархия объектов, которые могут быть как простыми (листья), так и сложными (композитные объекты).

```python
from abc import ABC, abstractmethod

# Базовый компонент
class Component(ABC):
    @abstractmethod
    def operation(self):
        pass

# Листья
class Leaf(Component):
    def __init__(self, name):
        self.name = name

    def operation(self):
        return f"Leaf {self.name}"

# Компоненты, которые могут содержать другие компоненты
class Composite(Component):
    def __init__(self, name):
        self.name = name
        self.children = []

    def add(self, component: 'Component'):
        self.children.append(component)

    def remove(self, component: 'Component'):
        self.children.remove(component)

    def operation(self):
        results = [child.operation() for child in self.children]
        return f"Composite {self.name} with children: [{', '.join(results)}]"

# Клиентский код
def client_code(component: Component):
    print(component.operation())

# Создание компонентов
leaf1 = Leaf("Leaf 1")
leaf2 = Leaf("Leaf 2")
composite1 = Composite("Composite 1")
composite2 = Composite("Composite 2")

# Строение иерархии
composite1.add(leaf1)
composite1.add(leaf2)
composite2.add(composite1)

# Клиентский код для выполнения операций
client_code(leaf1)
client_code(composite2)
```

### Вывод
В этом примере:
- `Component` — базовый интерфейс, который определяет метод `operation`.
- `Leaf` — простой компонент, представляющий отдельный объект.
- `Composite` — сложный компонент, который может содержать другие компоненты.

Клиентский код выполняет операции над компонентами через общий интерфейс, что позволяет работать как с простыми, так и со сложными объектами в едином стиле.