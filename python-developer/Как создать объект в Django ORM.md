### Шанс вопроса: 3%

В Django ORM можно создать объект, вызвав метод `create()` у модели. Например, если у вас есть модель `Article`, вы можете создать новый объект следующим образом:

```python
from myapp.models import Article

# Создание нового объекта Article
new_article = Article.objects.create(title='New Article Title', content='Content of the article')
```

Этот метод сохраняет объект в базу данных и возвращает его. Если вам нужно сначала создать объект, а затем работать с ним (например, установить какие-то поля), вы можете использовать метод `create()` или же сначала создать объект без сохранения:

```python
# Создание нового объекта Article без сохранения в базу данных
new_article = Article(title='New Article Title', content='Content of the article')

# Сохранение объекта в базу данных
new_article.save()
```

Также можно использовать метод `get_or_create()` для получения объекта, если он уже существует, или создания нового:

```python
from myapp.models import Article

# Попытка получить объект по заданным параметрам
article, created = Article.objects.get_or_create(title='New Article Title', content='Content of the article')
```

Этот метод вернет кортеж `(объект, созданный?)`, где `созданный?` булево значение, указывающее, был ли объект создан при этом запросе.