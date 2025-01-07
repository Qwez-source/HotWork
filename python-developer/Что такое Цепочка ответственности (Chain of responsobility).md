### Шанс вопроса: 3%

Цепочка обязанностей (Chain of Responsibility) — это паттерн проектирования, который позволяет передавать запросы последовательно по цепочке обработчиков. Каждый обработчик решает, может ли он обработать запрос сам или должен передать его дальше по цепи. Это позволяет избежать жесткой привязки отправителя запроса к получателю и повышает гибкость и расширяемость кода.

Пример реализации на Python:

```python
class Handler:
    def __init__(self, successor=None):
        self._successor = successor

    def handle(self, request):
        if self._successor:
            self._successor.handle(request)

class ConcreteHandler1(Handler):
    def handle(self, request):
        if request == "Запрос 1":
            print("Обработчик 1 обрабатывает запрос")
        else:
            super().handle(request)

class ConcreteHandler2(Handler):
    def handle(self, request):
        if request == "Запрос 2":
            print("Обработчик 2 обрабатывает запрос")
        else:
            super().handle(request)

# Создаем цепочку обработчиков
handler_chain = ConcreteHandler1(ConcreteHandler2())

# Отправляем запросы по цепи
requests = ["Запрос 1", "Запрос 2", "Другой запрос"]
for req in requests:
    handler_chain.handle(req)
```

В этом примере создается базовый класс `Handler` с методом `handle`, который перенаправляет запрос дальше по цепочке, если есть следующий обработчик. Два конкретных обработчика (`ConcreteHandler1` и `ConcreteHandler2`) обрабатывают определенные типы запросов. Если запрос не может быть обработан ни одним из обработчиков, он перенаправляется следующему в цепочке.