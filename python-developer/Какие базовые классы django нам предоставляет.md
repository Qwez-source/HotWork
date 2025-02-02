### Шанс вопроса: 3%

В Django есть несколько базовых моделей, которые облегчают работу с базами данных. Основные из них включают:

1. **Model**: Класс `Model` является базовым классом для всех моделей в Django. Он предоставляет методы для взаимодействия с базой данных, такие как создание, чтение, обновление и удаление записей.

2. **Manager**: Менеджер `Manager` позволяет вам определять пользовательские методы для модели. По умолчанию каждая модель имеет менеджера с именем `objects`, который используется для запросов к базе данных.

3. **QuerySet**: QuerySet — это набор объектов, полученных из базы данных на основе определенного запроса. Он предоставляет удобный интерфейс для работы с данными.

4. **Abstract Base Classes (ABC)**: Django предоставляет абстрактные базовые классы, такие как `Model` и другие, которые можно наследовать, чтобы создать более специализированные модели. Например, `AbstractUser` для пользовательских моделей.

5. **ManyToManyField**: Поле `ManyToManyField` позволяет установить связь многие ко многим между двумя моделями.

Пример использования базовых классов в Django:

```python
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()

    def __str__(self):
        return self.name

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.ManyToManyField(Author, related_name='books')

    def __str__(self):
        return self.title
```

В этом примере:
- Класс `Author` является моделью с полями `name` и `age`.
- Класс `Book` имеет поле `author`, которое устанавливает связь многие ко многим с моделью `Author`.

Таким образом, базовые классы Django значительно упрощают создание и управление моделями в приложении.