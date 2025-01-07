### Шанс вопроса: 3%

Паттерн Команда (Command) является поведенческим паттером проектирования, который превращает запросы в объекты, позволяя передавать их как аргументы при вызове методов, ставить заказы, логировать их или опосредованно поддерживать отмену операций. Паттерн Команда состоит из четырёх основных компонентов:

1. **Интерфейс команды (Command)**: Определяет метод выполнения (`execute`).
2. **Конкретная команда (Concrete Command)**: Реализует метод `execute`, используя объект получателя (Receiver) для выполнения запроса.
3. **Отправитель (Invoker)**: Запрашивает выполнение команды.
4. **Получатель (Receiver)**: Определяет бизнес-логику и операции, которые должны быть выполнены в результате запроса.

Пример на Python:

```python
# Интерфейс команды
class Command:
    def execute(self):
        pass

# Конкретная команда
class ConcreteCommand(Command):
    def __init__(self, receiver):
        self._receiver = receiver

    def execute(self):
        self._receiver.action()

# Получатель
class Receiver:
    def action(self):
        print("Действие получателя")

# Отправитель
class Invoker:
    def __init__(self, command):
        self._command = command

    def execute_command(self):
        self._command.execute()

# Клиентский код
receiver = Receiver()
concrete_command = ConcreteCommand(receiver)
invoker = Invoker(concrete_command)
invoker.execute_command()  # Вывод: "Действие получателя"
```

В этом примере `ConcreteCommand` связывает объект `Receiver` с командой, а `Invoker` запрашивает выполнение команды. Таким образом, паттерн Команда позволяет отделить отправителя запроса от получателя, что удобно для тестирования и расширяемости.