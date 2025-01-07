### Шанс вопроса: 6%

SOLID — это пять основных принципов объектно-ориентированного программирования и проектирования, которые помогают создать более понятную, гибкую и расширяемую систему классов. Эти принципы были предложены Робертом Мартином (также известный как Мартинсоном) в начале 2000-х годов. Каждый из этих принципов решает определенную проблему или предотвращает ошибки, которые могут возникнуть при проектировании программных систем:

1. **Single Responsibility Principle (Принцип единственной ответственности)**: Класс должен иметь только одну причину для изменения, то есть только одну ответственность. Это означает, что класс должен быть специализирован на выполнении одной задачи или функции.

   **Пример**: 
   ```python
   class OrderProcessor:
       def __init__(self, order):
           self.order = order
       
       def calculate_total(self):
           return sum(item['price'] * item['quantity'] for item in self.order)
   
   class OrderLogger:
       def log_order(self, order):
           print(f"Order processed: {order}")
   ```

2. **Open/Closed Principle (Принцип открытости/закрытости)**: Классы должны быть открыты для расширения, но закрыты для модификации. Это означает, что новые функциональности можно добавлять, не изменяя существующий код.

   **Пример**: 
   ```python
   class Order:
       def __init__(self, items):
           self.items = items
   
   class DiscountCalculator:
       def calculate_discount(self, order):
           total = 0
           for item in order.items:
               total += item['price'] * item['quantity']
           return total * 0.9  # Пример скидки в 10%
   
   class OrderWithDiscount(Order):
       def calculate_total(self):
           discount_calculator = DiscountCalculator()
           return discount_calculator.calculate_discount(self)
   ```

3. **Liskov Substitution Principle (Принцип подстановки Барбары Лисков)**: Объекты в программе должны быть заменяемыми на экземпляры их подтипов без изменения правильности выполнения программы.

   **Пример**: 
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
   ```

4. **Interface Segregation Principle (Принцип разделения интерфейса)**: Клиенты не должны зависеть от интерфейсов, которые они не используют. Это означает, что не следует давить клиентов в приспособление для использования ненужных методов.

   **Пример**: 
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
   
   class Airplane(Vehicle):
       def fly(self):
           print("Flying an airplane")
   ```

5. **Dependency Inversion Principle (Принцип инверсии зависимостей)**: Модули верхнего уровня не должны зависеть от модулей нижнего уровня. Оба типа модулей должны зависеть от абстракций.

   **Пример**: 
   ```python
   class Database:
       def save(self, data):
           pass
   
   class MySQLDatabase(Database):
       def save(self, data):
           print(f"Saving {data} to MySQL database")
   
   class UserService:
       def __init__(self, db: Database):
           self.db = db
   
   mysql_db = MySQLDatabase()
   user_service = UserService(mysql_db)
   ```

Реализация этих принципов помогает создать систему, которая легко понимается и модифицируется, обеспечивает расширяемость и устойчивость к изменениям.