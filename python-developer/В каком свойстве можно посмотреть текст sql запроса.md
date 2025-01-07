### Шанс вопроса: 3%

В Python, когда вы работаете с базами данных и используете SQLAlchemy или другие ORM-библиотеки для взаимодействия с базой данных, обычно нет прямого доступа к тексту SQL-запроса. Однако, если вы работаете с Flask-SQLAlchemy, который является микрофреймворком на основе Flask и интегрирует SQLAlchemy для удобного использования с базой данных, можно получить доступ к тексту SQL-запроса.

В контексте Flask-SQLAlchemy, если вы включите журналирование (logging), вы сможете видеть сгенерированные запросы:

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///example.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db = SQLAlchemy(app)

# Включаем журналирование для того, чтобы видеть сгенерированные запросы
import logging
logging.basicConfig()
logging.getLogger('sqlalchemy.engine').setLevel(logging.INFO)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50))

# Пример запроса
user = User.query.filter_by(name='John Doe').first()
```

При выполнении этого кода, в консоли будет виден текст SQL-запроса:

```
INFO sqlalchemy.engine:SELECT user.id AS user_id, user.name AS user_name 
FROM user 
WHERE user.name = ? [('John Doe',)]
```

Таким образом, включив журналирование на уровне `sqlalchemy.engine` с уровнем `INFO`, вы сможете видеть текст сгенерированных SQL-запросов.