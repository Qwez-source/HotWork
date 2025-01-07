### Шанс вопроса: 13%

Singleton — это порождающий паттерн проектирования, который гарантирует, что у класса есть только один экземпляр, и предоставляет глобальную точку доступа к этому экземпляру. В Python это можно реализовать несколькими способами.

### Способ 1: Использование статического метода
```python
class Singleton:
    _instance = None

    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = super(Singleton, cls).__new__(cls, *args, **kwargs)
        return cls._instance

# Пример использования
s1 = Singleton()
s2 = Singleton()
print(s1 is s2)  # Вывод: True
```

### Способ 2: Использование декоратора
```python
def singleton(cls):
    instances = {}

    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]

    return get_instance

@singleton
class SingletonClass:
    pass

# Пример использования
s1 = SingletonClass()
s2 = SingletonClass()
print(s1 is s2)  # Вывод: True
```

### Способ 3: Использование метакласса
```python
class MetaSingleton(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(MetaSingleton, cls).__call__(*args, **kwargs)
        return cls._instances[cls]

class Singleton(metaclass=MetaSingleton):
    pass

# Пример использования
s1 = Singleton()
s2 = Singleton()
print(s1 is s2)  # Вывод: True
```

### Плюсы и минусы каждого способа
- **Способ 1**: Простой и прямой способ. Однако, если класс наследуется от другого класса, который также реализует Singleton, этот метод может не работать.
- **Способ 2**: Гибкий и удобный способ использования декоратора. Однако, если нужно передать аргументы в класс, это усложняет реализацию.
- **Способ 3**: Универсальный способ для всех случаев. Работает с наследованием и передачей аргументов. Однако может быть менее понятен новичкам в Python.

В целом, выбор способа зависит от конкретной задачи и требований проекта.