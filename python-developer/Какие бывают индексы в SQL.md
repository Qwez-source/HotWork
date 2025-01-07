### Шанс вопроса: 3%

В SQL различают несколько типов индексов, которые помогают улучшить производительность запросов. Основные типы индексов включают:

1. **Clustered Index**: Этот индекс определяет порядок физического хранения данных в таблице. В SQL Server и других СУБД, поддерживающих кластеризованные индексы, один кластеризованный индекс на таблицу позволяет эффективно выполнять запросы по диапазонам ключей.
   
   **Пример**:
   ```sql
   CREATE TABLE Employees (
       EmployeeID INT PRIMARY KEY,
       FirstName NVARCHAR(50),
       LastName NVARCHAR(50)
   );

   CREATE CLUSTERED INDEX IX_Employees_LastName ON Employees(LastName);
   ```

2. **Non-Clustered Index**: Этот индекс создает отдельную структуру данных, которая указывает на расположение строк в таблице. Non-clustered индексы позволяют быстрее получать доступ к столбцам, даже если они не являются частью кластеризованного ключа.

   **Пример**:
   ```sql
   CREATE TABLE Orders (
       OrderID INT PRIMARY KEY,
       CustomerID INT,
       OrderDate DATE
   );

   CREATE NONCLUSTERED INDEX IX_Orders_CustomerID ON Orders(CustomerID);
   ```

3. **Unique Index**: Уникальный индекс гарантирует, что все значения в столбце или комбинации столбцов уникальны. Это может помочь предотвратить дубликаты данных и улучшить целостность данных.

   **Пример**:
   ```sql
   CREATE TABLE Products (
       ProductID INT PRIMARY KEY,
       ProductName NVARCHAR(50),
       SupplierID INT
   );

   CREATE UNIQUE INDEX UX_Products_SupplierID ON Products(SupplierID);
   ```

4. **Composite Index**: Композитный индекс включает в себя несколько столбцов. Он полезен для ускорения запросов, которые требуют поиска по нескольким столбцам одновременно.

   **Пример**:
   ```sql
   CREATE TABLE Sales (
       SaleID INT PRIMARY KEY,
       ProductID INT,
       CustomerID INT,
       SaleDate DATE
   );

   CREATE INDEX IX_Sales_ProductCustomer ON Sales(ProductID, CustomerID);
   ```

5. **Spatial Index**: Пространственные индексы используются для ускорения запросов, которые требуют работы с геопространственными данными. Поддерживаются СУБД, такие как SQL Server и PostgreSQL.

   **Пример (SQL Server)**:
   ```sql
   CREATE TABLE GeospatialData (
       ID INT PRIMARY KEY,
       Location GEOGRAPHY
   );

   CREATE SPATIAL INDEX SI_GeospatialData ON GeospatialData(Location);
   ```

Эти индексы помогают оптимизировать запросы и улучшить производительность баз данных, особенно при работе с большими объемами информации.