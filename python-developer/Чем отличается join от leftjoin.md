### Шанс вопроса: 3%

`JOIN` в SQL используется для объединения строк из двух или более таблиц на основе соответствующих значений одного или нескольких столбцов. Различают несколько типов JOIN:

1. **INNER JOIN**: Возвращает только те строки, для которых есть соответствие в обеих таблицах. Этот тип JOIN является наиболее распространенным и выполняет пересечение множеств двух таблиц.
   ```sql
   SELECT * FROM table1 INNER JOIN table2 ON table1.id = table2.id;
   ```

2. **LEFT JOIN (или LEFT OUTER JOIN)**: Возвращает все строки из левой таблицы и соответствующие строки из правой таблицы. Если для какой-то строки из левой таблицы нет соответствия в правой, то результирующей строке будут содержать значения `NULL` для столбцов правой таблицы.
   ```sql
   SELECT * FROM table1 LEFT JOIN table2 ON table1.id = table2.id;
   ```

3. **RIGHT JOIN (или RIGHT OUTER JOIN)**: Возвращает все строки из правой таблицы и соответствующие строки из левой таблицы. Если для какой-то строки из правой таблицы нет соответствия в левой, то результирующей строке будут содержать значения `NULL` для столбцов левой таблицы.
   ```sql
   SELECT * FROM table1 RIGHT JOIN table2 ON table1.id = table2.id;
   ```

4. **FULL OUTER JOIN**: Возвращает все строки из обеих таблиц. Если для какой-то строки нет соответствия в другой таблице, то значение будет `NULL`.
   ```sql
   SELECT * FROM table1 FULL OUTER JOIN table2 ON table1.id = table2.id;
   ```

5. **CROSS JOIN**: Возвращает декартово произведение двух таблиц, т.е. каждая строка левой таблицы соединяется с каждой строкой правой таблицы.
   ```sql
   SELECT * FROM table1 CROSS JOIN table2;
   ```

**Основное отличие между LEFT JOIN и RIGHT JOIN**:
- **LEFT JOIN**: Возвращает все строки из левой таблицы, даже если нет соответствия в правой. Если нет соответствия, то поля из правой таблицы будут заполнены значениями `NULL`.
- **RIGHT JOIN**: Возвращает все строки из правой таблицы, даже если нет соответствия в левой. Если нет соответствия, то поля из левой таблицы будут заполнены значениями `NULL`.

Пример:
Предположим у нас есть две таблицы:
- **table1**: id (PK), name
- **table2**: id (PK), value

```sql
SELECT * FROM table1 LEFT JOIN table2 ON table1.id = table2.id;
-- Этот запрос вернет все строки из table1 и соответствующие строки из table2, если они есть. Если нет соответствия, то value будет NULL.
```

```sql
SELECT * FROM table1 RIGHT JOIN table2 ON table1.id = table2.id;
-- Этот запрос вернет все строки из table2 и соответствующие строки из table1, если они есть. Если нет соответствия, то name будет NULL.
```