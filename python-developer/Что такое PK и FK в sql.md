### Шанс вопроса: 3%

В SQL первичный ключ (Primary Key, PK) и внешний ключ (Foreign Key, FK) являются важными концепциями для обеспечения целостности данных.

**Первичный Ключ (PK):**
- **Определение:** Первичный ключ — это столбец или группа столбцов в таблице, которые уникально идентифицируют каждую строку. Он не может содержать NULL-значения и должен быть уникален для всех строк в таблице.
- **Пример:** Предположим, у вас есть таблица `employees` с колонками `employee_id`, `first_name`, `last_name`. Если `employee_id` является первичным ключом, то каждый работник будет уникально идентифицирован по этому ID.
  ```sql
  CREATE TABLE employees (
      employee_id INT PRIMARY KEY,
      first_name VARCHAR(255),
      last_name VARCHAR(255)
  );
  ```

**Внешний Ключ (FK):**
- **Определение:** Внешний ключ — это столбец или группа столбцов в таблице, которые ссылаются на первичный ключ другой таблицы. Цель внешнего ключа — поддерживать целостность данных между связанными таблицами.
- **Пример:** Рассмотрим таблицу `orders` и таблицу `customers`. В таблице `orders` можно иметь внешний ключ, который ссылается на первичный ключ в таблице `customers`. Это гарантирует, что каждый заказ относится к существующему клиенту.
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(255)
  );

  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
  );
  ```

**Связь между PK и FK:**
- **Один к одному:** Одна строка в таблице может ссылаться на только одну строку в другой таблице. Например, каждый клиент имеет уникальный идентификатор, и каждый заказ относится к этому клиенту.
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(255)
  );

  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
  );
  ```
- **Один ко многим:** Одна строка в таблице может ссылаться на множество строк в другой таблице. Например, один клиент может иметь несколько заказов.
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(255)
  );

  CREATE TABLE orders (
      order_id INT,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id),
      PRIMARY KEY (order_id)
  );
  ```
- **Многие ко многим:** Это более сложная связь, которая требует промежуточной таблицы для хранения связей. Например, книга может иметь несколько авторов, и каждый автор может быть в нескольких книгах.
  ```sql
  CREATE TABLE books (
      book_id INT PRIMARY KEY,
      title VARCHAR(255)
  );

  CREATE TABLE authors (
      author_id INT PRIMARY KEY,
      name VARCHAR(255)
  );

  CREATE TABLE book_authors (
      book_id INT,
      author_id INT,
      FOREIGN KEY (book_id) REFERENCES books(book_id),
      FOREIGN KEY (author_id) REFERENCES authors(author_id),
      PRIMARY KEY (book_id, author_id)
  );
  ```

Таким образом, первичный и внешний ключи являются важными инструментами для обеспечения ссылочной целостности в базах данных SQL.