### Шанс вопроса: 6%

В Django основными сущностями являются модели, представления, URL-маршруты и шаблоны. Вот краткое описание каждой из этих сущностей:

1. **Модели (Models)**: Это классы в Django, которые наследуются от `models.Model`. Каждая модель соответствует таблице в базе данных и представляет набор полей для хранения данных. Пример модели:
   ```python
   from django.db import models

   class Article(models.Model):
       title = models.CharField(max_length=100)
       content = models.TextField()
       published_date = models.DateField()
   ```

2. **Представления (Views)**: Это функции или классы, которые принимают веб-запросы и возвращают веб-ответы. В Django представления могут быть как функциональными, так и классами. Пример функционального представления:
   ```python
   from django.http import HttpResponse

   def article_list(request):
       articles = Article.objects.all()
       return HttpResponse(articles)
   ```

3. **URL-маршруты (URLs)**: Это правила, которые сопоставляют URL-адреса с представлениями в Django. В файле `urls.py` можно определить маршруты для приложения:
   ```python
   from django.urls import path
   from .views import article_list

   urlpatterns = [
       path('articles/', article_list),
   ]
   ```

4. **Шаблоны (Templates)**: Шаблоны используются для описания внешнего вида веб-страниц. В Django шаблоны обычно пишутся на языке разметки, таком как HTML, с использованием тегов и переменных. Пример шаблона:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <title>{{ article.title }}</title>
   </head>
   <body>
       <h1>{{ article.title }}</h1>
       <p>{{ article.content }}</p>
       <p>Published on: {{ article.published_date }}</p>
   </body>
   </html>
   ```

Эти сущности работают вместе, чтобы создать функциональный веб-сайт или API на Django.