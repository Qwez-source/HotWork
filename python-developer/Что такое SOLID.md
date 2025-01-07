### Шанс вопроса: 36%

SOLID — это пять основных принципов объектно-ориентированного программирования и дизайна, которые помогают создать более понятную, гибкую и расширяемую систему. Эти принципы были предложены Робертом Мартином (Robert C. Martin) и являются частью его книги "Принципы, принципы, паттерны". Вот краткое объяснение каждого принципа:

1. **Single Responsibility Principle (Принцип единственной ответственности)**: Класс должен иметь только одну причину для изменения, то есть он должен быть ответственен за одно понятие и выполнять только одну функцию.
   ```python
   class OrderProcessor:
       def __init__(self, order):
           self.order = order
       
       def calculate_total(self):
           return sum(item['price'] * item['quantity'] for item in self.order)

   class OrderLogger:
       def log_order(self, total, customer_id):
           print(f"Order total for customer {customer_id} is {total}")

   order = [{'name': 'Laptop', 'price': 1000, 'quantity': 2}, {'name': 'Mouse', 'price': 50, 'quantity': 3}]
   processor = OrderProcessor(order)
   total = processor.calculate_total()
   
   logger = OrderLogger()
   logger.log_order(total, '12345')
   ```

2. **Open/Closed Principle (Принцип открытости/закрытости)**: Классы должны быть открыты для расширения, но закрыты для модификации. Это означает, что новые функциональности можно добавлять, не изменяя существующий код.
   ```python
   from abc import ABC, abstractmethod

   class OrderCalculator(ABC):
       @abstractmethod
       def calculate_total(self, order):
           pass

   class SimpleOrderCalculator(OrderCalculator):
       def calculate_total(self, order):
           return sum(item['price'] * item['quantity'] for item in order)

   class DiscountOrderCalculator(OrderCalculator):
       def __init__(self, calculator: OrderCalculator):
           self.calculator = calculator
       
       def calculate_total(self, order):
           total = self.calculator.calculate_total(order)
           return total * 0.9  # Применяем скидку в 10%

   order = [{'name': 'Laptop', 'price': 1000, 'quantity': 2}, {'name': 'Mouse', 'price': 50, 'quantity': 3}]
   calculator = SimpleOrderCalculator()
   discount_calculator = DiscountOrderCalculator(calculator)
   
   total_without_discount = calculator.calculate_total(order)
   total_with_discount = discount_calculator.calculate_total(order)
   ```

3. **Liskov Substitution Principle (Принцип подстановки Барбары Лисков)**: Объекты в программе должны быть заменяемыми на экземпляры своих подтипов без изменения правильности выполнения программы.
   ```python
   class Bird:
       def fly(self):
           pass

   class Sparrow(Bird):
       def fly(self):
           print("Sparrow flying")

   class Ostrich(Bird):
       def fly(self):
           raise NotImplementedError("Ostriches can't fly")

   def make_bird_fly(bird: Bird):
       bird.fly()

   sparrow = Sparrow()
   ostrich = Ostrich()
   
   make_bird_fly(sparrow)  # Работает корректно
   make_bird_fly(ostrich)  # Ошибка, но это правильно для Ostrich
   ```

4. **Interface Segregation Principle (Принцип разделения интерфейса)**: Клиенты не должны зависеть от интерфейсов, которые они не используют. Это означает, что вместо одного большого интерфейса можно определить несколько специализированных интерфейсов для более конкретных клиентов.
   ```python
   from abc import ABC, abstractmethod

   class Vehicle(ABC):
       @abstractmethod
       def drive(self):
           pass
       
       @abstractmethod
       def fly(self):
           pass

   class Car(Vehicle):
       def drive(self):
           print("Driving a car")
       
       def fly(self):
           raise NotImplementedError("Cars can't fly")

   class Airplane(Vehicle):
       def drive(self):
           raise NotImplementedError("Airplanes don't drive")
       
       def fly(self):
           print("Flying an airplane")

   car = Car()
   airplane = Airplane()
   
   car.drive()  # Работает корректно
   airplane.fly()  # Работает корректно
   ```

5. **Dependency Inversion Principle (Принцип инверсии зависимостей)**: Модули верхнего уровня не должны зависеть от модулей нижнего уровня. Оба типа модулей должны зависеть от абстракций. Абстракции не должны зависеть от деталей, а детали должны зависеть от абстракций.
   ```python
   class Database:
       def save(self, data):
           print("Saving to database")

   class FileSaver:
       def save(self, data):
           print("Saving to file")

   class DataManager:
       def __init__(self, saver):
           self.saver = saver
       
       def store_data(self, data):
           self.saver.save(data)

   db_saver = Database()
   file_saver = FileSaver()
   
   manager_db = DataManager(db_saver)
   manager_file = DataManager(file_saver)
   
   data = {"key": "value"}
   manager_db.store_data(data)  # Использует базу данных для сохранения
   manager_file.store_data(data)  # Сохраняет в файл
   ```

Эти принципы помогают создать более чистый, расширяемый и легко тестируемый код, что является важным при разработке программного обеспечения.