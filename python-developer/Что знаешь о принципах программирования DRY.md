### Шанс вопроса: 6%

Конечно! Принцип DRY (Don't Repeat Yourself) гласит, что каждая часть логики должна быть определена только один раз. Это помогает избежать дублирования кода и облегчает его поддержку. В Python это можно реализовать с помощью функций, классов или модулей.

Примеры:
1. **Функции**: Если у вас есть несколько мест в коде, где выполняется одна и та же операция, лучше определить эту операцию как функцию и вызывать её откуда нужно.
    ```python
    def calculate_total(items):
        return sum([item['price'] * item['quantity'] for item in items])

    # Использование функции
    items1 = [{'name': 'Item1', 'price': 10, 'quantity': 2}, {'name': 'Item2', 'price': 5, 'quantity': 3}]
    total1 = calculate_total(items1)

    items2 = [{'name': 'ItemA', 'price': 7, 'quantity': 1}, {'name': 'ItemB', 'price': 3, 'quantity': 4}]
    total2 = calculate_total(items2)
    ```

2. **Классы**: Если у вас есть несколько объектов с похожими свойствами и методами, можно создать класс и определить все общие атрибуты и методы в нём.
    ```python
    class Item:
        def __init__(self, name, price, quantity):
            self.name = name
            self.price = price
            self.quantity = quantity

        def total_price(self):
            return self.price * self.quantity

    # Использование класса
    item1 = Item('Item1', 10, 2)
    item2 = Item('Item2', 5, 3)

    print(item1.total_price())  # Вывод: 20
    print(item2.total_price())  # Вывод: 15
    ```

3. **Модули**: Если есть повторяющиеся фрагменты кода, можно вынести их в отдельный модуль и импортировать там, где это необходимо.
    ```python
    # В файле utils.py
    def calculate_total(items):
        return sum([item['price'] * item['quantity'] for item in items])

    # В основном файле
    import utils

    items = [{'name': 'Item1', 'price': 10, 'quantity': 2}, {'name': 'Item2', 'price': 5, 'quantity': 3}]
    total = utils.calculate_total(items)
    print(total)  # Вывод: 35
    ```

Реализация принципа DRY улучшает читаемость и поддерживаемость кода, а также минимизирует вероятность внесения ошибок при его изменении.