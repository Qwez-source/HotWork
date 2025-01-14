### Шанс вопроса: 3%

В PostgreSQL существует несколько типов блокировок, которые помогают управлять конкурентным доступом к данным. Основные типы блокировок включают:

1. **Row-level Lock (строковая блокировка)**: Этот тип блокировки применяется, когда транзакция пытается обновить или удалить строку в таблице, к которой уже имеет доступ другая транзакция. PostgreSQL автоматически устанавливает блокировку на строку, пока первая транзакция не завершит свою работу.

2. **Access Method (метод доступа)**: В некоторых случаях, особенно при использовании специфических методов доступа, таких как GiST или SP-GiST, блокировки могут быть установлены на уровне индекса или страницы.

3. **Row Share Lock (строковая блокировка на чтение)**: Этот тип блокировки устанавливается при чтении строки, но не позволяет другим транзакциям обновить или удалить эту строку до завершения текущей транзакции.

4. **Row Exclusive Lock (строковая блокировка на запись)**: Этот тип блокировки устанавливается при попытке обновления или удаления строки и запрещает другим транзакциям как чтение, так и запись к этой строке.

5. **Share Lock (блокировка на чтение)**: Эта блокировка позволяет другим транзакциям читать данные, но запрещает обновление или удаление данных до завершения текущей транзакции.

6. **Share Update Exclusive Lock (блокировка на обновление)**: Эта блокировка позволяет другим транзакциям читать данные, но запрещает как обновление, так и удаление данных до завершения текущей транзакции.

Пример использования блокировки в PostgreSQL:

```python
import psycopg2
from psycopg2 import sql

# Установка соединения с базой данных
conn = psycopg2.connect(dbname="example_db", user="user", password="password", host="localhost")
cursor = conn.cursor()

try:
    # Начинаем транзакцию
    cursor.execute("BEGIN;")
    
    # Пытаемся обновить строку в таблице
    update_query = sql.SQL("UPDATE users SET age = %s WHERE id = %s;").format(sql.Literal(30), sql.Literal(1))
    cursor.execute(update_query)
    
    # Устанавливаем блокировку на строку, которую обновляем
    cursor.execute("SELECT * FROM users WHERE id = 1 FOR UPDATE;")
    
    # Фиксируем транзакцию
    conn.commit()
except psycopg2.Error as e:
    print(f"Ошибка: {e}")
    # Откатываем транзакцию в случае ошибки
    cursor.execute("ROLLBACK;")
finally:
    # Закрываем курсор и соединение
    cursor.close()
    conn.close()
```

В этом примере мы начинаем транзакцию, обновляем строку в таблице `users` с идентификатором 1, устанавливая блокировку на эту строку с помощью команды `FOR UPDATE`. Если транзакция завершится успешно, данные будут сохранены и блокировка снята.