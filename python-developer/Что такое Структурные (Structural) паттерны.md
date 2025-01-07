### Шанс вопроса: 3%

Структурные паттерны проектирования программного обеспечения предназначены для определения простых способов организации классов, объектов и взаимодействий между ними. Они фокусируются на том, как компоненты системы собираются в более крупные структуры, чтобы улучшить гибкость и простоту расширения. Вот несколько примеров таких паттернов:

1. **Декоратор (Decorator)**: Этот паттерн позволяет добавлять новую функциональность к объектам динамически, без изменения их основного кода. Он использует композицию вместо наследования для расширения функциональности.

   ```python
   from abc import ABC, abstractmethod

   class Component(ABC):
       @abstractmethod
       def operation(self):
           pass

   class ConcreteComponent(Component):
       def operation(self):
           return "ConcreteComponent"

   class Decorator(Component):
       def __init__(self, component: Component):
           self._component = component

       def operation(self):
           return f"Decorated {self._component.operation()}"

   # Использование
   simple_component = ConcreteComponent()
   decorated_component = Decorator(simple_component)
   print(decorated_component.operation())  # Вывод: "Decorated ConcreteComponent"
   ```

2. **Фасад (Facade)**: Паттерн Facade предоставляет простой интерфейс к сложной системе классов, библиотеке или фреймворку. Он скрывает сложность системы, предоставляя упрощенный API.

   ```python
   class SubsystemA:
       def operation_a(self):
           return "Subsystem A method"

   class SubsystemB:
       def operation_b(self):
           return "Subsystem B method"

   class Facade:
       def __init__(self, subsystem_a: SubsystemA, subsystem_b: SubsystemB):
           self._subsystem_a = subsystem_a
           self._subsystem_b = subsystem_b

       def operation(self):
           results = []
           results.append(self._subsystem_a.operation_a())
           results.append(self._subsystem_b.operation_b())
           return "\n".join(results)

   # Использование
   facade = Facade(SubsystemA(), SubsystemB())
   print(facade.operation())  # Вывод: "Subsystem A method\nSubsystem B method"
   ```

3. **Приспособленец (Adapter)**: Паттерн Adapter позволяет объектам с несовместимыми интерфейсами работать вместе, преобразуя интерфейс одного класса в интерфейс другого.

   ```python
   class Target:
       def request(self):
           return "Target request"

   class Adaptee:
       def specific_request(self):
           return ".adaptee's specific request"

   class Adapter(Target):
       def __init__(self, adaptee: Adaptee):
           self._adaptee = adaptee

       def request(self):
           return f"Adapter: {self._adaptee.specific_request()}"

   # Использование
   adaptee = Adaptee()
   adapter = Adapter(adaptee)
   print(adapter.request())  # Вывод: "Adapter: .adaptee's specific request"
   ```

Эти примеры иллюстрируют, как структурные паттерны могут помочь в проектировании гибких и расширяемых систем.