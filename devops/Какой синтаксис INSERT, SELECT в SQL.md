### Шанс вопроса: 6%

Синтаксис операторов SQL `INSERT` и `SELECT` следующий:

**INSERT**:
```sql
INSERT INTO таблица (столбец1, столбец2, ...) VALUES (значение1, значение2, ...);
```
Пример вставки данных в таблицу:
```sql
INSERT INTO users (id, name, email) VALUES (1, 'John Doe', 'john@example.com');
```

**SELECT**:
```sql
SELECT столбец1, столбец2, ... FROM таблица WHERE условие;
```
Пример выборки данных из таблицы:
```sql
SELECT id, name FROM users WHERE age > 25;
```

Эти операторы позволяют вам добавлять данные в базу и извлекать информацию из неё.